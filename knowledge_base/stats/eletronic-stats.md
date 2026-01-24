# DayZ Vanilla Electronic Stats

## Important Notes on Data
- Name: The user-facing display string identifying the electronic device in the game inventory.
- Class Name: The precise code identifier required by the server configuration to reference or spawn the item.
- Wgt: The numeric mass of the device (typically in grams), abbreviated from "Weight," which affects player load.
- Size: The integer value representing the inventory grid space required to store the item.
- Location: The specific map zones or building types (e.g., "Radio Tower," "Industrial") where the device is configured to spawn.
- Power Source: The specific battery type (e.g., 9V, CarBattery) or energy input required to activate the device's functionality.
- Range / Specs: Technical performance data detailing transmission radius, frequency bands, or operational duration.
- Description: A functional overview explaining the device's utility, such as communication or night vision capabilities.

## Communication & Navigation
Items used to communicate over distances or measure environments.

| Name              | Class Name           | Wgt  | Size   | Location          | Power Source | Range / Specs      | Description                                             |
|-------------------|----------------------|------|--------|-------------------|--------------|--------------------|---------------------------------------------------------|
| Handheld Radio    | PersonalRadio        | 400g | 1x2    | Police, Mil, Hunt | 9V Battery   | 5km (approx)       | Walkie-talkie. Can change frequencies.                  |
| Field Transceiver | ItemRadio            | 2kg  | Back   | Military          | Car Battery  | Global (Map-wide)  | Heavy backpack radio. Infinite range.                   |
| Megaphone         | Megaphone            | 800g | 2x2    | Fire, Ind         | 9V Battery   | ~500m Voice        | Amplifies voice range significantly.                    |
| PAS Panel         | Land_Radio_PanelPAS  | N/A  | Static | Towns             | Car Battery  | Town-wide          | Public Address System. Broadcasts to speakers on poles. |
| Rangefinder       | Rangefinder          | 300g | 2x2    | Hunt, Golf        | 9V Battery   | 1km Max            | Digital optics. Measures distance to target.            |
| GPS Receiver      | GPSReceiver          | 150g | 1x2    | Hunt, Mil         | 9V Battery   | N/A                | Displays precise X/Y Map Coordinates.                   |

## Vision & Lighting
Electronic visual aids.

| Name               | Class Name      | Wgt  | Size | Location   | Power Source  | Specs         | Description                                      |
|--------------------|-----------------|------|------|------------|---------------|---------------|--------------------------------------------------|
| NVG Goggles        | NVGoggles       | 300g | 2x2  | Heli Crash | 9V (in Strap) | Green Filter  | Night Vision. Needs Headstrap or Tac Helmet.     |
| Headtorch          | Headtorch_Color | 180g | 1x2  | Camp, Ind  | 9V Battery    | Medium Beam   | Wearable light. Hands-free.                      |
| Univ. Flashlight   | Flashlight      | 100g | 1x2  | Civ, Ind   | 9V Battery    | Focused Beam  | Standard handheld flashlight.                    |
| Weapon Light       | UniversalLight  | 80g  | 1x1  | Military   | 9V Battery    | Focused Beam  | Mounts to rails on pistols/rifles.               |
| Pistol Light       | TLRLight        | 50g  | 1x1  | Military   | 9V Battery    | Short Beam    | Smaller light for handguns.                      |
| Construction Light | Spotlight       | 10kg | 5x5  | Ind        | Power Gen     | Massive Flood | Static floodlight. Requires Generator or wiring. |

## Explosive Triggers & Timers
Electronics used to detonate IEDs or plastic explosives.

| Name             | Class Name       | Wgt  | Size | Location   | Power Source | Used For                 | Description                                    |
|------------------|------------------|------|------|------------|--------------|--------------------------|------------------------------------------------|
| Remote Detonator | RemoteDetonator  | 100g | 1x2  | Ind, Mil   | 9V Battery   | IEDs / Plastic Explosive | Remote trigger. Must be paired with explosive. |
| Alarm Clock      | AlarmClock_Color | 200g | 2x2  | Civ, House | -            | IED Timer                | Mechanical/Electric. Set time to detonate.     |
| Kitchen Timer    | KitchenTimer     | 100g | 1x1  | Kitchen    | -            | IED Timer                | Set timer to detonate.                         |

## Power Generation & Batteries
The infrastructure required to run the items above.

| Name            | Class Name     | Wgt  | Size  | Location    | Specs            | Description                                         |
|-----------------|----------------|------|-------|-------------|------------------|-----------------------------------------------------|
| 9V Battery      | Battery9V      | 50g  | 1x1   | Civ, Ind    | ~100 Quantity    | Small battery for most handheld electronics.        |
| Car Battery     | CarBattery     | 10kg | 3x3   | Ind, Garage | 12V Output       | Powers Cars, PAS, Field Radios, Lights.             |
| Truck Battery   | TruckBattery   | 15kg | 3x4   | Ind, Garage | 24V Output       | Powers V3S Trucks.                                  |
| Power Generator | PowerGenerator | 40kg | 10x10 | Ind, Shed   | Needs Spark Plug | Gas-powered generator. Powers base lights/chargers. |
| Battery Charger | BatteryCharger | 5kg  | 3x3   | Ind, Garage | Needs Generator  | Recharges Car/Truck batteries.                      |
| Cable Reel      | CableReel      | 2kg  | 2x2   | Ind, Shed   | -                | Connects Generator to Lights/Chargers.              |
| Spark Plug      | SparkPlug      | 50g  | 1x1   | Garage, Civ | -                | Required to start Cars and Generators.              |
