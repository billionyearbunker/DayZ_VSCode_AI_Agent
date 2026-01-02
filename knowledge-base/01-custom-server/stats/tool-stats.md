# DayZ Custom Tool Stats

## Important Notes on Data
- Note that "Item Health Used" varies by action (e.g., chopping a tree damages an axe more than hitting a zombie), so I have provided the standard value for the tool's primary purpose.
- Name: The human-readable display string used to identify the tool in the inventory interface.
- Class Name: The technical identifier string used in server configuration files to spawn or reference the object.
- Weight: The mass of the tool (typically in grams), which contributes to the player's total load and stamina drain.
- Size: The integer number of inventory grid slots the tool occupies when stored.
- Location: The specific map zones or building types (e.g., "Industrial," "Farm," "Sheds") where the tool spawns.
- Damage (HP/Shock): A dual-value metric indicating the Health damage and Shock (unconscious) damage inflicted when using the tool as a melee weapon.
- Health Used: The amount of durability (hitpoints) the tool loses per specific action (e.g., chopping a tree, opening a can).
- Used For: A list of the primary actions or interactions the tool enables, such as base building, dismantling, or gardening.
- Stack: The maximum quantity of the item that can be combined into a single inventory slot (often 1 for large tools).
- Description: A text summary explaining the tool's versatility and effectiveness for specific survival tasks.

## Heavy Tools (Chopping, Digging, Breaking)
These tools are large (often taking shoulder slots) and are used for resource gathering or base destruction.

| Name            | Class Name      | Weight | Size | Location    | Damage (HP/Shock) | Health Used  | Used For                          | Stack | Description                              |
|-----------------|-----------------|--------|------|-------------|-------------------|--------------|-----------------------------------|-------|------------------------------------------|
| Firefighter Axe | FirefighterAxe  | 2.5kg  | 2x5  | Fire Stn    | 55 / 40           | 2.5 (Tree)   | Chopping Wood, Raiding            | 1     | Heavy two-handed axe painted red/yellow. |
| Splitting Axe   | WoodAxe         | 2.0kg  | 2x5  | Farm, Ind   | 45 / 30           | 2.5 (Tree)   | Chopping Wood                     | 1     | Standard axe for splitting firewood.     |
| Pickaxe         | Pickaxe         | 2.5kg  | 2x5  | Farm, Ind   | 30 / 30           | 3.0 (Rock)   | Mining Stone, Digging, Raiding    | 1     | Heavy tool for breaking rock or soil.    |
| Sledgehammer    | SledgeHammer    | 6.0kg  | 2x5  | Ind, Constr | 45 / 75           | 4.0 (Rock)   | Mining Stone, Raiding Walls       | 1     | Massive hammer capable of breaking walls |
| Shovel          | Shovel          | 3.0kg  | 2x5  | Farm, Ind   | 25 / 45           | 4.0 (Dig)    | Digging Garden/Logs, Burying      | 1     | Standard shovel for earthworks.          |
| Farming Hoe     | Hoe             | 1.5kg  | 2x5  | Farm        | 20 / 30           | 3.0 (Dig)    | Tilling Ground                    | 1     | Tool for preparing garden plots.         |
| Pitchfork       | Pitchfork       | 1.5kg  | 1x5  | Farm        | 15 / 15           | 2.0 (Hit)    | Combat (Reach)                    | 1     | Agricultural tool with sharp tines.      |
| Crowbar         | Crowbar         | 1.0kg  | 1x4  | Ind, Garage | 15 / 20           | 2.0 (Hit)    | Locking/Unlocking Doors, Skinning | 1     | L-shaped metal bar used for prying.      |

## Light Tools (Cutting, Repair, Crafting)
Essential belt-slot or pocket items required for crafting kits and managing inventory.

| Name        | Class Name  | Weight | Size | Location   | Damage (HP/Shock) | Health Used  | Used For                         | Stack | Description                                  |
|-------------|-------------|--------|------|------------|-------------------|--------------|----------------------------------|-------|----------------------------------------------|
| Hatchet     | Hatchet     | 1.1kg  | 2x3  | Farm, Camp | 30 / 20           | 2.0 (Tree)   | Wood, Hammering, Raid            | 1     | Multi-purpose tool. Acts as Axe AND Hammer.  |
| Hammer      | Hammer      | 800g   | 2x2  | Ind, Garage| 18 / 25           | 2.0 (Build)  | Building Base Parts              | 1     | Essential for nailing planks to frames.      |
| Hacksaw     | Hacksaw     | 600g   | 2x3  | Ind, Garage| 10 / 5            | 5.0 (Cut)    | Cutting Metal/Code Locks         | 1     | Saw for cutting metals and hard plastics.    |
| Hand Saw    | HandSaw     | 400g   | 2x3  | Ind, Farm  | 12 / 5            | 4.0 (Wood)   | Crafting Planks                  | 1     | Saw for cutting timber into planks.          |
| Pliers      | Pliers      | 300g   | 1x2  | Ind, Garage| 5 / 5             | 2.0 (Build)  | Building Gates, Barbed Wire      | 1     | Used to manipulate wire and metal sheets.    |
| Screwdriver | Screwdriver | 180g   | 1x2  | Ind, Civ   | 8 / 5             | 3.0 (Lock)   | Electrical, Opening Cans         | 1     | Tool for screws. Can open cans poorly.       |
| Wrench      | Wrench      | 400g   | 1x2  | Ind, Garage| 10 / 15           | -            | Locking Car Parts                | 1     | Used to secure car batteries/panels.         |
| Pipe Wrench | PipeWrench  | 1.5kg  | 1x4  | Ind        | 25 / 35           | -            | Moving Car Engines               | 1     | Heavy wrench for plumbing or mechanics.      |
| Can Opener  | CanOpener   | 100g   | 1x1  | Kitchen    | 2 / 0             | 0.0 (Open)   | Opening Cans (0% Loss)           | 1     | The only way to open food without spilling.  |

## Knives (Skinning & Stealth)
Used for skinning animals, crafting rags, and stealth kills.

| Name          | Class Name   | Weight | Size | Location   | Damage (HP/Shock) | Health Used  | Used For                   | Stack | Description                             |
|---------------|--------------|--------|------|------------|-------------------|--------------|----------------------------|-------|-----------------------------------------|
| Hunting Knife | HuntingKnife | 180g   | 1x2  | Hunt, Camp | 25 / 15           | 2.0 (Skin)   | Skinning, Crafting, Combat | 1     | Best durability knife.                  |
| Combat Knife  | CombatKnife  | 150g   | 1x2  | Military   | 27 / 15           | 2.5 (Skin)   | Skinning, Combat           | 1     | Military grade bayonet/knife.           |
| Kitchen Knife | KitchenKnife | 150g   | 1x2  | Kitchen    | 15 / 5            | 4.0 (Skin)   | Skinning, Cooking          | 1     | Common household knife. Low durability. |
| Steak Knife   | SteakKnife   | 80g    | 1x2  | Kitchen    | 12 / 5            | 5.0 (Skin)   | Skinning                   | 1     | Flimsy knife. Breaks very fast.         |
| Stone Knife   | StoneKnife   | 150g   | 1x1  | Crafted    | 10 / 5            | 6.0 (Skin)   | Skinning, Rags             | 1     | Crafted from two small stones.          |
| Bone Knife    | BoneKnife    | 100g   | 1x2  | Crafted    | 12 / 5            | 5.0 (Skin)   | Skinning, Rags             | 1     | Crafted from bones. Sharp but brittle.  |
| Machete       | Machete      | 600g   | 1x4  | Farm       | 35 / 15           | 3.0 (Bush)   | Clearing Bushes, Combat    | 1     | Long blade for clearing vegetation.     |
| Kukri         | KukriKnife   | 500g   | 1x3  | Military   | 30 / 15           | 3.0 (Bush)   | Clearing Bushes, Combat    | 1     | Heavy curved blade. Very durable.       |

## Maintenance & Repair Kits
Items used to restore durability to other items.

| Name             | Class Name          | Weight | Size | Location    | Damage | Health Used | Used For                 | Stack | Description                               |
|------------------|---------------------|--------|------|-------------|--------|-------------|--------------------------|-------|-------------------------------------------|
| Sharpening Stone | Whetstone           | 200g   | 1x1  | Outhouse    | N/A    | 15%         | Repair Knives/Axes       | 1     | Stone for sharpening edges.               |
| Sewing Kit       | SewingKit           | 100g   | 1x1  | Residential | N/A    | 10%         | Repair Fabric Clothes    | 1     | Needle and thread for fabrics.            |
| Leather Kit      | LeatherSewingKit    | 200g   | 1x1  | Farm, Hunt  | N/A    | 10%         | Repair Vests/Boots/Bags  | 1     | Heavy needle for leather repair.          |
| Epoxy Putty      | EpoxyPutty          | 200g   | 1x1  | Ind         | N/A    | 10%         | Repair Helmets/Plastics  | 1     | Industrial adhesive putty.                |
| Weapon Clean Kit | WeaponCleaningKit   | 250g   | 2x2  | Military    | N/A    | 10%         | Repair Guns              | 1     | Brushes and oil for firearms.             |
| Electronic Kit   | ElectronicRepairKit | 500g   | 1x2  | Ind         | N/A    | 10%         | Repair Radios/NVG        | 1     | Soldering iron and multimeter.            |
| Duct Tape        | DuctTape            | 200g   | 1x2  | Ind, Shed   | N/A    | 10%         | Repair "Almost Anything" | 1     | Universal repair (usually lower quality). |

## Building Materials & Hardware
The raw resources required to construct bases.

| Name             | Class Name       | Weight | Size     | Location   | Damage   | Health Used | Used For                | Stack | Description                          |
|------------------|------------------|--------|----------|------------|----------|-------------|-------------------------|-------|--------------------------------------|
| Wooden Log       | WoodenLog        | 20kg   | Shoulder | Trees      | 15 / 20  | -           | Base Frame, Pillars     | 1     | Heavy log chopped from large trees.  |
| Wooden Plank     | WoodenPlank      | 300g   | 2x8      | Crafted    | 5 / 5    | -           | Walls, Crates           | 10    | Cut from logs using a saw.           |
| Nails            | Nail             | 10g    | 1x1      | Ind, Shed  | N/A      | -           | Fastening Planks/Sheet  | 99    | Essential for all base building.     |
| Sheet Metal      | MetalPlate       | 3kg    | 10x10    | Ind        | N/A      | -           | Metal Walls (Tier 2)    | 10    | Heavy plating for stronger walls.    |
| Barbed Wire      | BarbedWire       | 1kg    | 2x2      | Ind, Shed  | 10 / 0   | -           | Wall Defense            | 1     | Causes cuts if touched.              |
| Metal Wire       | MetalWire        | 300g   | 1x2      | Ind, Shed  | N/A      | -           | Gates, Tripwires        | 1     | Flexible wire for mechanisms.        |
| Combination Lock | CombinationLock  | 400g   | 1x2      | Ind, Shed  | N/A      | -           | Locking Gates (3-Dial)  | 1     | 3-digit rotary lock (1,000 combos).  |
| Code Lock        | CombinationLock4 | 400g   | 1x2      | Ind (Rare) | N/A      | -           | Locking Gates (4-Dial)  | 1     | 4-digit rotary lock (10,000 combos). |
| Camo Net         | CamoNet          | 1kg    | 1x5      | Military   | N/A      | -           | Hiding Bases/Tents      | 1     | Reduces visibility of base parts.    |
| Burlap Strips    | BurlapStrip      | 100g   | 1x2      | Crafted    | N/A      | -           | Ghillie Suits, Wraps    | 1     | Cut from Burlap Sacks.               |

## Kits & Storage (Placeables)
Often overlooked but vital for survival.

| Name           | Class Name    | Weight | Size     | Location   | Health | Used For                | Stack | Description                            |
|----------------|---------------|--------|----------|------------|--------|-------------------------|-------|----------------------------------------|
| Fence Kit      | FenceKit      | 600g   | 1x5      | Crafted    | N/A    | Layout for Walls        | 1     | Rope + 2 Sticks. Define wall pos.      |
| Watchtower Kit | WatchtowerKit | 600g   | 1x5      | Crafted    | N/A    | Layout for Towers       | 1     | Rope + 4 Sticks. Define tower pos.     |
| Garden Plot    | GardenPlot    | N/A    | N/A      | Digged     | N/A    | Growing Food            | -     | Created using Shovel/Pickaxe/Hoe.      |
| Medium Tent    | MediumTent    | 15kg   | Bag Slot | Civ, Camp  | High   | Storage/Shelter         | 1     | Standard blue camping tent.            |
| Large Tent     | LargeTent     | 35kg   | Bag Slot | Military   | High   | Storage/Shelter         | 1     | Large green military tent.             |
| Car Tent       | CarTent       | 50kg   | Bag Slot | Ind        | High   | Storage/Vehicle Hiding  | 1     | Massive tent capable of fitting a car. |
| Barrel         | Barrel_Color  | 10kg   | Shoulder | Ind        | High   | Storage (150 Slots)     | 1     | Steel drum. Can be used for tanning.   |
| Sea Chest      | SeaChest      | 20kg   | Shoulder | Ind, Coast | High   | Storage (100 Slots)     | 1     | Heavy wooden chest.                    |
| Wooden Crate   | WoodenCrate   | 5kg    | 5x5      | Crafted    | Med    | Storage (50 Slots)      | 1     | Planks + Nails. Buried for stash.      |
