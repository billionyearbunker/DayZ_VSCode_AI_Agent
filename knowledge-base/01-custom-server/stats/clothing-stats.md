# DayZ Custom Clothing Stats

## Important Notes on Data
If you are using this data to configure types.xml or cfgspawnabletypes.xml, keep these notes in mind:
- Class Name: This must match the exact string in the game files. Note that for items with variants, the base class might be different, or you may need to list every color variant individually (e.g., M65Jacket_Olive, M65Jacket_Black).
- Sex: In the actual game code, most items auto-adjust to the character model. However, for a database or trader config, designating "Dresses" as Female prevents male characters from spawning with them if you are building loadout scripts.
- Protection: This is a complex stat in DayZ code (derived from insulation values and damage modifiers). For a simple database, "Low/Med/High" or "Ballistic" is usually easier to read than the raw float values.
- Name: The human-readable display string used in the game's user interface to identify the item.
- Class Name: The exact, case-sensitive technical identifier used in server files (like types.xml) to spawn or reference the object.
- Size: The integer value representing the number of inventory grid slots the item occupies when stored inside another container.
- Weight: The numeric mass of the item (usually in grams), used to calculate the player's total load and stamina penalty.
- Civ/Mil: A categorical tag distinguishing the item's origin as either Civilian or Military to determine loot tier logic.
- Protection: A composite summary of the item's defensive attributes, including thermal insulation, water absorbency, and ballistic resistance.
- Sex: Specifies the character model compatibility, indicating if the clothing fits Male, Female, or Universal ("Uni") skeletons.
- Storage: The integer capacity of the item's internal container, defining how many slots it adds to the player's inventory when worn.
- Location: A set of usage tags or map zones (e.g., "Town," "Military") defining valid spawn points for the item.
- Rarity: A qualitative value describing the spawn frequency probability relative to other items in the loot table.
- Variants: A list of related class names that share the same base model but utilize different texture or color maps.

## Tops (Jackets, Coats, Shirts)
High utility items with storage and insulation.

| Name             | Class Name            | Size | Weight | Civ/Mil  | Protection                  | Sex    | Storage | Location           | Rarity | Variants                                         |
|------------------|-----------------------|------|--------|----------|-----------------------------|--------|---------|--------------------|--------|--------------------------------------------------|
| Field Jacket     | M65Jacket_Color       | 2x2  | 800g   | Military | High Insul / Water Res      | Unisex | 42      | Tier 2, 3 Mil      | Rare   | Olive, Black, Khaki, Tan                         |
| Hiking Jacket    | HikingJacket_Color    | 2x2  | 700g   | Civ      | High Insul                  | Unisex | 30      | Residential, Camp  | Common | Red, Blue, Green, Black                          |
| Hunting Jacket   | HuntingJacket_Color   | 2x3  | 1.1kg  | Hunting  | Best Insul / Water Res      | Unisex | 30      | Hunting, Farm      | Med    | Autumn, Spring, Summer, Winter, Brown            |
| Tactical Shirt   | TacticalShirt_Color   | 2x2  | 450g   | Military | Med Insul                   | Unisex | 42      | Tier 3, 4 Mil      | Rare   | Black, Olive, Tan, Grey                          |
| Peacoat          | WoolCoat_Color        | 2x3  | 1.5kg  | Civ      | High Insul                  | Unisex | 30      | City, Coast        | Med    | Black, Blue, Red, Green, Beige                   |
| Raincoat         | Raincoat_Color        | 2x2  | 600g   | Civ      | Waterproof                  | Unisex | 20      | Coast, Town        | Common | Orange, Green, Yellow, Pink, Blue, Red           |
| Quilted Jacket   | QuiltedJacket_Color   | 2x2  | 500g   | Civ      | Med Insul                   | Unisex | 30      | Town, Village      | Common | Blue, Green, Grey, Orange, Red, Violet, Yellow   |
| Paramedic Jacket | ParamedicJacket_Color | 2x2  | 500g   | Civ      | Med Insul                   | Unisex | 30      | Hospital, Fire Stn | Med    | Blue, Crimson, Green                             |
| Bomber Jacket    | BomberJacket_Color    | 2x2  | 600g   | Civ      | Med Insul                   | Unisex | 30      | City, Industry     | Med    | Black, Brown, Blue, Grey, Maroon, Olive, SkyBlue |
| BDU Jacket       | BDUJacket             | 2x2  | 500g   | Military | Med Insul                   | Unisex | 42      | Tier 3 Mil         | Rare   | Woodland (Base only)                             |
| USMC Jacket      | USMCJacket_Color      | 2x2  | 500g   | Military | Med Insul                   | Unisex | 42      | Tier 3 Mil         | Rare   | Woodland, Desert                                 |
| Nurse Dress      | NurseDress_Color      | 1x3  | 250g   | Civ      | Low Insul                   | Female | 0       | Medical            | Common | Blue, White                                      |
| Mini Dress       | MiniDress_Color       | 1x3  | 250g   | Civ      | Low Insul                   | Female | 0       | City               | Common | Pink, Red, Blue, Green, Grim                     |
| Rider Jacket     | RidersJacket_Color    | 2x2  | 1.8kg  | Civ      | Low Insul / High Bleed Prot | Unisex | 30      | City, Biker        | Rare   | Black                                            |

## Bottoms (Pants, Shorts, Skirts)
Pants usually dictate the remaining storage capacity of a player.

| Name            | Class Name           | Size | Weight | Civ/Mil  | Protection     | Sex    | Storage | Location       | Rarity | Variants                                 |
|-----------------|----------------------|------|--------|----------|----------------|--------|---------|----------------|--------|------------------------------------------|
| Cargo Pants     | CargoPants_Color     | 2x2  | 500g   | Civ      | Med Insul      | Unisex | 30      | City, Industry | Common | Beige, Black, Blue, Green, Grey          |
| Hunter Pants    | HunterPants_Color    | 2x2  | 650g   | Hunting  | Best Insul     | Unisex | 30      | Hunting, Farm  | Med    | Autumn, Spring, Summer, Winter, Brown    |
| Jeans           | Jeans_Color          | 2x2  | 400g   | Civ      | Low Insul      | Unisex | 12      | Everywhere     | Common | Blue, Black, Brown, Green, Grey          |
| BDU Pants       | BDUPants             | 2x2  | 500g   | Military | Med Insul      | Unisex | 30      | Tier 3 Mil     | Rare   | Woodland                                 |
| USMC Pants      | USMCPants_Color      | 2x2  | 500g   | Military | Med Insul      | Unisex | 30      | Tier 3 Mil     | Rare   | Woodland, Desert                         |
| Paramedic Pants | ParamedicPants_Color | 2x2  | 400g   | Civ      | Med Insul      | Unisex | 30      | Medical        | Med    | Blue, Crimson, Green                     |
| Tracksuit Pants | TrackSuitPants_Color | 2x2  | 300g   | Civ      | Low Insul      | Unisex | 12      | Residential    | Common | Black, Blue, Green, Red, LightBlue       |
| Skirt           | Skirt_Color          | 1x2  | 200g   | Civ      | Low Insul      | Female | 0       | City           | Common | Blue, Red, Yellow, White                 |
| Short Jeans     | ShortJeans_Color     | 1x2  | 200g   | Civ      | Very Low Insul | Unisex | 12      | Coast, City    | Common | Black, Blue, Brown, DarkBlue, Green, Red |
| Canvas Pants    | CanvasPants_Color    | 2x2  | 450g   | Civ      | Low Insul      | Unisex | 30      | Farm, Village  | Common | Beige, Blue, Grey, Red, Violet           |

## Vests & Armor
Crucial for protection and quick-access storage.

| Name          | Class Name          | Size | Weight | Civ/Mil  | Protection               | Sex    | Storage           | Location      | Rarity  | Variants                  |
|---------------|---------------------|------|--------|----------|--------------------------|--------|-------------------|---------------|---------|---------------------------|
| Plate Carrier | PlateCarrierVest    | 4x3  | 12kg   | Military | High Ballistic           | Unisex | 0 (Need pouch)    | Tier 3/4 Mil  | V. Rare | Green, Black, Camo        |
| Press Vest    | PressVest_Color     | 3x3  | 4kg    | Civ/Mil  | Med Ballistic            | Unisex | 24                | Police, Press | Rare    | Blue, LightBlue           |
| Stab Vest     | PoliceVest          | 2x2  | 2kg    | Police   | Anti-Melee/Low Ballistic | Unisex | 0                 | Police Stn    | Med     | Police                    |
| Tactical Vest | TacticalVest        | 2x2  | 1kg    | Military | Low Protection           | Unisex | 35                | Tier 3 Mil    | Rare    | Black, Olive, Camo        |
| Assault Vest  | UKAssaultVest_Color | 3x3  | 1.5kg  | Military | None                     | Unisex | 30                | Tier 2 Mil    | Med     | Black, Green, Khaki, Camo |
| Field Vest    | SmershVest          | 2x2  | 1kg    | Military | None                     | Unisex | 0 (Backpack slot) | Heli Crash    | V. Rare | Olive                     |
| Hunting Vest  | HuntingVest         | 2x2  | 800g   | Hunting  | None                     | Unisex | 30                | Hunting       | Med     | -                         |

## Backpacks
The primary inventory expansion.

| Name              | Class Name        | Size | Weight | Civ/Mil  | Protection | Sex    | Storage | Location      | Rarity | Variants                                | Notes                  |
|-------------------|-------------------|------|--------|----------|------------|--------|---------|---------------|--------|-----------------------------------------|------------------------|
| Mountain Backpack | MountainBag_Color | 5x6  | 2kg    | Civ      | None       | Unisex | 80      | Residential   | Med    | Blue, Green, Orange, Red                | -                      |
| Field Backpack    | AliceBag_Color    | 6x6  | 2kg    | Military | None       | Unisex | 90      | Tier 3 Mil    | Rare   | Black, Green, Camo                      | -                      |
| Tactical Backpack | TortillaBag       | 5x5  | 1.5kg  | Military | None       | Unisex | 63      | Tier 3 Mil    | Rare   | -                                       | -                      |
| Assault Backpack  | AssaultBag_Color  | 5x4  | 1.2kg  | Military | None       | Unisex | 42      | Tier 2 Mil    | Med    | Black, Green, Ttsko                     | -                      |
| Hunting Backpack  | HuntingBag        | 5x6  | 1.5kg  | Hunting  | None       | Unisex | 63      | Hunting       | Med    | Hannah's, Olive                         | -                      |
| Drybag            | DryBag_Color      | 5x5  | 1.5kg  | Civ      | Waterproof | Unisex | 63      | Coast, Boat   | Med    | Black, Blue, Green, Orange, Red, Yellow | -                      |
| Taloon Backpack   | TaloonBag_Color   | 4x4  | 800g   | Civ      | None       | Unisex | 42      | City, House   | Common | Blue, Green, Orange, Violet             | -                      |
| School Backpack   | ChildBag_Color    | 3x4  | 600g   | Civ      | None       | Unisex | 20      | School, House | Common | Blue, Green, Red                        | -                      |
| Burlap Backpack   | BurlapSackCover   | 2x2  | 200g   | Crafted  | None       | Unisex | 30      | Crafted       | -      | -                                       | Requires Rope + Burlap |

## Headgear (Helmets, Hats, Masks)
Critical for damage mitigation and insulation.

| Name             | Class Name            | Size | Weight | Civ/Mil    | Protection         | Sex    | Storage | Location      | Rarity | Variants                                          | Notes                 |
|------------------|-----------------------|------|--------|------------|--------------------|--------|---------|---------------|--------|---------------------------------------------------|-----------------------|
| Assault Helmet   | GorkaHelmet           | 2x2  | 1.2kg  | Military   | High Ballistic     | Unisex | -       | Tier 3 Mil    | Rare   | Black, Green, Visor attachable                    | -                     |
| Tactical Helmet  | Mich2001Helmet        | 2x2  | 1.2kg  | Military   | High Ballistic     | Unisex | -       | Tier 3 Mil    | Rare   | Green, Black, Camo                                | -                     |
| Ballistic Helmet | BallisticHelmet_Color | 2x2  | 1.3kg  | Military   | High Ballistic     | Unisex | -       | Tier 3 Mil    | Rare   | Green, Black, UN (Blue)                           | -                     |
| Great Helm       | GreatHelm             | 3x3  | 2kg    | Historical | Melee Prot/Low Vis | Unisex | -       | Castles       | Rare   | -                                                 | -                     |
| Moto Helmet      | MotoHelmet_Color      | 2x2  | 1kg    | Civ        | Shock Prot         | Unisex | -       | Garages       | Common | Black, Blue, Green, Red, White, Lime              | -                     |
| Ushanka          | Ushanka_Color         | 2x2  | 300g   | Civ        | Best Insulation    | Unisex | -       | Village, Cold | Med    | Black, Blue, Green                                | -                     |
| Beanie           | BeanieHat_Color       | 1x2  | 150g   | Civ        | High Insulation    | Unisex | -       | Everywhere    | Common | Beige, Black, Blue, Brown, Green, Grey, Pink, Red | -                     |
| Radar Cap        | RadarCap_Color        | 1x2  | 100g   | Civ        | Med Insulation     | Unisex | -       | Coast         | Common | Black, Blue, Brown, Green, Red                    | -                     |
| Gas Mask         | GasMask               | 2x2  | 800g   | Civ/Mil    | NBC Prot           | Unisex | -       | Fire Stn, Mil | Med    | -                                                 | -                     |
| Combat Gas Mask  | AirborneMask          | 2x2  | 900g   | Military   | NBC Prot           | Unisex | -       | Tier 3 Mil    | Rare   | -                                                 | -                     |
| Nvg Headstrap    | NVGHeadstrap          | 2x2  | 300g   | Military   | None               | Unisex | -       | Tier 2/3 Mil  | Med    | -                                                 | Allows NVG attachment |

## Accessories (Hands, Feet, Belts)
Often overlooked but vital for survival.

| Name            | Class Name           | Size | Weight | Civ/Mil  | Protection      | Sex    | Storage     | Location    | Rarity | Variants                               | Notes                               |
|-----------------|----------------------|------|--------|----------|-----------------|--------|-------------|-------------|--------|----------------------------------------|-------------------------------------|
| Assault Boots   | MilitaryBoots_Color  | 2x2  | 1.4kg  | Military | High Durability | Unisex | Knife Slot  | Tier 3 Mil  | Med    | Beige, Black, Blueline, Brown, Redpunk | -                                   |
| Jungle Boots    | JungleBoots_Color    | 2x2  | 1.2kg  | Military | High Water Res  | Unisex | -           | Tier 3 Mil  | Rare   | Beige, Black, Brown, Green, Olive      | -                                   |
| Hiking Boots    | HikingBoots_Color    | 2x2  | 1.1kg  | Civ      | Med Durability  | Unisex | -           | Town, Camp  | Common | Brown, Black                           | -                                   |
| Wellies         | Wellies_Color        | 2x2  | 800g   | Civ      | Waterproof      | Unisex | -           | Farm, Coast | Common | Black, Brown, Green, Grey              | -                                   |
| Tactical Gloves | TacticalGloves_Color | 1x2  | 200g   | Military | High Insul      | Unisex | -           | Tier 3 Mil  | Rare   | Beige, Black, Green                    | -                                   |
| Working Gloves  | WorkingGloves_Color  | 1x2  | 150g   | Civ      | Med Insul       | Unisex | -           | Industry    | Common | Beige, Black, Yellow                   | -                                   |
| Surgical Gloves | SurgicalGloves_Color | 1x1  | 50g    | Medical  | None            | Unisex | -           | Hospital    | Common | Blue, Green, White                     | -                                   |
| Military Belt   | MilitaryBelt         | 1x2  | 200g   | Military | -               | Unisex | Attachments | Tier 3 Mil  | Rare   | -                                      | Holds Canteen + Gun Holster + Knife |
| Rope Belt       | RopeBelt             | 1x1  | 100g   | Crafted  | -               | Unisex | Attachments | Crafted     | -      | -                                      | Holds Knife                         |

