# DayZ Vanilla Weapons Stats

## Important Notes on Data
- Barrel Damage: For firearms, this refers to the base Health Damage of the standard projectile fired. For melee/bladed weapons, this is n/a.
- Health, Blood, Shock: These columns refer to the Item's Max Durability (HP) and the Damage Dealt (Blood/Shock) by its standard attack (bullet for guns, swing for melee).
- Health: The item's total durability points (e.g., how much damage it can take before Ruined).
- Blood: Damage dealt to target's blood (Bleed/Gore).
- Shock: Damage dealt to target's shock (Unconscious chance).
- Light/Heavy Attack: Refers to the melee damage dealt when swinging the weapon (Left Click vs. Shift+Left Click).
- Ballistics: Based on the weapon's standard ammunition type (e.g., M4-A1 stats use 5.56x45mm values).
- Name: The human-readable label displayed in the game inventory to identify the firearm or weapon.
- Class Name: The technical identifier string used by the server configuration to spawn or reference the weapon.
- Size: The integer number of inventory grid slots the weapon occupies (width × height) when stored.
- Weight: The mass of the weapon (typically in grams), which affects weapon sway and player stamina.
- Sonic: A boolean or numeric value indicating whether the projectile travels faster than sound (causing a "crack") or is subsonic.
- Velocity: The initial speed of the projectile in meters per second (m/s) as it leaves the barrel.
- Air Friction: A coefficient (usually negative) representing how quickly the projectile slows down over distance due to drag.
- Penetration: A numeric value indicating the projectile's ability to pass through surfaces or armor plating.
- Dispersion: A value representing the weapon's inherent accuracy or "spread" in angle/radians (lower values mean higher accuracy).
- Barrel Length: The numeric length of the barrel, which modifies the base velocity and dispersion of the fired projectile.
- Health: The raw damage value inflicted on a target's health pool upon impact.
- Blood: The amount of blood loss (bleeding damage) inflicted on a target upon impact.
- Shock: The amount of unconsciousness damage inflicted on a target, affecting their ability to stay awake.
- Location: The specific military tiers or map zones (e.g., "Tier 4," "Heli Crash," "Police") where the weapon spawns.
- Rarity: A qualitative indicator describing the spawn frequency probability relative to other weapons.
- Description: A text summary explaining the weapon's caliber, firing modes, and historical or functional context.
- Variants: A list of alternative versions of the weapon (e.g., camo patterns, special editions) that share the same mechanics.

## Melee Tools
Blunt and heavy tools used for construction and defense.

| Name             | Class Name          | Size | Weight | Light | Heavy | Dura | Health | Blood | Shock | Location          | Rarity   | Variants     |
|------------------|---------------------|------|--------|-------|-------|------|--------|-------|-------|-------------------|----------|--------------|
| Crowbar          | Crowbar             | 1x5  | 2.0 kg | 12    | 19    | 1    | 180    | 10    | 15    | Industrial        | Common   | -            |
| Firefighter Axe  | FirefighterAxe      | 2x5  | 2.7 kg | 25    | 40    | 1    | 220    | 20    | 25    | Fire Station      | Uncommon | Green, Black |
| Splitting Axe    | WoodAxe             | 2x5  | 1.8 kg | 20    | 30    | 1    | 150    | 20    | 20    | Farm, Village     | Common   | -            |
| Sledgehammer     | Sledgehammer        | 2x6  | 5.0 kg | 20    | 35    | 2    | 200    | 0     | 50    | Industrial        | Common   | -            |
| Shovel           | Shovel              | 2x5  | 3.0 kg | 14    | 22    | 1    | 130    | 0     | 22    | Farm, Industrial  | Common   | -            |
| Pickaxe          | Pickaxe             | 2x5  | 2.5 kg | 19    | 30    | 1    | 160    | 10    | 25    | Industrial, Farm  | Common   | -            |
| Pipe Wrench      | PipeWrench          | 1x4  | 1.5 kg | 13    | 20    | 1    | 150    | 0     | 25    | Industrial        | Common   | -            |
| Brass Knuckles   | BrassKnuckles_Shiny | 1x2  | 0.2 kg | 8     | 15    | 0.5  | 100    | 0     | 18    | Town              | Uncommon | Dull         |

## Knives & Blades
Sharp tools for combat, skinning, and crafting.

| Name          | Class Name   | Size | Weight  | Light | Heavy | Dura | Health | Blood | Shock | Location      | Rarity   | Variants |
|---------------|--------------|------|---------|-------|-------|------|--------|-------|-------|---------------|----------|----------|
| Combat Knife  | CombatKnife  | 1x2  | 0.25 kg | 15    | 27    | 1    | 150    | 20    | 12    | Military      | Rare     | -        |
| Hunting Knife | HuntingKnife | 1x2  | 0.23 kg | 14    | 25    | 1    | 120    | 20    | 10    | Hunting       | Uncommon | -        |
| Kitchen Knife | KitchenKnife | 1x2  | 0.17 kg | 10    | 16    | 2    | 80     | 15    | 8     | Town, Village | Common   | -        |
| Steak Knife   | SteakKnife   | 1x2  | 0.10 kg | 8     | 13    | 3    | 50     | 15    | 5     | Town, Village | Common   | -        |
| Machete       | Machete      | 1x4  | 0.60 kg | 16    | 25    | 1    | 120    | 20    | 15    | Farm          | Common   | -        |
| Kukri         | Kukri        | 1x3  | 0.60 kg | 17    | 28    | 1    | 130    | 20    | 15    | Town, Hunting | Rare     | -        |
| Fange Knife   | FangeKnife   | 1x2  | 0.25 kg | 15    | 26    | 1    | 150    | 20    | 12    | Hunting       | Rare     | -        |
| Bone Knife    | BoneKnife    | 1x2  | 0.05 kg | 9     | 15    | 4    | 30     | 15    | 7     | Crafted       | Common   | -        |
| Stone Knife   | StoneKnife   | 1x2  | 0.20 kg | 7     | 12    | 5    | 30     | 10    | 5     | Crafted       | Common   | -        |
| Cleaver       | Cleaver      | 1x2  | 0.40 kg | 11    | 18    | 2    | 100    | 20    | 10    | Town, Village | Common   | -        |

## Pistols
Handguns suitable for close to medium range.

| Name      | Class Name      | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion   | Barrel Length | Health | Blood | Shock | Location       | Rarity   | Description                                          | Variants   |
|-----------|-----------------|------|--------|-------|----------|--------------|-------------|--------------|---------------|--------|-------|-------|----------------|----------|------------------------------------------------------|------------|
| IJ-70     | MakarovIJ70     | 2x2  | 0.7 kg | No    | 280      | -0.0016      | 0.8         | 0.006        | 20            | 100    | 20    | 20    | Town           | Common   | A compact semi-automatic pistol.                     | -          |
| CR-75     | CZ75            | 2x2  | 1.1 kg | Yes   | 350      | -0.003       | 0.8         | 0.004        | 25            | 150    | 25    | 25    | Police         | Uncommon | A semi-automatic pistol.                             | -          |
| Mlock-91  | Glock19         | 2x2  | 0.9 kg | Yes   | 340      | -0.003       | 0.8         | 0.0045       | 25            | 150    | 25    | 25    | Police         | Uncommon | A polymer-framed, semi-automatic pistol.             | -          |
| Kolt 1911 | Colt1911        | 2x2  | 1.1 kg | No    | 250      | -0.0014      | 0.9         | 0.004        | 33            | 180    | 30    | 35    | Military, Town | Uncommon | A single-action, semi-automatic pistol.              | Engraved   |
| FX-45     | FNX45           | 2x2  | 1.2 kg | No    | 255      | -0.0014      | 0.9         | 0.004        | 33            | 200    | 30    | 35    | Military       | Rare     | A semi-automatic pistol chambered in .45 ACP.        | -          |
| Magnum    | Magnum          | 2x3  | 1.4 kg | No    | 330      | -0.002       | 1.0         | 0.003        | 50            | 200    | 50    | 50    | Town, Village  | Rare     | A powerful revolver chambered in .357.               | -          |
| Deagle    | Deagle          | 3x2  | 1.7 kg | Yes   | 390      | -0.002       | 1.0         | 0.0035       | 50            | 220    | 50    | 50    | Town           | Rare     | A large-framed gas-operated semi-automatic pistol.   | Gold       |
| MK II     | MKII            | 2x3  | 1.3 kg | No    | 280      | -0.0012      | 0.5         | 0.003        | 15            | 120    | 10    | 10    | Town, Hunting  | Common   | An integrally suppressed .22 pistol.                 | -          |
| Longhorn  | Longhorn        | 2x4  | 1.8 kg | Yes   | 600      | -0.0008      | 1.5         | 0.001        | 110           | 200    | 100   | 110   | Hunting        | Rare     | A break-action single-shot pistol chambered in .308. | -          |
| Derringer | Derringer_Black | 1x2  | 0.4 kg | No    | 230      | -0.002       | 1.0         | 0.01         | 50            | 80     | 50    | 50    | Town           | Common   | A small double-barrel break-action pistol.           | Pink, Grey |

## Shotguns
High close-range damage weapons using buckshot or slugs.

| Name   | Class Name   | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion  | Barrel Length | Health | Blood | Shock | Location      | Rarity   | Description                           | Variants  |
|--------|--------------|------|--------|-------|----------|--------------|-------------|------------ |---------------|--------|-------|-------|---------------|----------|---------------------------------------|-----------|  
| BK-12  | Izh18Shotgun | 8x3  | 2.5 kg | Yes   | 380      | -0.007       | 0.5         | 0.003       | 112           | 200    | 120   | 120   | Town, Farm    | Common   | A single-barrel break-action shotgun. | Sawed-off |
| BK-43  | Izh43Shotgun | 8x3  | 3.1 kg | Yes   | 380      | -0.007       | 0.5         | 0.003       | 112           | 200    | 120   | 120   | Village, Farm | Common   | A double-barrel side-by-side shotgun. | Sawed-off |
| BK-133 | Mp133Shotgun | 9x3  | 3.2 kg | Yes   | 380      | -0.007       | 0.5         | 0.003       | 112           | 250    | 120   | 120   | Police, Farm  | Uncommon | A pump-action shotgun.                | -         |
| Vaiga  | Saiga        | 7x3  | 3.6 kg | Yes   | 380      | -0.007       | 0.5         | 0.004       | 112           | 300    | 120   | 120   | Military      | Rare     | A semi-automatic 12-gauge shotgun.    | -         |

## Submachine Guns (SMG)
Fast-firing weapons using pistol ammunition.

| Name           | Class Name | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion | Barrel Length | Health | Blood | Shock | Location | Rarity   | Description                                              | Variants |
|----------------|------------|------|--------|-------|----------|--------------|-------------|------------|---------------|--------|-------|-------|----------|----------|----------------------------------------------------------|----------|
| SG5-K          | MP5K       | 4x3  | 2.5 kg | Yes   | 360      | -0.003       | 0.8         | 0.003      | 25            | 250    | 25    | 25    | Military | Uncommon | A submachine gun chambered in 9mm.                       | -        |
| USG-45         | UMP45      | 5x3  | 2.5 kg | No    | 260      | -0.0014      | 0.9         | 0.003      | 33            | 250    | 30    | 35    | Military | Uncommon | A submachine gun chambered in .45 ACP.                   | -        |
| CR-61 Skorpion | CZ61       | 3x3  | 1.3 kg | No    | 290      | -0.0016      | 0.8         | 0.004      | 20            | 200    | 20    | 20    | Police   | Common   | A compact submachine gun.                                | -        |
| Bizon          | PP19       | 5x3  | 2.7 kg | No    | 290      | -0.0016      | 0.8         | 0.0035     | 20            | 250    | 20    | 20    | Military | Rare     | A submachine gun with a high-capacity helical magazine.  | -        |
| Vikhr          | Vikhr      | 5x3  | 2.2 kg | No    | 300      | 0.0005       | 1.2         | 0.003      | 55            | 250    | 55    | 55    | Military | Rare     | A compact assault rifle/SMG using 9x39mm rounds.         | -        |

## Assault Rifles & Battle Rifles
Versatile automatic rifles for all combat ranges.

| Name   | Class Name | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion | Barrel Length | Health | Blood | Shock | Location         | Rarity    | Description                                             | Variants |
|--------|------------|------|--------|-------|----------|--------------|-------------|------------|---------------|--------|-------|-------|------------------|-----------|---------------------------------------------------------|----------|
| M4-A1  | M4A1       | 8x3  | 2.9 kg | Yes   | 880      | -0.001       | 1.2         | 0.0015     | 107           | 300    | 100   | 100   | Static Gas Zones | Rare      | A selective-fire carbine.                               | Green    |
| KAM    | AKM        | 8x3  | 3.1 kg | Yes   | 715      | -0.0014      | 1.0         | 0.002      | 110           | 300    | 100   | 55    | Military         | Rare      | A modernized version of the AK-47.                      | -        |
| KA-74  | AK74       | 8x3  | 3.1 kg | Yes   | 880      | -0.0002      | 1.0         | 0.002      | 80            | 300    | 75    | 55    | Military         | Uncommon  | An assault rifle chambered in 5.45x39mm.                | Green    |
| KA-101 | AK101      | 8x3  | 3.4 kg | Yes   | 910      | -0.001       | 1.2         | 0.0015     | 96            | 300    | 100   | 100   | Military         | Rare      | An export version of the AK-74M chambered in 5.56x45mm. | -        |
| AUR AX | Aug        | 8x3  | 3.6 kg | Yes   | 880      | -0.001       | 1.2         | 0.0015     | 107           | 350    | 100   | 100   | Static Gas Zones | Very Rare | A bullpup assault rifle.                                | -        |
| M16-A2 | M16A2      | 9x3  | 4.0 kg | Yes   | 950      | -0.001       | 1.2         | 0.0015     | 107           | 300    | 100   | 100   | Military         | Uncommon  | A burst-fire assault rifle.                             | -        |
| LAR    | FAL        | 9x3  | 4.3 kg | Yes   | 840      | -0.0008      | 1.5         | 0.001      | 123           | 300    | 110   | 110   | Heli Crash       | Very Rare | A battle rifle chambered in .308.                       | -        |
| AS VAL | ASVAL      | 6x3  | 2.5 kg | No    | 300      | 0.0005       | 1.5         | 0.002      | 75            | 200    | 75    | 55    | Static Gas Zones | Rare      | An integrally suppressed assault rifle.                 | -        |

## Sniper Rifles & Long Range
Precision weapons for long-range engagements.

| Name        | Class Name   | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion   | Barrel Length | Health | Blood | Shock | Location       | Rarity    | Description                                 | Variants  |
|-------------|--------------|------|--------|-------|----------|--------------|-------------|--------------|---------------|--------|-------|-------|----------------|-----------|---------------------------------------------|-----------|  
| Mosin 91/30 | Mosin9130    | 10x3 | 4.0 kg | Yes   | 860      | -0.0009      | 1.5         | 0.001        | 150           | 300    | 110   | 110   | Town, Hunting  | Common    | A bolt-action military rifle.               | Sawed-off |
| M70 Tundra  | Winchester70 | 10x3 | 3.2 kg | Yes   | 840      | -0.0008      | 1.5         | 0.0008       | 150           | 250    | 110   | 110   | Hunting        | Rare      | A bolt-action hunting rifle.                | -         |
| Blaze       | B95          | 10x3 | 3.8 kg | Yes   | 840      | -0.0008      | 1.5         | 0.001        | 150           | 250    | 110   | 110   | Hunting        | Uncommon  | A double-barrel break-action rifle.         | Sawed-off |
| VSD         | SVD          | 10x3 | 4.3 kg | Yes   | 830      | -0.0009      | 1.5         | 0.001        | 150           | 300    | 110   | 110   | Heli Crash     | Very Rare | A semi-automatic designated marksman rifle. | -         |
| DMR         | M14          | 10x3 | 5.1 kg | Yes   | 850      | -0.0008      | 1.5         | 0.001        | 150           | 350    | 110   | 110   | Convoy         | Very Rare | A semi-automatic designated marksman rifle. | -         |
| SK 59/66    | SKS          | 9x3  | 3.8 kg | Yes   | 735      | -0.0014      | 1.0         | 0.0015       | 110           | 300    | 100   | 55    | Military       | Uncommon  | A semi-automatic carbine.                   | -         |
| BK-18       | Izh18        | 8x3  | 2.8 kg | Yes   | 700      | -0.0014      | 1.0         | 0.002        | 110           | 200    | 100   | 55    | Town, Farm     | Common    | A single-shot break-action rifle.           | Sawed-off |
| SSG 82      | SSG82        | 9x3  | 3.0 kg | Yes   | 950      | -0.0002      | 1.0         | 0.001        | 135           | 200    | 100   | 100   | Police         | Rare      | A bolt-action border patrol rifle.          | -         |
| Pioneer     | Scout        | 8x3  | 3.0 kg | Yes   | 900      | -0.001       | 1.2         | 0.0015       | 107           | 200    | 100   | 100   | Police, Prison | Uncommon  | A bolt-action scout rifle.                  | -         |
| CR-527      | CZ527        | 9x3  | 2.7 kg | Yes   | 760      | -0.0014      | 1.0         | 0.0015       | 110           | 200    | 100   | 55    | Town, Hunting  | Common    | A bolt-action carbine.                      | -         |

## Special Weapons
Unique weapons with distinct mechanics.

| Name        | Class Name | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion | Barrel Length | Light | Heavy | Health | Blood | Shock | Location      | Rarity   | Description                                                  | Variants     |
|-------------|------------|------|--------|-------|----------|--------------|-------------|------------|---------------|-------|-------|--------|-------|-------|---------------|----------|--------------------------------------------------------------|--------------|  
| Crossbow    | Crossbow   | 9x3  | 3.4 kg | No    | 85       | -0.002       | 0.8         | 0.005      | 100           | 12    | 25    | 200    | 100   | 50    | Hunting, Town | Uncommon | A weapon consisting of a bow mounted on a stock.             | Black, Green |
| M79 Thumper | M79        | 6x3  | 2.7 kg | No    | 75       | 0            | 0           | 0          | Explosion     | 10    | 20    | 200    | -     | -     | Military      | Rare     | A single-shot grenade launcher.                              | -            |
| Flaregun    | Flaregun   | 2x2  | 0.4 kg | No    | 50       | -0.02        | 0           | 0.01       | 5             | 5     | 10    | 80     | 0     | 5     | Coast, Ind    | Common   | A pistol that shoots flares.                                 | -            |
| Spear       | Spear      | 1x8  | 1.5 kg | -     | -        | -            | -           | -          | -             | 18    | 30    | 40     | 20    | 20    | Crafted       | Common   | An improvised spear made from a long stick and a bone knife. | -            |

