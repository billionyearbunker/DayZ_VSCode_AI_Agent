# DayZ Custom Craftable Stats

## Important Notes on Data
- Name: The human-readable label used to identify the crafted object in the game interface.
- Class Name: The technical identifier string used by the game engine to spawn the resulting object after crafting is complete.
- Size: The integer number of inventory slots the final crafted item occupies if placed inside a container.
- Weight: The mass of the finished object, usually in grams, which impacts the player's stamina calculation.
- Items Needed to Craft: A list of the specific input ingredients (tools and consumables) required to execute the crafting recipe.
- Description: A text summary explaining the utility, function, or lore of the crafted item to the player.

## Survival & Utilities
Essential items created from basic resources found in nature.

| Name            | Class Name    | Size | Weight | Items Needed to Craft                               | Description                                                            |
|-----------------|---------------|------|--------|-----------------------------------------------------|------------------------------------------------------------------------|
| Hand Drill Kit  | HandDrillKit  | 1x2  | 100g   | 1x Short Stick + 1x Tree Bark                       | Primitive fire starter. Replaces matches. High failure chance in wind. |
| Campfire        | Fireplace     | 3x3  | 1kg    | 1x Short Stick + 1x Kindling (Paper/Rag/Bark)       | Basic fire setup. Add fuel (Logs/Sticks) to burn.                      |
| Torch           | Torch         | 1x5  | 500g   | 1x Short Stick + 1x Rag (add Lard/Fuel to extend)   | Portable light source. Can also provide warmth.                        |
| Stone Knife     | StoneKnife    | 1x1  | 150g   | 2x Small Stone (Interact with each other)           | Primitive knife. Low durability but essential early game.              |
| Bone Knife      | BoneKnife     | 1x2  | 100g   | 1x Bone + 1x Stone/Wall (Interact with environment) | Sharp improvised knife. Better than stone but brittle.                 |
| Improvised Rope | Rope          | 1x3  | 200g   | 6x Rags (Combined in two stacks of 6)               | Used for crafting backpacks, shelters, and restraints.                 |
| Burlap Strips   | BurlapStrip   | 1x2  | 100g   | 1x Burlap Sack + 1x Knife                           | Used for ghillie suits and weapon wraps.                               |
| Fishing Bait    | Bait          | 1x1  | 5g     | 1x Earthworm + 1x Hook                              | Required to catch fish with a rod.                                     |
| Bone Hook       | BoneHook      | 1x1  | 5g     | 1x Bone + 1x Knife                                  | Improvised fishing hook.                                               |

## Improvised Gear & Clothing
Wearable items made from collected materials.

| Name                   | Class Name           | Size | Weight | Items Needed to Craft            | Description                                                  |
|------------------------|----------------------|------|--------|----------------------------------|--------------------------------------------------------------|  
| Improvised Courier Bag | CourierBag           | 3x4  | 400g   | 1x Burlap Sack + 1x Rope         | Small improvised backpack (30 Slots).                        |
| Improvised Backpack    | ImprovisedBag        | 4x5  | 600g   | 1x Courier Bag + 3x Short Sticks | Larger improvised backpack (42 Slots). Low profile.          |
| Leather Backpack       | LeatherSack_Natural  | 5x5  | 1.2kg  | 1x Boar Pelt (Tanned) + 1x Rope  | Durable leather bag (63 Slots). Waterproof.                  |
| Ghillie Suit           | GhillieSuit_Color    | 6x6  | 2kg    | 10x Burlap Strips + 4x Netting   | Full body camouflage. Takes Backpack slot. Overheats player. |
| Ghillie Hood           | GhillieHood_Color    | 2x2  | 500g   | 2x Burlap Strips + 1x Netting    | Head camouflage.                                             |
| Ghillie Gun Wrap       | GhillieAtt_Color     | 1x2  | 200g   | 2x Burlap Strips + 1x Netting    | Camouflage for rifles.                                       |
| Face Mask              | Rag (Wearable)       | 1x1  | 50g    | 1x Rag (Equip to Face slot)      | Very basic insulation/dust protection.                       |
| Armband                | Armband_Color        | 1x1  | 20g    | 1x Rag (Cut into armband)        | Identification marker for teams.                             |
| Feet Wraps             | FeetCover_Improvised | 2x2  | 100g   | 2x Rags                          | Temporary footwear. Very low durability. Quiet footsteps.    |

## Improvised Weapons & Traps
Primitive combat tools.

| Name                  | Class Name            | Size | Weight | Items Needed to Craft                     | Description                                                            |
|-----------------------|-----------------------|------|--------|-------------------------------------------|------------------------------------------------------------------------|  
| Improvised Spear      | Spear                 | 1x10 | 1kg    | 1x Long Stick + 1x Bone Knife/Stone Knife | Reach weapon. Good for killing zombies safely.                         |
| Improvised Bow        | ImprovisedBow         | 1x8  | 500g   | 1x Long Stick + 1x Rope                   | Primitive bow. Silent. (Note: Removed in some versions, check server). |
| Improvised Arrow      | Ammo_ImprovisedArrow  | 1x2  | 50g    | 1x Short Stick + 1x Feather               | Basic ammunition for bows.                                             |
| Improvised Suppressor | ImprovisedSuppressor  | 1x2  | 200g   | 1x PET Bottle + 1x Duct Tape              | Silences shots for a few rounds. Ruined quickly.                       |
| Sawed-off Mosin       | Mosin9130_Sawedoff    | 4x2  | 2kg    | 1x Mosin 91/30 + 1x Hacksaw               | Compact sniper. Lower range/accuracy. Fits in bags.                    |
| Sawed-off BK-43       | Izh43Shotgun_Sawedoff | 4x2  | 1.5kg  | 1x BK-43 Shotgun + 1x Hacksaw             | Compact double barrel. devastating close range.                        |
| Tripwire Trap         | TripwireTrap          | 2x2  | 200g   | 1x Metal Wire + 2x Short Sticks           | Trigger mechanism. Add grenade/flare to arm.                           |
| Fish Trap (Bottle)    | FishNetTrap           | 2x3  | 100g   | 1x PET Bottle + 1x Knife (Cut bottle)     | Catch small fish in shallow water.                                     |
| Snare Trap            | RabbitSnareTrap       | 2x2  | 200g   | 1x Metal Wire + 1x Short Stick            | Catches rabbits/chickens.                                              |

## Medical & Chemistry
Health and processing items.

| Name             | Class Name    | Size | Weight | Items Needed to Craft                             | Description                                        |
|------------------|---------------|------|--------|---------------------------------------------------|----------------------------------------------------|  
| Splint           | Splint        | 1x3  | 500g   | 2x Short Sticks + 4x Rags (or 1x Bandage)         | Fixes broken legs allowing walking.                |
| Blood Bag Kit    | BloodBagIV    | 1x2  | 200g   | 1x Blood Bag (Full) + 1x IV Start Kit             | Prepared blood bag ready for transfusion.          |
| Saline Bag Kit   | SalineBagIV   | 1x2  | 200g   | 1x Saline Bag + 1x IV Start Kit                   | Prepared saline for hydration/blood regen.         |
| Tanned Leather   | TannedLeather | 2x2  | 500g   | 1x Garden Lime + 1x Animal Pelt (In Barrel/crate) | Processed leather used for crafting shelters/bags. |
| Disinfected Rags | Rag (Clean)   | 1x1  | 50g    | Rags + Alcohol/Disinfectant/Iodine                | Safe for bandaging wounds without infection risk.  |

## Base Building (Kits & Parts)
The foundation of all structures.

| Name           | Class Name    | Size | Weight | Items Needed to Craft               | Description                                     |
|----------------|---------------|------|--------|-------------------------------------|-------------------------------------------------|  
| Fence Kit      | FenceKit      | 1x5  | 600g   | 1x Rope + 2x Short Sticks           | Used to place the foundation for a fence/gate.  |
| Watchtower Kit | WatchtowerKit | 1x5  | 600g   | 1x Rope + 4x Short Sticks           | Used to place the foundation for a watchtower.  |
| Flag Pole Kit  | FlagKit       | 1x5  | 10kg   | 1x Rope + 3x Short Sticks           | Foundation for flag pole (prevents despawning). |
| Shelter Kit    | ShelterKit    | 1x2  | 500g   | 1x Rope + 4x Short Sticks           | Foundation for improvised shelters.             |
| Wooden Planks  | WoodenPlank   | 2x8  | 300g   | 1x Wooden Log + 1x Hacksaw/Hand Saw | Refined wood for walls and crates.              |
| Wooden Crate   | WoodenCrate   | 5x5  | 5kg    | 8x Planks + 16x Nails               | 50-slot persistent storage. Can be buried.      |

