# DayZ Vanilla Ammunition Stats

## Important Notes on Data
- Name: The colloquial or display name of the ammunition as seen by players in the game inventory.
- Class Name: The precise internal variable name (ID) used in the game code and scripts to spawn or manipulate this item.
- Size: The inventory grid dimensions (Width x Height) required to store one box or stack of this ammo.
- Weight: The mass of a full stack or box of this ammo, usually expressed in grams, which affects player stamina.
- Stack: The maximum number of loose rounds that can be combined into a single inventory slot.
- Sonic: Indicates whether the projectile breaks the sound barrier ("Supersonic") creating a loud crack, or travels slower than sound ("Subsonic") for stealth.
- Velocity: The speed in meters per second (m/s) the bullet travels, which acts as the primary multiplier for damage calculation.
- Air Friction: A negative value representing aerodynamic drag; values closer to zero mean the bullet retains speed (and therefore damage) better over long distances.
- Penetration: A numerical rating of the bullet's ability to punch through environmental objects (walls/trees) and retain damage after hitting armor.
- Deflect: A value determining the probability of the bullet ricocheting off hard surfaces or angled armor instead of penetrating.
- Dispersion: A value representing the bullet's inherent inaccuracy spread; lower numbers indicate higher precision and tighter grouping.
- Barrel: The specific barrel length or test weapon used to calculate the damage and velocity stats shown in this row.
- Health: The raw damage (HP) dealt to the target's life pool upon impact.
- Blood: The amount of immediate blood loss or bleed damage applied to the target upon impact.
- Shock: The concussion damage dealt to the target; exceeding the target's shock threshold causes immediate unconsciousness.
- Location: The specific map zones or tiered areas (e.g., Military, Hunting, Police) where this ammo spawns.
- Rarity: A qualitative tag indicating the spawn frequency and difficulty of finding this item.
- Description: The official in-game text tooltip that provides lore or basic usage instructions.
- Variants: Lists alternative versions of this ammo type, such as Tracers (visual flight path) or Rubber (non-lethal) rounds.

## Pistol & SMG Ammunition
Low-velocity rounds used in handguns and submachine guns.

| Name     | Class Name  | Size | Weight | Stack | Sonic | Velocity | Air Friction | Penetration | Deflect | Dispersion | Barrel | Health | Blood | Shock | Location       | Rarity   | Description                                  | Variants |
|----------|-------------|------|--------|-------|-------|----------|--------------|-------------|---------|------------|--------|--------|-------|-------|----------------|----------|----------------------------------------------|----------|
| .22 LR   | Ammo_22     | 1x1  | 2 g    | 50    | No    | 280      | -0.0012      | 0.5         | 30      | 0          | 15     | n/a    | 10    | 10    | Town, Hunting  | Common   | A small-caliber rimfire cartridge.           | -        |
| .380 ACP | Ammo_380    | 1x1  | 6 g    | 35    | No    | 300      | -0.0016      | 0.6         | 30      | 0          | 20     | n/a    | 20    | 20    | Town           | Common   | A rimless, straight-walled pistol cartridge. | -        |
| 9mm      | Ammo_9x19   | 1x1  | 8 g    | 25    | Yes   | 350      | -0.002       | 0.8         | 30      | 0          | 25     | n/a    | 25    | 25    | Town, Police   | Common   | A rimless, tapered firearms cartridge.       | -        |
| .45 ACP  | Ammo_45ACP  | 1x1  | 15 g   | 25    | No    | 260      | -0.0014      | 0.9         | 30      | 0          | 33     | n/a    | 30    | 35    | Military, Town | Uncommon | A rimless straight-walled handgun cartridge. | -        |
| .357 Mag | Ammo_357    | 1x1  | 10 g   | 20    | Yes   | 390      | -0.002       | 1.0         | 30      | 0          | 50     | n/a    | 50    | 50    | Town, Hunting  | Uncommon | A rimmed, centerfire cartridge.              | -        |

## Intermediate Rifle Ammunition
Standard cartridges for assault rifles and carbines.

| Name      | Class Name  | Size | Weight | Stack | Sonic | Velocity | Air Friction | Penetration | Deflect | Dispersion | Barrel | Health | Blood | Shock | Location            | Rarity   | Description                                        | Variants            |
|-----------|-------------|------|--------|-------|-------|----------|--------------|-------------|---------|------------|--------|--------|-------|-------|---------------------|----------|----------------------------------------------------|---------------------|
| 5.45x39mm | Ammo_545x39 | 1x1  | 8 g    | 20    | Yes   | 880      | -0.0002      | 1.0         | 10      | 0          | 80     | n/a    | 75    | 55    | Military            | Common   | A rimless bottlenecked rifle cartridge.            | Tracer              |
| 5.56x45mm | Ammo_556x45 | 1x1  | 8 g    | 20    | Yes   | 910      | -0.001       | 1.2         | 10      | 0          | 107    | n/a    | 100   | 100   | Military            | Uncommon | A rimless bottlenecked intermediate cartridge.     | Tracer              |
| 7.62x39mm | Ammo_762x39 | 1x1  | 12 g   | 20    | Yes   | 730      | -0.0014      | 1.0         | 10      | 0          | 110    | n/a    | 100   | 55    | Military, Hunting   | Common   | A rimless bottlenecked intermediate cartridge.     | Tracer              |
| 9x39mm    | Ammo_9x39   | 1x1  | 16 g   | 20    | No    | 300      | 0.0005       | 1.2         | 20      | 0          | 55     | n/a    | 55    | 55    | Military (Tier 3/4) | Rare     | A subsonic rifle cartridge based on the 7.62x39mm. | AP (Armor Piercing) |

## Full-Power / Sniper Ammunition
High-damage rounds for long-range rifles and LMGs.

| Name       | Class Name  | Size | Weight | Stack | Sonic | Velocity | Air Friction | Penetration | Deflect | Dispersion | Barrel | Health | Blood | Shock | Location          | Rarity   | Description                              | Variants |
|------------|-------------|------|--------|-------|-------|----------|--------------|-------------|---------|------------|--------|--------|-------|-------|-------------------|----------|------------------------------------------|----------|
| .308 Win   | Ammo_308Win | 1x1  | 15 g   | 20    | Yes   | 840      | -0.0008      | 1.5         | 10      | 0          | 110    | n/a    | 100   | 110   | Hunting           | Uncommon | A rimless, bottlenecked rifle cartridge. | Tracer   |
| 7.62x54mmR | Ammo_762x54 | 1x1  | 18 g   | 20    | Yes   | 860      | -0.0009      | 1.5         | 10      | 0          | 150    | n/a    | 110   | 110   | Military, Hunting | Uncommon | A rimmed rifle cartridge.                | Tracer   |

## Shotgun Ammunition
Shells for 12-gauge shotguns.

| Name        | Class Name          | Size | Weight | Stack | Sonic | Velocity | Air Friction | Penetration | Deflect | Dispersion | Barrel  | Health | Blood | Shock | Location      | Rarity   | Description                                           | Variants |
|-------------|---------------------|------|--------|-------|-------|----------|--------------|-------------|---------|------------|---------|--------|-------|-------|---------------|----------|-------------------------------------------------------|----------|
| 12ga Buck   | Ammo_12gaPellets    | 1x1  | 35 g   | 20    | Yes   | 380      | -0.007       | 0.5         | 0       | 0          | 14 (x8) | n/a    | 15    | 15    | Town, Hunting | Common   | A shotgun shell filled with lead pellets.             | -        |
| 12ga Slug   | Ammo_12gaSlug       | 1x1  | 25 g   | 20    | Yes   | 400      | -0.0045      | 0.8         | 0       | 0          | 110     | n/a    | 110   | 110   | Town, Hunting | Uncommon | A shotgun shell containing a single solid projectile. | -        |
| 12ga Rubber | Ammo_12gaRubberSlug | 1x1  | 15 g   | 20    | No    | 120      | -0.012       | 0.2         | 0       | 0          | 5       | n/a    | 0     | 120   | Police        | Common   | A shotgun shell containing a rubber slug.             | -        |

(Note: "12ga Buck" total damage if all 8 pellets hit is 112 Health, 120 Blood, 120 Shock.)

## Specialty & Explosive Ammunition
Projectiles for launchers, bows, and flare guns.

| Name           | Class Name            | Category | Size | Weight  | Stack | Sonic | Velocity | Air Friction | Penetration | Deflect | Dispersion | Barrel    | Health | Blood | Shock | Location         | Rarity    | Description                                    | Variants                 |
|----------------|-----------------------|----------|------|---------|-------|-------|----------|--------------|-------------|---------|------------|-----------|--------|-------|-------|------------------|-----------|------------------------------------------------|--------------------------|
| 40mm Explosive | Ammo_40mm_Explosive   | Grenade  | 1x2  | 0.23 kg | n/a   | No    | 75       | 0            | 0           | 0       | 0          | Explosion | n/a    | n/a   | n/a   | Military         | Rare      | A high-explosive grenade for the M79 launcher. | -                        |
| 40mm Smoke     | Ammo_40mm_Smoke_Color | Grenade  | 1x2  | 0.23 kg | n/a   | No    | 75       | 0            | 0           | 0       | 0          | Impact    | n/a    | n/a   | n/a   | Military         | Uncommon  | A smoke grenade for the M79 launcher.          | Red, Green, Black, White |
| 40mm Chem      | Ammo_40mm_ChemGas     | Grenade  | 1x2  | 0.23 kg | n/a   | No    | 75       | 0            | 0           | 0       | 0          | Gas       | n/a    | n/a   | n/a   | Static Gas Zones | Very Rare | A gas grenade for the M79 launcher.            | -                        |
| Bolt           | Ammo_HuntingBolt      | Bolt     | 1x3  | 0.05 kg | 5     | No    | 85       | -0.002       | 0.8         | 30      | 0          | 100       | n/a    | 100   | 50    | Hunting, Town    | Uncommon  | A short bolt for a crossbow.                   | Improvised               |
| Flare          | Ammo_Flare            | Flare    | 1x2  | 0.05 kg | n/a   | No    | 50       | -0.02        | 0           | 0       | 0          | 5         | n/a    | 0     | 5     | Coast, Ind       | Common    | A flare cartridge.                             | Red, Green, Blue         |