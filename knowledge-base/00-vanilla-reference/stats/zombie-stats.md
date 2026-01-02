# DayZ Vanilla Zombie Stats

## Important Notes on Data
- Type/Name: The common descriptive name used to identify the specific infected variant (e.g., "Military," "Runner," "Screamer").
- Class Name (Root): The base technical identifier prefix used in configuration files (e.g., ZmbM_SoldierNormal_Base) to reference the entity group.
- HP: The hitpoints or health pool of the infected, determining how much damage is required to neutralize it.
- Damage: The amount of Health and Shock damage the infected inflicts per hit on a player.
- Speed: A qualitative or relative metric describing the infected's movement capabilities (e.g., "Fast/Runner," "Slow/Walker").
- Armor: The resistance level of the infected to specific damage types (e.g., ballistic, melee) based on their equipment (helmets, vests).
- Perception: A rating of the infected's ability to detect players via sight and sound radius.
- Location: The specific map zones or environment types where this infected variant is configured to spawn (e.g., "Military Base," "City," "Farm").
- Loot Drops: A list of items (e.g., "Canned Food," "Ammo," "Kiwi") that have a chance to appear in the infected's inventory upon death.
- Description: A text summary distinguishing the visual appearance and behavioral quirks of the infected variant.

## Civilian Infected (Common)
The most numerous enemies. Low threat individually, but dangerous in groups.

| Type/Name         | Class Name (Root)  | HP | Damage             | Speed         | Armor             | Perception | Location                | Loot Drops                 | Description                                             |
|-------------------|--------------------|----|--------------------| --------------|-------------------|------------|-------------------------|----------------------------|---------------------------------------------------------|
| Villager (Male)   | ZmbM_VillagerOld   | 50 | Low (Bleed chance) | Walk/Sprint   | None              | Medium     | Towns, Villages         | Food, Knives, Rags         | Standard infected in casual clothes.                    |
| Villager (Female) | ZmbF_VillagerOld   | 50 | Low (Bleed chance) | Walk/Sprint   | None              | Medium     | Towns, Villages         | Food, Sewing Kits          | Standard female infected.                               |
| City/Office       | ZmbM_ClerkFat      | 60 | Low                | Walk/Sprint   | None              | Medium     | Cities (Cherno/Electro) | Batt 9V, Soda, Canned Food | Wearing suits or office attire.                         |
| Hiker/Tourist     | ZmbM_HikerSkinny   | 60 | Low                | Sprint (Fast) | None              | High       | Trails, Camps           | Maps, Compass, Kiwi        | Often wears backpacks and brighter clothing.            |
| Jogger            | ZmbF_JoggerSkinny  | 50 | Low                | Sprint (Fast) | None              | High       | Residential             | Sodas, Sport Gear          | Athletic infected. Seems to aggro faster.               |
| Skater            | ZmbM_SkaterYoung   | 50 | Low                | Sprint        | Helmet (Sometimes)| Medium     | Cities                  | Sodas, Tape                | Wears skate helmet which offers slight head protection. |

## Worker Infected (Utility)
Infected wearing work gear. They often have higher health or specific useful loot.

| Type/Name    | Class Name (Root)    | HP  | Damage | Speed       | Armor             | Perception | Location        | Loot Drops                       | Description                                             |
|--------------|----------------------|-----|--------|-------------|-------------------|------------|-----------------|----------------------------------|---------------------------------------------------------|
| Police       | ZmbM_PatrolNormal    | 100 | Med    | Sprint      | Stab Vest (Torso) | High       | Police Stations | 9V, Ammo, Handcuffs, Radio       | Wearing police uniforms. Vest protects torso.           |
| Firefighter  | ZmbM_Firefighter     | 120 | Med    | Walk/Sprint | Helmet (Head)     | Med        | Fire Stations   | Axes, Extinguishers              | High health due to thick gear. Helmet blocks melee.     |
| Paramedic    | ZmbM_Paramedic       | 80  | Low    | Sprint      | None              | Med        | Hospitals       | Bandages, Tetracycline, Morphine | Excellent source of medical supplies.                   |
| Doctor       | ZmbF_Doctor          | 60  | Low    | Sprint      | None              | Med        | Hospitals       | Surgical Gloves, Meds            | Wearing white lab coats.                                |
| Construction | ZmbM_Construction    | 100 | Med    | Walk/Sprint | Hardhat (Head)    | Low        | Industrial      | Nails, Duct Tape, Hammers        | Wearing yellow/orange vests. Hardhats reflect melee.    |
| Mechanic     | ZmbM_Mechanic        | 80  | Med    | Walk/Sprint | None              | Med        | Garages, Ind    | Wrenches, Spark Plugs            | Wearing blue overalls.                                  |
| Priest       | ZmbM_PriestPopSkinny | 60  | Low    | Walk        | None              | Low        | Churches        | Unknown Food, Religious items    | Wearing black robes. Usually found alone near churches. |

## Military Infected (High Threat)
Found in military zones. They hit harder, have high health, and often wear ballistic gear that stops bullets.

| Type/Name       | Class Name (Root)  | HP   | Damage            | Speed     | Armor              | Perception    | Location           | Loot Drops                  | Description                                             |
|-----------------|--------------------|------|-------------------|-----------|--------------------|---------------|--------------------|-----------------------------|-------------------------------------------------------- |
| Soldier (Grunt) | ZmbM_SoldierNormal | 150  | High (High Bleed) | Sprint    | Low                | High          | Tents, Checkpoints | Ammo, Kiwi, Canteens        | Standard camo infected. Tougher than civilians.         |
| Heavy Soldier   | ZmbM_SoldierHeavy  | 200+ | High              | Sprint    | High (Vest+Helm)   | High          | T3/T4 Mil Bases    | Ammo, Grenades (Rare)       | Wearing Plate Carrier + Helmet. Headshots may bounce.   |
| Officer         | ZmbM_usmc_Officer  | 150  | High              | Sprint    | Med                | Very High     | T3 Mil Bases       | Pistol Ammo, Tactical Bacon | Officer cap/beret. "Screamer" behavior (alerts others). |
| Runner          | ZmbF_SoldierNormal | 100  | High              | Very Fast | Low                | High          | Tents, Airfields   | Ammo, Knives                | Female military infected. Very fast attack animation.   |
| NBC Infected    | ZmbM_NBC_Yellow    | 100  | Med               | Sprint    | Suit (Resists Gas) | Low (Muffled) | Rad Zones          | Filters, Injectors          | Found inside static gas zones. Immune to PO-X gas.      |

## Dynamic/Event Infected
Rare types that spawn during specific events or updates.

| Type/Name       | Class Name (Root) | HP   | Damage | Speed  | Armor          | Perception | Location        | Loot Drops        | Description                                    |
|-----------------|-------------------|------|--------|--------|----------------|------------|-----------------|-------------------|----------------------------------------------- |
| Mummy           | ZmbM_Mummy        | 400+ | High   | Sprint | Very High      | High       | Halloween Event | Meds, Wraps       | Extremely tanky. Eyes glow red. Bleeds on hit. |
| Santa           | ZmbM_Santa        | 60   | Low    | Walk   | None           | Low        | Christmas Event | Gifts, Beard, Hat | Wearing Santa suit. Drops wrapped boxes.       |
| Hoplon (Knight) | ZmbM_Medieval     | 150  | Med    | Walk   | Chainmail/Helm | Low        | Castles         | Helmets, Swords   | Medieval armor. Resistant to melee.            |
