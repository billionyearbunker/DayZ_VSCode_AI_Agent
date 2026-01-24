# How to Create AI Patrols

---

## Overview of Most Recent Changes

### Expansion 1.9.50 (2025-12-22)
- Added **DefaultStance** [Jump To]
- Added **DefaultLookAngle** [Jump To]
- Added **MaxFlankingDistance** [Jump To]
- Added **EnableFlankingOutsideCombat** [Jump To]

### Expansion 1.9.41 (2025-10-10)
- Added **LootDropOnDeath** [Jump To]

### Expansion 1.9.34 (2025-08-22)
- Merged **ObjectPatrols** into **Patrols**

### Expansion 1.9.23 (2025-05-14)
- Added **LoadBalancingCategory** [Jump To] and **FormationScale** [Jump To]

### Expansion 1.9.14 (2025-02-12)
- Added extended description for new **LootingBehaviour** options [Jump To]

### Expansion 1.9.0 (2024-07-25)
- Added **Persist** option [Jump To]
- Added new possible value \"RANDOM\" for **Faction** option [Jump To]
- Added new possible value \"ROAMING\" for **Behaviour** option [Jump To]
- Changed **UnlimitedReload** to a bitmask to allow different behavior per target type [Jump To]

---

## 1. Finding AIPatrolSettings.json

Inside your `mpmissions/dayzoffline.mapname/expansion/settings/` you will find the **AIPatrolSettings.json**

---

## 2. Adding a New Patrol

The easiest way to create a new patrol is using the in-game AI menu. Set yourself as admin in AISettings.json, spawn a few companion AI, use CTRL+click to set waypoints, and select \"Export Patrol\" from the AI menu. You can then edit the exported file to your liking and copy the patrol into AIPatrolSettings.json.

---

## Patrol Parameters

### **`Name`**
- **Type**: String
- **Description**: Allows you to give a name for each patrol so you know what is what. It is also used as the group name in logs

---

### **`Persist`**
- **Type**: Boolean
- **Description**: If Name is given and unique, alive patrol members will be saved when despawning (also at server restarts) and restored with all their gear at the last position when respawning
- **Note**: This is only supported if ObjectClassName is not set

---

### **`Faction`**
- **Type**: String
- **Description**: This setting allows you to specify what faction this patrol will be in

When an AI encounters another AI with a different faction, then if either faction considers the other as hostile, combat will ensue. Peaceful encounters will only happen if both factions see each other as neutral.

**Note**: Any AI that is attacked will turn hostile even if it originally considered the attacker's faction as neutral.

#### Available Factions

- **West** → Considered hostile by any faction except Civilian and other West
- **East** → Considered hostile by any faction except Civilian and other East
- **Raiders** → Considered hostile by everyone, including other Raiders (unless they are part of the same group)
- **Mercenaries** → Considered hostile by any faction except other Mercenaries
- **Civilian** → Considered neutral by any faction
- **Passive** → Completely passive, will not react to other entities and be ignored by other factions
- **Guards** → Always neutral toward other guards, neutral toward other AI and players as long as they don't raise their weapon
- **InvincibleGuards** → Like guards, but can't be killed
- **Shamans** → Considered hostile by everyone except other Shamans, won't attack or be attacked by Zs and animals
- **Observers** → Will only look at other entities, but not engage in combat
- **InvincibleObservers** → Like observers, but can't be killed
- **YeetBrigade** → Same as guard faction but won't pick up weapons and has insanely strong melee (one-shots bears with their fists) that send their victim flying. More of a showcase for faction abilities than something you should actually use
- **InvincibleYeetBrigade** → Like YeetBrigade, but can't be killed
- **Brawlers** → Seen as hostile by any faction except Civilian and other Brawlers. Very strong melee (not as strong as YeetBrigade) that can one-shot Infected with fists
- **RANDOM** → Chooses one of the above factions that are not invincible, observer or passive and don't have special melee abilities

---

### **`Formation`**
- **Type**: String
- **Description**: Formation of the group
- **Valid Values**: Column, InvColumn, File, InvFile, Vee, InvVee, Wall, Star, StarDot, Circle, CircleDot or RANDOM

---

### **`FormationScale`**
- **Type**: Float
- **Description**: How far apart the individual formation positions are
- **Details**:
  - For formations that are on a grid (like Vee, InvVee, Wall, Column and InvColumn), the value determines the side length of the grid in meters
  - For formations that are not on a grid (like Star, StarDot, Circle and CircleDot), the value roughly determines the distance between the positions (in case of star-based formations, the inner positions, with distances between outer positions scaled accordingly)
- **Default**: -1.0 = use value from top of AIPatrolSettings.json (fall back to AISettings.json if also -1)

---

### **`FormationLooseness`**
- **Type**: Float
- **Description**: How loose the formation is, i.e. how close each AI tries to stay to their respective position in the formation. In meters
- **Examples**:
  - `0` = will try to follow formation exactly
  - `0.5` = loose formation
  - `1.0` = very loose formation

---

### **`Loadout`**
- **Type**: String
- **Description**: The name of your loadout.json containing the weapons, outfit and gear they will carry with them
- **Example**: \"HumanLoadout\"

### **`Units`**
- **Type**: Array
- **Description**: If you want specific AI to spawn, enter the eAI classnames here, else leave empty. Note that it will pick classnames randomly from the list UNLESS you set NumberOfAI (see below) to EXACTLY the number of classnames you enter here (in which case it will spawn the exact set you entered)

**Example:**

```json
"Units": [
    "eAI_SurvivorF_Eva",
    "eAI_SurvivorM_Mirek",
    "eAI_SurvivorF_Judy",
    "eAI_SurvivorM_Guo"
]
```

---
### **`NumberOfAI`**
- **Type**: Integer
- **Description**: How many AI will be in this patrol

**Note**: If you set this setting to a negative number, the system will spawn a random amount of AI between 1 and the specified number with the sign removed.

For example `-6` will tell the game to spawn between 1 and 6 AI.

---

### **`Behaviour`**
- **Type**: String
- **Description**: Desired behaviour of your patrol

**Valid Values:**
- **HALT** → The patrol won't move
- **ONCE** → The patrol will follow the waypoints from start to finish, then stop
- **LOOP** → The patrol will follow the waypoints from start to finish, then return to start and repeat. Should only be used if the last waypoint is close to the first waypoint, as the AI will just go in a more or less straight line from finish back to start
- **ALTERNATE** → The patrol will follow the waypoints from start to finish, then from finish to start and repeat
- **HALT_OR_ALTERNATE** → The patrol will spawn with a random behaviour of either HALT or ALTERNATE
- **HALT_OR_LOOP** → The patrol will spawn with a random behaviour of either HALT or LOOP
- **ROAMING** → Only the starting waypoint will be used, then the AI will go off and pick destination locations on its own

---
### **`LootingBehaviour`**
- **Type**: String
- **Description**: Desired AI looting behavior

**Note**: Options can be combined like so:

```json
"LootingBehaviour": "WEAPONS | BANDAGES | CLOTHING_HIPS | CLOTHING_BACK_SMALL | UPGRADE"
```

**Available Options:**
- `WEAPONS_FIREARMS`
- `WEAPONS_LAUNCHERS`
- `WEAPONS_MELEE`
- `WEAPONS` → Same as WEAPONS_FIREARMS | WEAPONS_LAUNCHERS | WEAPONS_MELEE
- `BANDAGES`
- `CLOTHING_ARMBAND`
- `CLOTHING_BACK_LARGE`
- `CLOTHING_BACK_MEDIUM`
- `CLOTHING_BACK_SMALL`
- `CLOTHING_BACK` → Same as all CLOTHING_BACK_* options combined
- `CLOTHING_BODY`
- `CLOTHING_EYEWEAR`
- `CLOTHING_FEET`
- `CLOTHING_GLOVES`
- `CLOTHING_HEADGEAR`
- `CLOTHING_HIPS`
- `CLOTHING_LEGS`
- `CLOTHING_MASK`
- `CLOTHING_MELEE`
- `CLOTHING_SHOULDER`
- `CLOTHING_VEST`
- `CLOTHING` → Same as all the other CLOTHING_* options combined (except CLOTHING_SIMILAR and CLOTHING_IDENTICAL)
- `CLOTHING_IDENTICAL` → Will only loot identical clothing to the one the AI is currently wearing
- `CLOTHING_SIMILAR` → Will only loot similar clothing to the one the AI is currently wearing (i.e. same type, different color)
- `FOOD` → Food procurement including hunting and animal skinning
- `UPGRADE` → If the AI already has a weapon or clothing in slot, should it be allowed to upgrade?
- `DEFAULT` → Same as WEAPONS_FIREARMS | WEAPONS_LAUNCHERS | WEAPONS_MELEE
- `ALL` → Same as WEAPONS | BANDAGES | CLOTHING | UPGRADE

---
### **`Speed`**
- **Type**: String
- **Description**: Maximum speed allowed for the AI when not in combat

**Valid Values:**
- `STATIC`
- `WALK`
- `JOG`
- `SPRINT`
- `RANDOM` → will give a result between STATIC and SPRINT
- `RANDOM_NONSTATIC` → will give a result between WALK and SPRINT

---
### **`UnderThreatSpeed`**
- **Type**: String
- **Description**: Maximum speed allowed for the AI when in combat

**Valid Values:**
- `STATIC`
- `WALK`
- `JOG`
- `SPRINT`
- `RANDOM` → will give a result between STATIC and SPRINT
- `RANDOM_NONSTATIC` → will give a result between WALK and SPRINT

---
### **`DefaultStance`**
- **Type**: String
- **Description**: Default stance the AI will take when not under fire and not melee fighting

**Valid Values:**
- `STANDING` (default)
- `CROUCHED`
- `PRONE`

---
### **`DefaultLookAngle`**
- **Type**: Float
- **Description**: Default horizontal look angle in degrees when not looking at a target and not moving. `0.0` = off/not used, `90` = west, `-90` = east `+-180` = south, any value in between is possible

---

### **`CanBeLooted`**
- **Type**: Boolean
- **Description**: If set to 1, AI can be looted once dead. If set to 0, they cannot be looted

---

### **`LootDropOnDeath`**
- **Type**: String
- **Description**: If set to a JSON filename in `<serverprofile>\ExpansionMod\AI\LootDrops`, will spawn this loot when AI dies. You can look at the Example.json that is automatically generated to see how the file contents need to be laid out (format is similar to loadouts)

---

### **`UnlimitedReload`**
- **Type**: Integer (Bitmask)
- **Description**: If set to any non-zero value (see below), AI will be able to reload infinitely if they have a spare mag or ammo in their inventory (mags will refill automagically)

**Valid Values:**
- `0` → Off
- `1` → All targets
- `2` → Animals
- `4` → Infected
- `8` → Players
- `16` → Vehicles

**Note**: Values other than 1 can be added together to combine them. E.g. a value of 6 means only allow unlimited reload if current AI target is an animal or Infected.

---

### **`SniperProneDistanceThreshold`**
- **Type**: Float
- **Description**: Minimum distance in meters before an AI holding a bolt action rifle will go prone to engage a target. If the target is closer, AI won't go prone. Setting to 0 disables prone completely

---

### **`AccuracyMin`**
- **Type**: Float
- **Description**: Minimum accuracy of this patrol (0.0-1.0)
- **Default**: If set to `-1` will use the AccuracyMin setting used on the top of the config file

---
### **`AccuracyMax`**
- **Type**: Float
- **Description**: Maximum accuracy of this patrol (0.0-1.0)
- **Default**: If set to `-1` will use the AccuracyMax setting used on the top of the config file

---
### **`ThreatDistanceLimit`**
- **Type**: Float
- **Description**: Distance in meters when the target will start be considered a potential threat
- **Default**: If set to `-1` will use the setting used on the top of the config file

---
### **`NoiseInvestigationDistanceLimit`**
- **Type**: Float
- **Description**: Max distance in meters that AI will search for noise sources
- **Default**: `-1` = use value from top of AIPatrolSettings.json (fall back to AISettings.json if also -1)

---

### **`MaxFlankingDistance`**
- **Type**: Float
- **Description**: Max distance to enemy in meters that AI will try to flank the enemy (default 200)
- **Default**: `-1` = use value from top of AIPatrolSettings.json (fall back to AISettings.json if also -1)

---

### **`EnableFlankingOutsideCombat`**
- **Type**: Integer
- **Description**: Enable flanking outside combat. Note that this will give AI a sort of "sixth sense" about enemies, but not necessarily their exact position when there is no line of sight
- **Valid Values**:
  - `0` = Disabled
  - `1` = Enabled
  - `-1` = Use value from top of AIPatrolSettings.json (fall back to AISettings.json if also -1)

---

### **`DamageMultiplier`**
- **Type**: Float
- **Description**: Damage multiplier for damage dealt by the AI (default 1.0 = no change). Base damage they deal will be multiplied by this value
- **Default**: If set to `-1` will use the setting used on the top of the config file

---
### **`DamageReceivedMultiplier`**
- **Type**: Float
- **Description**: Damage multiplier for damage the AI receive (default 1.0 = no change). Base damage they receive will be multiplied by this value
- **Default**: If set to `-1` will use the setting used on the top of the config file

---
### **`HeadshotResistance`**
- **Type**: Float
- **Description**: Default 0.0 = no change. Any value above 0 will disable the brain damage zone (disables instakill when brain is hit). 1.0 = AI will not receive damage from headshots

---

### **`CanBeTriggeredByAI`**
- **Type**: Boolean
- **Description**: Whether or not this patrol can be triggered by other AI or only actual players

---

### **`MinDistRadius`**
- **Type**: Float
- **Description**: The required minimum distance from a player to spawn. If a player is closer than MinDistRadius meters, then the patrol won't spawn
- **Default**: If set to `-1` will use the MinDistRadius setting used on the top of the config file

---
### **`MaxDistRadius`**
- **Type**: Float
- **Description**: The required maximum distance from a player to spawn. If a player is further away than MaxDistRadius meters, then the patrol won't spawn
- **Default**: If set to `-1` will use the MinDistRadius setting used on the top of the config file

---
### **`DespawnRadius`**
- **Type**: Float
- **Description**: The required distance from a player to despawn. If a player is closer than DespawnRadius meters, then the patrol won't despawn
- **Default**: If set to `-1` will use the DespawnRadius setting used on the top of the config file

---
### **`MinSpreadRadius`** / **`MaxSpreadRadius`**
- **Type**: Float
- **Description**: This setting allows you to make each of your waypoints randomized in a radius defined by min/max spread. If you want your waypoints to be accurate, keep this setting at 0

---

### **`Chance`**
- **Type**: Float
- **Description**: Spawn chance for this patrol as a value between 0.0 (0%) and 1.0 (100%)

---

### **`DespawnTime`**
- **Type**: Float
- **Description**: How long will it take for the patrol to despawn if no players are in MaxDistRadius
- **Default**: If set to `-1` will use the DespawnTime setting used on the top of the config file

---
### **`RespawnTime`**
- **Type**: Float
- **Description**: How long until this patrol can respawn?
- **Valid Values**:
  - `-1` = They won't respawn
  - `-2` = Will use the RespawnTime setting used on the top of the config file

---
### **`LoadBalancingCategory`**
- **Type**: String
- **Description**: This allows you to assign a category for load balancing, to determine how many patrols of this type can be active depending on player count, with great amount of customizability. See AI Load Balancing

---

### **`ObjectClassName`**
- **Type**: String
- **Description**: A classname of a building you want AI to spawn on (e.g. heli or police wrecks, police stations, etc)

**Note**: Will ignore Waypoints if set.

By default, only objects inheriting from BuildingBase/House are supported, but if you use DayZ-Expansion-Missions, then also the individual airdrop container classnames can be used.

Other objects can be supported by modding (the object type needs to be registered using eAIRegisterDynamicPatrolSpawner and have a eAIDynamicPatrolSpawner instance assigned. How this needs to be initialized depends on the type of object, see BuildingBase.c in DayZ-Expansion-Scripts and ExpansionAirdropContainerBase.c in DayZ-Expansion-Scripts as examples)

---

### **`WaypointInterpolation`**
- **Type**: String
- **Description**: If any interpolation should be used on the given waypoints to smooth out the path at turns
- **Valid Values**: `CatmullRom`, `NaturalCubic`, `UniformCubic` or empty string (no interpolation)

**Note**: To illustrate the difference using four waypoints arranged in a zig-zag pattern, look at the following image (image is more exaggerated than the result you will get, as we have an angle threshold of 5 degrees and a distance threshold of 4.5 meters to limit the number of generated points):

Curve interpolation

---

### **`UseRandomWaypointAsStartPoint`**
- **Type**: Boolean
- **Description**: If set to 1, use a random waypoint as spawn point (else use the 1st waypoint)

**Note**: Only used if ObjectClassName is empty.

---

### **`Waypoints`**
- **Type**: Array
- **Description**: A list of positions the patrols will have to go to

**Note**: Only used if ObjectClassName is empty.
