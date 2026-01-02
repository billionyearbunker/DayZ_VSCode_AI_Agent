# DayZ Custom Survival Gear Stats

## Important Notes on Data
- Name: The human-readable label displayed in the game inventory to identify the equipment or tool.
- Class Name: The technical identifier string used by the server to spawn the item, critical for config files.
- Wgt: The numeric mass of the item (typically in grams), abbreviated from "Weight," impacting stamina and load.
- Size: The integer number of inventory grid slots the item occupies when stored in a container.
- Location: The specific map zones or building types (e.g., "Camping," "Industrial") where the gear is found.
- Description: A text summary explaining the item's primary function, such as navigation, cooking, or resource gathering.
- Variants: A list of alternative versions of the item (usually color changes) that share functionality but differ visually.

## Light Sources & Electrical
Essential for night operations. Most require a battery (usually 9V).

| Name               | Class Name         | Wgt  | Size | Location    | Description                                          | Variants                              |
|--------------------|--------------------| -----|------|-------------|------------------------------------------------------|---------------------------------------|
| Headtorch          | Headtorch_Color    | 180g | 1x2  | Ind, Camp   | Wearable light. Best for hands-free tasks. Needs 9V. | Black, Grey                           |
| Univ. Flashlight   | Flashlight         | 100g | 1x2  | Civ, Ind    | Standard handheld flashlight. Needs 9V.              | -                                     |
| Weapon Flashlight  | UniversalLight     | 80g  | 1x2  | Military    | Mounts to rifles/pistols. Needs 9V.                  | -                                     |
| Gas Lamp           | PortableGasLamp    | 350g | 2x2  | Camp, Ind   | Very bright area light. Attaches to Gas Canister.    | -                                     |
| Chemlight          | Chemlight_Color    | 50g  | 1x1  | Civ, Mil    | Chemical stick. Low light, no battery needed.        | Blue, Green, Red, White, Yellow       |
| NVG Goggles        | NVGoggles          | 300g | 2x2  | Heli Crash  | Night Vision Goggles. Requires Headstrap + 9V.       | -                                     |
| 9V Battery         | Battery9V          | 50g  | 1x1  | Civ, Ind    | Standard power source for small electronics.         | -                                     |
| Cable Reel         | CableReel          | 2kg  | 2x2  | Ind, Shed   | Extension cord for generators/spotlights.            | -                                     |

## Fire, Cooking & Camping
Tools for warmth and preparing food safely.

| Name                  | Class Name         | Wgt  | Size | Location    | Description                                           | Variants |
|-----------------------|--------------------|------|------|-------------|-------------------------------------------------------|----------|
| Matches               | Matchbox           | 10g  | 1x1  | Civ, Hunt   | Box of matches (100 uses). Must be dry to work.       | -        |
| Lighter               | PetrolLighter      | 50g  | 1x1  | Civ, Hunt   | Refillable petrol lighter. Works in wind better.      | -        |
| Road Flare            | Roadflare          | 200g | 1x2  | Civ, Police | Bright red burning flare. Can start fires.            | -        |
| Gas Stove             | PortableGasStove   | 200g | 1x2  | Camp, Hunt  | Burner attachment for Gas Canister. Smokeless fire.   | -        |
| Gas Canister (Small)  | SmallGasCanister   | 200g | 1x2  | Camp, Hunt  | Fuel for stoves/lamps. ~1 hour burn time.             | -        |
| Gas Canister (Large)  | LargeGasCanister   | 800g | 2x2  | Camp, Hunt  | Fuel for stoves/lamps. ~4 hours burn time.            | -        |
| Cooking Pot           | Pot                | 400g | 3x4  | Civ, Camp   | Metal pot for boiling water/cooking. Holds 2000ml.    | -        |
| Frying Pan            | FryingPan          | 500g | 3x4  | Civ, Camp   | Metal pan for baking food. Cannot boil water.         | -        |
| Tripod                | Tripod             | 1kg  | 1x5  | Camp        | Stand for holding a pot over a campfire.              | -        |
| Thermometer           | Thermometer        | 50g  | 1x1  | Hospital    | Measures player temperature (Medical).                | -        |
| Hand Drill Kit        | HandDrillKit       | 100g | 1x2  | Crafted     | Stick + Bark. Starts fires without matches.           | -        |

## Fishing & Outdoor Recreation
Items specifically for gathering food via fishing.

| Name           | Class Name            | Wgt  | Size | Location    | Description                                        | Variants |
|----------------|-----------------------|------|------|-------------|----------------------------------------------------|----------|
| Fishing Rod    | FishingRod            | 400g | 1x5  | Coast, Boat | Modern rod. High durability.                       | -        |
| Improvised Rod | ImprovisedFishingRod  | 200g | 1x5  | Crafted     | Long Stick + Rope. Low durability.                 | -        |
| Fishing Hook   | Hook                  | 2g   | 1x1  | Coast, Boat | Metal hook. Requires bait (worm).                  | -        |
| Bone Hook      | BoneHook              | 5g   | 1x1  | Crafted     | Crafted from bones. Breaks easily.                 | -        |
| Earthworm      | Worm                  | 5g   | 1x1  | Digging     | Bait. Dug up from ground with Knife/Hoe.           | -        |
| Fishing Bait   | Bait                  | 5g   | 1x1  | Crafted     | Hook + Worm combined. Ready to fish.               | -        |
| Fish Trap      | FishNetTrap           | 200g | 2x3  | Coast, Boat | Net bottle trap for catching Sardines/Minnows.     | -        |

## Navigation & Communications
Tools for locating yourself and coordinating with teammates.

| Name                 | Class Name          | Wgt  | Size | Location    | Description                                      | Variants |
|----------------------|---------------------|------|------|-------------|--------------------------------------------------|----------|
| Tourist Map          | ChernarusMap        | 50g  | 1x2  | Civ, Camp   | Paper map of the entire region. Press M to view. | -        |
| Compass              | Compass             | 80g  | 1x1  | Hunt, Scout | Precision compass. Shows bearing in UI.          | -        |
| Orienteering Compass | OrienteeringCompass | 50g  | 1x1  | Camp        | Clear plastic compass. Faster alignment.         | -        |
| GPS Receiver         | GPSReceiver         | 150g | 1x2  | Hunt, Mil   | Shows X/Y coordinates on HUD. Needs 9V.          | -        |
| Binoculars           | Binoculars          | 500g | 2x2  | Civ, Camp   | Standard optics for scouting. No battery needed. | -        |
| Rangefinder          | Rangefinder         | 300g | 2x2  | Hunt, Golf  | Zoom optics + Distance readout. Needs 9V.        | -        |
| Handheld Radio       | PersonalRadio       | 400g | 1x2  | Police, Mil | Short range comms (approx 3-5km). Needs 9V.      | -        |
| Megaphone            | Megaphone           | 800g | 2x2  | Fire, Ind   | Amplifies voice locally. Needs 9V.               | -        |

## Storage Containers & Cases
Protective items that hold other items, often keeping them dry or organized.

| Name            | Class Name          | Wgt  | Size | Location    | Description                                    | Variants                                |
|-----------------|---------------------|------|------|-------------|------------------------------------------------|-----------------------------------------|
| Protective Case | SmallProtectorCase  | 500g | 3x4  | Ind, Fire   | Hard plastic case (12 slots). Very durable.    | -                                       |
| Ammo Box        | AmmoBox             | 500g | 2x3  | Military    | Metal tin (20 slots). Only accepts ammo.       | -                                       |
| Dry Sack        | WaterproofBag_Color | 200g | 3x4  | Coast, Camp | Waterproof bag (20 slots). Keeps items dry.    | Orange, Yellow, Green                   |
| Dry Bag (Small) | DryBag_Color        | 600g | 3x4  | Coast, Camp | Backpack that doubles as container (20 slots). | Yellow, Green, Blue, Red, Black, Orange |
| First Aid Pouch | FirstAidKit         | 150g | 3x3  | Hospital    | Red pouch (9 slots). Stores meds/bandages.     | -                                       |
| Teddy Bear      | Bear_Color          | 200g | 2x3  | Civ, House  | Stuffed toy (6 slots). Can hide items inside.  | Beige, Dark, Pink, White                |
| Cooking Pot     | Pot                 | 400g | 3x4  | Civ, Camp   | Holds 12 slots + Water. Items get wet inside.  | -                                       |

## DayZ Tents & Shelters
A place to lay your head and stash some gear.

| Name                         | Class Name            | Wgt  | Size            | Storage   | Repair Material        | Camo Slots | Location            | Description                                                                                   | Variants      |
|------------------------------|-----------------------|------|-----------------|-----------|------------------------|------------|---------------------|-----------------------------------------------------------------------------------------------|---------------|
| Medium Tent                  | MediumTent            | 15kg | 3x10 (Back)     | 63 Slots  | Sewing Kit / Duct Tape | Yes (1)    | Camping, Civilian   | Standard blue dome tent. Good for solo players. Hard to hide due to bright color.             | Orange, Green |
| Large Tent                   | LargeTent             | 35kg | 2x10 (Back)     | 150 Slots | Sewing Kit / Duct Tape | Yes (1)    | Military Areas      | Large military-grade tent. Fits a squad. Waterproof and durable.                              | -             |
| Car Tent                     | CarTent               | 50kg | 2x10 (Back)     | 150 Slots | Sewing Kit / Duct Tape | Yes (1)    | Industrial, Garages | Massive box-shaped tent. Can fit a sedan inside to hide/protect it.                           | -             |
| Improvised Shelter (Stick)   | ShelterSite + Stick   | N/A  | N/A             | 100 Slots | N/A                    | No         | Crafted             | Requires ShelterKit + 50 Short Sticks. Very hard to see in forests.                           | -             |
| Improvised Shelter (Leather) | ShelterSite + Leather | N/A  | N/A             | 100 Slots | Leather Kit            | No         | Crafted             | Requires ShelterKit + 8 Tanned Leathers. High durability and waterproof.                      | -             |
| Improvised Shelter (Tarp)    | ShelterSite + Fabric  | N/A  | N/A             | 100 Slots | Sewing Kit             | No         | Crafted             | Requires ShelterKit + 4 Tarps. Blue color makes it visible, but easier to build than leather. | -             |
| Canopy Tent                  | PartyTent             | 35kg | 2x10 (Back)     | 0 Slots   | Sewing Kit             | Yes (1)    | Civilian, Carnival  | Large open-sided shelter. No storage, purely for rain protection/shade.                       | -             |
| Sea Chest                    | SeaChest              | 20kg | Shoulder (10x5) | 100 Slots | Plank                  | No         | Ind, Coast, Hunting | Not a tent, but often used as buried stash. Heavy wooden trunk.                               | -             |
| Barrel                       | Barrel_Color          | 10kg | Shoulder        | 150 Slots | Epoxy Putty            | No         | Ind, Sheds          | Steel drum. Can be used for storage, tanning leather, or dying clothes.                       | Various       |

