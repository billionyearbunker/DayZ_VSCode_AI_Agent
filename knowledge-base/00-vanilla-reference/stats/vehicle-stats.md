# DayZ Vanilla Vehicle Stats

## Important Notes on Data
- Size / Weight: Marked as N/A because vehicles are World Entities (physics objects) and cannot be placed inside an inventory slot.
- Storage Capacity: The "M3S" truck capacity varies based on the rear attachment (Covered vs. Flatbed). The Boat currently has 0 persistent storage slots in vanilla.
- Class Names: These are the "root" class names. Specific color variants usually append _Color (e.g., CivilianSedan_Wine).
- Name: The human-readable label used to identify the vehicle model in the game interface.
- Class Name: The technical identifier string used by the server configuration to spawn or reference the vehicle entity.
- Size: The integer number of inventory grid slots the item occupies (typically N/A for vehicles as they are persistent world objects).
- Weight: The mass of the vehicle, utilized for physics simulations and collision interactions rather than player inventory load.
- Locations: The specific map zones or spawn points (e.g., "Industrial," "Coast") where the vehicle is configured to appear.
- Storage Capacity: The total number of inventory slots available within the vehicle's trunk or cargo hold for transporting loot.
- Accessories: A list of detachable body parts (e.g., "Hood," "Doors") that can be attached to provide protection or aesthetics.
- Required Parts: A list of mechanical components (e.g., "Spark Plug," "Battery," "Radiator") essential for the engine to run.
- Variants: A list of alternative versions of the vehicle (usually color changes) that share the same base model and statistics.
- In-game Descriptions: A text summary detailing the vehicle's handling characteristics, history, or intended terrain usage.

## Vehicles
All vehicles and their parts.

| Name            | Class Name       | Size | Weight | Locations             | Storage Capacity | Accessories                         | Required Parts                               | Variants                            | In-game Description                                                             |
|-----------------|------------------|------|--------|-----------------------|------------------|-------------------------------------|----------------------------------------------|-------------------------------------|---------------------------------------------------------------------------------|
| Ada 4x4         | OffroadHatchback | N/A  | N/A    | Towns, Tier 1-3       | 300 Slots        | Hood, Doors (2), Trunk, Spare Wheel | Spark Plug, Car Battery, Radiator, 4x Wheels | Green, Blue, White (Rust/Clean)     | A rugged, compact 4x4 Lada Niva suitable for off-road terrain.                  |
| Olga 24         | CivilianSedan    | N/A  | N/A    | Towns, Cities         | 400 Slots        | Hood, Doors (4), Trunk, Spare Wheel | Spark Plug, Car Battery, Radiator, 4x Wheels | Black, White, Wine, Silver          | A classic GAZ-24 sedan with the highest trunk capacity of all cars.             |
| Gunter 2        | Hatchback_02     | N/A  | N/A    | Towns, Industrial     | 300 Slots        | Hood, Doors (4), Trunk, Spare Wheel | Spark Plug, Car Battery, Radiator, 4x Wheels | Red, Black, Blue                    | A small VW Golf Mk2 hatchback. Fast acceleration but struggles off-road.        |
| Sarka 120       | Sedan_02         | N/A  | N/A    | Towns, Suburbs        | 300 Slots        | Hood, Doors (4), Trunk, Spare Wheel | Spark Plug, Car Battery, Radiator, 4x Wheels | Yellow, Grey, Red                   | A rear-engine Skoda sedan. Protects the engine from frontal crashes.            |
| M3S Truck       | Truck_01_Covered | N/A  | N/A    | Industrial, Military  | 600+ Slots*      | Doors (2), Hood, Dual Wheels        | Truck Battery, 4x Wheels, 4x Dual Wheels     | Blue, Orange, Green (Cargo/Flatbed) | A massive Praga V3S 6x6 transport truck. Slow, loud, but carries the most gear. |
| M1025           | Offroad_02       | N/A  | N/A    | Military (Tier 3/4)   | 300 Slots        | Doors (4), Trunk, Hood              | Glow Plug, Car Battery, Radiator, 4x Wheels  | Green, Tan (Camo)                   | An armored military Humvee. Automatic transmission and bullet-resistant glass.  |
| Inflatable Boat | Boat_01_Color    | N/A  | N/A    | Coast, Islands        | 0 Slots*         | Motor (Engine)                      | Spark Plug (for Motor), Gasoline             | Black, Blue, Camo, Orange           | A rubber dinghy for water travel. Requires a BoatMotor to operate efficiently.  |
