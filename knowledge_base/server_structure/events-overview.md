# DayZ Vanilla Dynamic Events: events.xml Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 (Stable)  
**Purpose:** Technical documentation of events.xml architecture, dynamic spawning mechanics, and lifecycle management

---

## 1. File Overview & Scope

**Path:** `/mpmissions/dayzOffline.chernarusplus/db/events.xml`

**Role:** The "Spawner Manager" for dynamic, non-static entities in the world.

**Function:** Defines WHAT spawns (the event class), HOW MANY spawn, and the LIFECYCLE of the event.

**Limitation:** It does not define the loot on the event (that is handled by `types.xml` using `deloot="1"`), nor the precise coordinates (that is handled by `cfgeventspawns.xml`). It simply acts as the trigger mechanism.

---

## 2. Core Structure: The <event> Element

Each dynamic scenario (Vehicle spawns, Heli Crashes, Loot Drops, Animal Herds) is defined as an `<event>`.

```xml
<events>
    <event name="VehicleCivilianSedan">
        </event>
</events>
```

### Attributes of <event>

**name:** The unique identifier for the event. This must match the entry in `cfgeventspawns.xml` to link coordinates.

---

## 3. Child Elements: The Logic Engine

### A. Quantity Control (<nominal>, <min>, <max>)
<nominal>: The target number of active events on the map simultaneously.


**`<nominal>`:** The target number of active events on the map simultaneously.
- **Example:** If `<nominal>3</nominal>` is set for Helicrashes, the server attempts to keep 3 crashes active at all times.

**`<min>`:** The threshold to trigger a respawn.
- **Logic:** If the count drops to this number, the server queues a new event.

**`<max>`:** The hard cap. The server will never spawn more than this, even if requested by admin tools.


**`<lifetime>` (Seconds):** How long the event exists before despawning (if not interacted with).
- **Example:** Helicrashes usually have 2500 (approx 42 mins). Vehicles usually have 3888000 (45 days) to mimic persistence.

**`<restock>` (Seconds):** The delay between an event despawning and a new one respawning.
- **Settings:** 0 allows instant respawn. High numbers create "rare" windows.

**`<saferadius>` (Meters):** The "No-Player Zone."
- **Logic:** The event will NOT spawn if a player is within this radius of the spawn point. Prevents immersion breaking (cars popping in front of players).

**`<distanceradius>` (Meters):** The minimum distance between this event and another instance of the same event.
- **Logic:** Prevents two Helicrashes from spawning 50m apart.

### C. Cleanup & Maintenance (<cleanupradius>)

Logic: If a player is within this radius, the event will NOT despawn when its <lifetime> expires. It waits until the player leaves the area.

Usage: Critical for ensuring loot doesn't vanish while a player is looting it.

D. Flags (<flags>)
Boolean switches (0/1) for behavior.

deletable:

1: The event can be cleaned up/deleted by the system when lifetime expires.

0: The event is permanent (used for static objects or territory logic).

init_random:

1: Randomizes the spawn location on server startup.

0: Spawns in a fixed sequence or specific default.

remove_damaged:

1: If the vehicle/entity is ruined, delete it.

0: Keep ruined entities (persists wrecks).

---

## 5. Loot Injection: The deloot Connection

**Concept:** `events.xml` spawns the Container (e.g., The Wrecked Heli `Wreck_UH1Y`). It does not spawn the Loot (e.g., The LAR Rifle).

**The Handshake:**
1. `events.xml` spawns `Wreck_UH1Y`.
2. The Central Economy sees the wreck.
3. It scans `types.xml` for items flagged with `<flags deloot="1"/>` and `<usage name="HeliCrash"/>`.
4. It spawns those items strictly around the coordinates of the active event.

---

## 6. Coordinates: cfgeventspawns.xml

**Dependency:** Every `<event name="X">` in `events.xml` must have a corresponding `<event name="X">` block in `cfgeventspawns.xml`.

**Content:** List of `<pos x="..." z="..." a="..." />` (Position and Angle).

**Logic:** When `events.xml` triggers an event, it grabs a random coordinate from `cfgeventspawns.xml`.

---

## 7. Common Use Cases & Adjustments


### A. Increasing Heli Crashes

1. Find `<event name="StaticHeliCrash">`.
2. Increase `<nominal>` (e.g., from 3 to 6).
3. Decrease `<restock>` (e.g., from 2500 to 900 for faster cycling).

**Agent Warning:** Ensure `cfgeventspawns.xml` has enough valid coordinates. If you ask for 50 crashes but only 10 coordinates exist, only 10 will spawn.

### B. "Santa Sleigh" / Special Events

These are standard events that are toggled on/off by developers seasonally.

**To enable them manually:** Ensure the `<event>` block is uncommented and `<nominal>` is greater than 0.

### C. Disable Specific Events


**Vehicle "Hoarding" Fix:** Ve

**To remove Bears or Wolves:** Set `<nominal>`, `<min>`, and `<max>` all to 0. Do not delete the entry; just zero it out to prevent syntax errors.

---

## 8. Operational Odditieshicles spawned via `events.xml` (the standard way) are tracked by the nominal count. If players hide 50 cars in bases, and `<nominal>` is 50, zero new cars will spawn on the map.
- **Fix:** Some admins switch vehicle logic to `types.xml` spawning (rare/complex) or use Trader mods to bypass the event cap.

**Secondary Events:** Some events trigger other events.
## 9. Validation

**Syntax Sensitivity:** Like all DayZ XMLs, a single unclosed tag invalidates the file.

**Default Fallback:** If `events.xml`
"Static" Events: The StaticHeliCrash name is misleading. It is "Static" in the sense that the wreck doesn't move, but the event is dynamic (it despawns and moves locations).

9. Validation
Syntax Sensitivity: Like all DayZ XMLs, a single unclosed tag invalidates the file.

Default Fallback: If events.xml is broken, the server typically defaults to spawning nothing dynamic, or reverts to hardcoded engine defaults (very rare). You will see empty roads and no animals.
**To remove Bears or Wolves:** Set `<nominal>`, `<min>`, and `<max>` all to 0. Do not delete the entry; just zero it out to prevent syntax errors.

---

## 8. Operational Oddities

**Vehicle "Hoarding" Fix:** Vehicles on private servers often get hoarded in bases. Consider lowering `<lifetime>` if vehicles are hidden indefinitely.