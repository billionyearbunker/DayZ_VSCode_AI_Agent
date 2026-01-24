# RaidSettings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`ExplosionTime`**
- **Type**: Integer
- **Description**: Time in seconds it takes for the ExpansionSatchel to explode

---

### **`ExplosiveDamageWhitelist`**
- **Type**: Array of string
- **Description**: Put every classname of the explosive items you want to be able to be used for raiding. The classnames are not the weapons items nor the explosives items but the explosion itself. For example you can disable rpg explosions with `Expansion_RPG_Explosion`

**Example**:
```json
"ExplosiveDamageWhitelist": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withoutCommaAtTheEndBecauseItsTheLastOne"
],
```

---

### **`EnableExplosiveWhitelist`**
- **Type**: Bool
- **Values**:
  - `0` = Every items from the game will be able to raid basebuilding elements regardless of ExplosiveDamageWhitelist
  - `1` = Only the items listed above will be able to raid basebuilding elements

---

### **`ExplosionDamageMultiplier`**
- **Type**: Float
- **Description**: It is a damage multiplier for all explosion type damages to Expansion base parts. For example with the default value of 50, a grenade that does 50 damage will do 50 * 50 damage to the wall, so 2500. For reference, vanilla grenades do 50 damage, Expansion rockets do 300, and C4 does 600. Less than 1 values work here as well, so 0x will disable damage to base parts, and .5x will halve them. Note, walls currently have an HP of 30,000

---

### **`ProjectileDamageMultiplier`**
- **Type**: Float
- **Description**: It is a damage multiplier for all bullet type damages to Expansion base parts. For example with the default value of 2, a bullet that does 65 damage will do 65 * 2 damage to the wall, so 130. Less than 1 values work here as well, so 0x will disable damage to base parts, and .5x will halve them. Note, walls currently have an HP of 30,000

---

### **`CanRaidSafes`**
- **Type**: Bool
- **Values**:
  - `0` = Players won't be able to destroy Expansion safes
  - `1` = Allow to players to raid expansion safes

---

### **`SafeExplosionDamageMultiplier`**
- **Type**: Float
- **Description**: It is a damage multiplier for all explosion type damages to Expansion base parts. For example with the default value of 50, a grenade that does 50 damage will do 50 * 50 damage to the safe, so 2500. For reference, vanilla grenades do 50 damage, Expansion rockets do 300, and C4 does 600. Less than 1 values work here as well, so 0x will disable damage to base parts, and .5x will halve them. Note, safes currently have 20,000 15,000 and 10,000 HP

---

### **`SafeProjectileDamageMultiplier`**
- **Type**: Float
- **Description**: It is a damage multiplier for all bullet type damages to Expansion base parts. For example with the default value of 2, a bullet that does 65 damage will do 65 * 2 damage to the safe, so 130. Less than 1 values work here as well, so 0x will disable damage to base parts, and .5x will halve them. Note, safes currently have 20,000 15,000 and 10,000 HP

---

### **`SafeRaidTools`**
- **Type**: Array
- **Description**: List of tools allowed for raiding safes

**Example**:
```json
"SafeRaidTools": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withoutCommaAtTheEndBecauseItsTheLastOne"
],
```

---

### **`SafeRaidToolTimeSeconds`**
- **Type**: Integer
- **Description**: Time needed to raid safe with tool

---

### **`SafeRaidToolCycles`**
- **Type**: Integer
- **Description**: Number of cycles needed to raid safe

---

### **`SafeRaidToolDamagePercent`**
- **Type**: Integer
- **Description**: Total damage dealt to tool over time (100 = tool will be in ruined state after all cycles finished)

---

### **`BarbedWireRaidTools`**
- **Type**: Array
- **Description**: List of tools allowed for raiding barbed wire

**Example**:
```json
"BarbedWireRaidTools": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withoutCommaAtTheEndBecauseItsTheLastOne"
],
```

---

### **`BarbedWireRaidToolTimeSeconds`**
- **Type**: Integer
- **Description**: Time needed to raid barbed wire with tool

---

### **`BarbedWireRaidToolCycles`**
- **Type**: Integer
- **Description**: Number of cycles needed to raid barbed wire

---

### **`BarbedWireRaidToolDamagePercent`**
- **Type**: Integer
- **Description**: Total damage dealt to tool over time (100 = tool will be in ruined state after all cycles finished)

---

### **`CanRaidLocksOnWalls`**
- **Type**: Integer
- **Values**:
  - `0` = You can't raid codelocks on tents
  - `1` = Make locks (both vanilla and Expansion) raidable on walls doors and gates
  - `2` = Make locks (both vanilla and Expansion) raidable on wall doors
  - `3` = Make locks (both vanilla and Expansion) raidable on wall gates

---

### **`CanRaidLocksOnFences`**
- **Type**: Bool
- **Values**:
  - `0` = You can't raid codelocks on fences
  - `1` = Make locks (both vanilla and Expansion) raidable on fences

---

### **`CanRaidLocksOnTents`**
- **Type**: Bool
- **Values**:
  - `0` = You can't raid codelocks on tents
  - `1` = Make locks (both vanilla and Expansion) raidable on tents

---

### **`LockRaidTools`**
- **Type**: Array
- **Description**: List of tools allowed for raiding locks

**Example**:
```json
"LockRaidTools": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withoutCommaAtTheEndBecauseItsTheLastOne"
],
```

---

### **`LockOnWallRaidToolTimeSeconds`**
- **Type**: Integer
- **Description**: Time needed to raid lock on wall with tool

"LockOnFenceRaidToolTimeSeconds"
Integer. Time needed to raid lock on fence with tool

"LockOnTentRaidToolTimeSeconds"
Integer. Time needed to raid lock on tent with tool

"LockRaidToolCycles"
Integer. Number of cycles needed to raid lock

"LockRaidToolDamagePercent"
Integer. Total damage dealt to tool over time (100 = tool will be in ruined state after all cycles finished)

"BaseBuildingRaidMode"
Integer.

-1 = Expansion BaseBuilding elements can't be raided.
0 = every basebuilding elements can be raided.
1 = only doors/gates.
2 = only doors/gates/windows.
