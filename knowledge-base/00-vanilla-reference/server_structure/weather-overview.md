# DayZ Vanilla Environment Configuration: Time & Weather Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 (Stable)  
**Purpose:** Technical documentation of time flow mechanics, weather systems, and environmental configuration

---

## 1. The Chronological System (Time Flow)

Time in DayZ is controlled by a handshake between the server configuration file (`serverDZ.cfg`) and the mission initialization script (`init.c`).

### A. Server Config Controls (serverDZ.cfg)

These parameters dictate the speed and persistence of time relative to the real world.

**serverTime:** Defines the starting time of the server upon boot.
- `"SystemTime"`: Matches the host machine's local clock (Real Time).
- `"2015/4/8/09/00"`: Forces a specific static start time (Year/Month/Day/Hour/Minute) on every restart.

**serverTimeAcceleration (Integer, 0-24):**
- Multiplier for daylight hours.
- Value 12: 1 Real Hour = 12 Game Hours (Full 24h cycle in 2 hours).

**serverNightTimeAcceleration (Float, 0.1-64):**
- Multiplier specific to night hours.
- **Formula:** The engine detects when the sun is below the horizon and applies this on top of the base acceleration.
- **Goal:** Allows for long days but short nights (e.g., fast-forwarding darkness).

**serverTimePersistent (0 or 1):**
- `1`: The server saves the time on shutdown. If it shuts down at 18:00, it starts at 18:00.
- `0`: The server resets to the `serverTime` value on every restart.

### B. Mission Script Controls (init.c)
The init.c file defines the Calendar Date, which dictates the season (Sun angle, Temperature, Day Length).

Method: GetGame().GetWorld().SetDate( Year, Month, Day, Hour, Minute );

Seasonal Logic:

Winter: Set Month to 12 or 1. Sun is low, nights are long, ambient temperature is lower (players freeze faster).

The `init.c` file defines the Calendar Date, which dictates the season (Sun angle, Temperature, Day Length).

**Method:** `GetGame().GetWorld().SetDate( Year, Month, Day, Hour, Minute );`

**Seasonal Logic:**
- **Winter:** Set Month to 12 or 1. Sun is low, nights are long, ambient temperature is lower (players freeze faster).
- **Summer:** Set Month to 6 or 7. Sun is high, days are long, players overheat in heavy gear.

**Conflict:** If `serverTimePersistent` is active in `serverDZ.cfg`, the `SetDate` hour/minute in `init.c` is ignored, but the Year/Month/Day is usually respected.

---

## 2. The Atmospheric System (cfgweather.xml)

**Path:** `/mpmissions/dayzOffline.chernarusplus/cfgweather.xml`

**Role:** Defines the probability, duration, and volatility of weather phenomena.

**Structure:** Hierarchical XML defining distinct weather patterns (overcast, fog, rain, wind, thunderstorm).

### A. The "Master" Variable: Overcast (Clouds)

Rain and Thunder cannot exist without Overcast. It is the driver of the weather system.

**Thresholds:**
- `0.0 - 0.3`: Clear Sky / Sunny.
- `0.4 - 0.6`: Partly Cloudy.
- `0.7 - 1.0`: Dark Clouds (Rain capable).

### B. XML Element Structure (Universal for all types)

Each weather type (e.g., `<overcast>`) uses the same child elements:

```xml
<overcast>
    <min>0.0</min>
    <max>1.0</max>
    <frequency>10</frequency>
    <timelimits>
        <min>900</min>
        <max>1800</max>
    </timelimits>
    <change>
        <min>0.1</min>
        <max>0.3</max>
    </change>
</overcast>
```

### C. Logic & Behavior

**Change Step:** When the timelimit expires, the engine picks a random change value (between `change.min` and `change.max`).

**Direction:** It randomly adds or subtracts this value from the current state.

**Clamping:** If the result hits the `<min>` or `<max>` bounds, it stops there.

**Implication:** To force a "Sunny Server," you must set `<overcast><max>` to `0.0`. If you leave `max` at `1.0` but increase timelimits, it will still eventually rain, just less often.

### D. The Rain Dependency

**Trigger:** Rain does not have its own "independent" will. It is tied to Overcast.

**Threshold:** Typically, Rain begins when Overcast > 0.7.

**Configuration:** The `<rain>` section in XML controls the intensity of the rain (Drizzle vs Storm), but the existence of rain is gated by Cloud coverage.

### E. Wind & Fog

**Wind:** Affects bullet ballistics and tree movement. High wind increases player convective cooling (freezing).

**Fog:** Render distance limiter.

**Oddity:** Fog is calculated at different altitudes. You can have fog in valleys (low altitude) but clear peaks.

---

## 3. Mission Script Overrides (init.c)

The `init.c` file often contains code that overrides or initializes the XML settings on server start.

```cpp
Weather weather = g_Game.GetWeather();

// Disables the mission-based scripted weather events to allow the XML dynamic system to run
weather.MissionWeather(false);

// Hard limits set here often OVERRIDE the XML min/max
weather.GetOvercast().SetLimits( 0.0 , 1.0 );
weather.GetRain().SetLimits( 0.0 , 1.0 );
weather.GetFog().SetLimits( 0.0 , 0.25 );

// Forecast Change Limits (Volatility)
weather.GetOvercast().SetForecastChangeLimits( 0.0, 0.2 );
weather.GetRain().SetForecastChangeLimits( 0.0, 0.1 );
```

**Agent Note:** If editing `cfgweather.xml` seems to have no effect, check `init.c`. The script executes after the XML load, potentially overwriting limits.

---

## 4. Temperature & Wetness Mechanics

The environment directly impacts the `PlayerBase` through thermodynamics.

**Wetness:**
- Controlled by Rain Intensity.
- Items in inventory can get wet. Wet clothing loses thermal insulation values.
- **Oddity:** Placing items inside a "Drybag" or protective case prevents wetness.

**Ambient Temperature:**
- **Base:** Derived from the Date (Month) and Time of Day.
- **Modifiers:**
  * **Altitude:** approx -0.65°C per 100m elevation. (Tisy is much colder than Chernogorsk).
  * **Overcast:** Clear nights are colder than cloudy nights (Radiative cooling).
  * **Wind:** Wind Chill factor drastically reduces "Feels Like" temp.
  * **Wetness:** Being wet multiplies heat loss.

---

## 5. Operational Oddities

**"Weather Blink":** Upon server restart, the weather often resets to a default state before loading the persistence or `init.c` values. Players may see a flash of different lighting.

**Sync Issues:** Weather is synchronized from Server to Client. Occasionally, desync occurs where it is raining for one player but sunny for another. This is usually a network packet loss issue, not a config error.

**Forecast Interpolation:** The engine does not snap from 0% rain to 100% rain. It interpolates over time. If you force a weather change via Admin Tools, the sky transitions smoothly, usually taking 1-2 minutes to fully visually update.


**File:** `cfgGameplay.json` (Newer builds) or `serverDZ.cfg`.
---

## 6. Personal Light (Darkness Settings)

**Parameter:** `disablePersonalLight` / `lightingConfig`.

**Concept:** DayZ has a subtle "aura" of light around players at night to aid navigation.

**Hardcore:** Setting `disablePersonalLight = 1` forces "Pitch Black" nights where flashlights/NVGs are mandatory.
Concept: DayZ has a subtle "aura" of light around players at night to aid navigation.

Hardcore: Setting disablePersonalLight = 1 forces "Pitch Black" nights where flashlights/NVGs are mandatory.
