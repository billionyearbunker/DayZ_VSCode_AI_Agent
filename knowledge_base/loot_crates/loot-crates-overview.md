# CJ187 Loot Chests - Instruction Guide

**Mod Version:** 1.06  
**Authors:** CJ187 and Hunterz  
**Latest Changes:** 30th Nov. 2025

---

## Installation

Install the mod like any other mod and start the game with: `-mod=@CJ187-Lootchest...`

After first time, the server will create a Mod-Settings folder at:
```
DayZServer/profiles/
```

There you will find the `CJ_LootChests` folder with these files inside:
- `LootChests_LOG.log`
- `LootChests_V106.json`
- `LootChestsTools_V106.json`

---

## Configuration Explanations

### LootChest_V106.json

#### Global Settings

```json
"EnableDebug": 0
```
Toggle Logfiles (`0` = minimalized // `1` = detailed)

```json
"DeleteLogs": 0
```
Toggle automatic cleaning Logfiles after Restart (`0` = don't clean // `1` = clean)

```json
"MaxSpareMags": 3
```
Set how many Spare Magazines will be possible when predefined Weapon will be in LootChest (`0-999`)

```json
"RandomQuantity": 0
```
Toggle random filled items (`0` = off // `1` = on)  
This will affect all items that have quantity (food, drinks, loose ammo, magazines, bandages, loose nails, sewing kits, etc.)

---

### LootChestsLocations

This section contains all information about your Lootchests.

```json
"name": "Police_Station"
```
Name of the Event (you can name them as you want, but never use same name twice!)

```json
"number": 2
```
How many Lootchests you want to spawn in this Event

```json
"pos": [
    "10159.65 248.12 5535.25|73.00 0.00 0.00",
    "11171.11 297.69 7665.23|55.00 0.00 0.00",
    "13727.68 316.12 8927.63|75.00 0.00 0.00",
    "12926.83 10.55 10186.83|22.00 0.00 0.00"
]
```
All possible Positions with rotations are listed here.

**Important:** 
- Do not set less coordinates than your `"number"` of Lootchests!
- **PLEASE beware correct formatting in this section!!!**
- Format: `"X Y Z|Y P R"` without commas between the numbers!!!
- If you use more coordinates than your `"number"` of Lootchests, the Lootchests will spawn randomly at these coordinates!

```json
"keyclass": "CJ_Key1"
```
Matching Key to unlock this crate  
(If you want an unlocked Lootchest, use: `"keyclass": ""`)  
**Note:** Only Keys are allowed, do not enter other classnames!!!

```json
"openable": 0
```
Set how this Lootchest can be opened when it spawns locked:
- `0` = key only!
- `1` = Key and Lockpick only!
- `2` = Key, Lockpick and Tools

```json
"chest": [
    "CJ_LootChest_Grey_Small",
    "CJ_LootChest_Grey_Medium",
    "CJ_LootChest_Grey_Large"
]
```
List of possible crates that can spawn on this event.  
You can enter as many Lootchests as you like, the selection will be random for each one.

```json
"lootrandomize": 0.5
```
Set the Chance for each Item to NOT spawn in this Lootchest to increase randomization:

Examples:
- `0.5` = 50% chance for each Item to NOT be in the Lootchest
- `1.0` = 100% chance for each Item to NOT be in the Lootchest (Chest will be empty)
- `0.0` = 0% chance for each Item to NOT be in the Lootchest (all items will be in the Chest)

```json
"light": 0
```
Set lightsource inside the opened crate (`0` = no light / `1` = light)

```json
"loot": [
    "MP5k",
    "Mag_MP5_30Rnd",
    "AmmoBox_9x19_25rnd",
    "LC_Table_Weapons_Police",
    "LC_Table_Magazines_Police",
    "LC_Table_Ammo_Police",
    "LC_predefined_UMP"
]
```
List of possible loot inside the crates.  
You can use:
- **classnames** of items
- **LC_Tables** for more randomization
- **LC_predefined** Weapons

#### How Lootchests Spawn Items

The Lootchest will always take all Entries from the loot list, depending on the `"lootrandomize"` factor.

- If you add an **LC_Table** in this List, the Lootchest will ALWAYS pick ONE random item from this Table!
- If you want e.g. 5 Items from a specific **LC_Table**, you need to add it multiple times!
- **Recommendation:** Add large Items or Weapons in the top section of the list, because these need a lot of space!

---

### LCPredefinedWeapons

This section contains all information about your already assembled Weapon Presets.

```json
"defname": "LC_predefined_AKM"
```
Name of Weaponpreset.  
Can be custom but MUST begin with `"LC_predefined_"`

```json
"weapon": "AKM"
```
Classname of the weapon (Must be type Weapon! No Gear!)

```json
"magazine": "Mag_AKM_30Rnd"
```
Classname of magazine in weapon  
(Use `"magazine": ""` for no magazine, e.g. for Shotguns)

```json
"attachments": [
    "AK_FoldingButtstock",
    "AK_RailHndgrd",
    "UniversalLight",
    "AK_Suppressor"
]
```
Classnames of attachments on weapon (Only for WeaponAttachments, no Optics!)

```json
"optic": "PSO1Optic"
```
Classname of Optic on weapon  
(If you don't want to have an Optic, use `"optic": ""`)

```json
"opticbattery": 1
```
ONLY when your Weapon has an Optic!
- `0` = Weapon has no optic or no Battery in Optic!
- `1` = Battery inside optic

---

### LootCategories

This section contains all information about your random Loot Tables.

```json
"name": "LC_Table_Tools"
```
or
```json
"name": "LC_Table_Weapons_Police"
```

Tables for more randomization. You can create your custom Tables, they always MUST begin with:
- `LC_Table_` for all kinds of Items, clothing, tools, consumables
- `LC_Table_Weapons_` for all kinds of Firearms

**Important:**
- For all kind of Items, clothing, tools, consumables you MUST use `"LC_Table_"`
- Only for all kind of Firearms you MUST use `"LC_Table_Weapons_"`

```json
"Loot": [
    "AKM",
    "LC_predefined_AK74",
    "LC_predefined_AK101"
]
```
Loot and Presets in this Table  
(Choose classnames of items or weapon-presets for custom mounted weapons)

Each time a Table is added in Lootchest, it will pick ONE random Item out of it!

---

## LootChestsTools_V106.json

The `"LCTools"` section contains all information how the Keys and Tools are working.

**Important!**  
Do not remove any of the Tools or Keys from the Default config!!!  
You cannot add other Tools without LootChest-Compatibility!

```json
"name": "SledgeHammer"
```
Classname of the tool (only Sledgehammer, Crowbar and Lockpick are supported!)

```json
"time": 1
```
How long in seconds it takes to unlock the LootChest.  
Only Tools are supported! Keys always need 3 seconds!  
(`-1` deactivates this option for all LootChests!)

```json
"dmg": 33
```
How much damage in % the tool takes when you unlocked a Lootchest.  
(If you want a Tool or Key be usable only once, set `"dmg": 100`)

```json
"desc": "NAME of KEY|DESCRIPTION of KEY"
```
Here you can change Name and Description of the Keys only!

**Important:**  
You MUST use this type of entry: `"name|description"`

Example:
```json
"Red Key|This key will open a crate hidden somewhere at the military airfield."
```
So you can customize the Keys to give players hints.

---

## Advanced Tips & Tricks

### Example 1: Variable Chest Count

You don't want to have each Restart the same amount of Lootchests?

**Scenario:** You have a Building with 5 possible Locations and want 1-3 Lootchests.

**Solution:**  
Add 2 more Locations far outside the Map border, e.g.:
```json
"-10000 0 -10000|0 0 0"
```
So 2 Chests will have the chance not to spawn inside the Building.  
The Players can't be 100% sure to find all Chests every time.

### Example 2: Weighted Random Tables

You want a Table with one very rare item in it and a very low chance to get this item?

**Scenario:** You want to have a Food-Chest with 90% apples and 10% Rice.

**Solution:**  
Easy! Add in the Table the Apple 9 times and the Rice only once.

---

## Classnames Reference for types.xml

### Chest Classnames

#### Standard Metal Chests (7x7, 10x10, 10x15 slots)

**Brown:**
- `CJ_LootChest_Brown_Small` - Small (7x7 slots)
- `CJ_LootChest_Brown_Medium` - Medium (10x10 slots)
- `CJ_LootChest_Brown_Large` - Large (10x15 slots)

**Green:**
- `CJ_LootChest_Green_Small` - Small (7x7 slots)
- `CJ_LootChest_Green_Medium` - Medium (10x10 slots)
- `CJ_LootChest_Green_Large` - Large (10x15 slots)

**Grey:**
- `CJ_LootChest_Grey_Small` - Small (7x7 slots)
- `CJ_LootChest_Grey_Medium` - Medium (10x10 slots)
- `CJ_LootChest_Grey_Large` - Large (10x15 slots)

**Olive:**
- `CJ_LootChest_Olive_Small` - Small (7x7 slots)
- `CJ_LootChest_Olive_Medium` - Medium (10x10 slots)
- `CJ_LootChest_Olive_Large` - Large (10x15 slots)

**Tan:**
- `CJ_LootChest_Tan_Small` - Small (7x7 slots)
- `CJ_LootChest_Tan_Medium` - Medium (10x10 slots)
- `CJ_LootChest_Tan_Large` - Large (10x15 slots)

**Camo:**
- `CJ_LootChest_Camo_Small` - Small (7x7 slots)
- `CJ_LootChest_Camo_Medium` - Medium (10x10 slots)
- `CJ_LootChest_Camo_Large` - Large (10x15 slots)

#### Wooden Chests (10x10, 10x15, 10x20 slots)

**Wood Brown (Plain):**
- `CJ_LootChest_Wood_Brown_Small` - Small (10x10 slots)
- `CJ_LootChest_Wood_Brown_Medium` - Medium (10x15 slots)
- `CJ_LootChest_Wood_Brown_Large` - Large (10x20 slots)

**Wood Green (Plain):**
- `CJ_LootChest_Wood_Green_Small` - Small (10x10 slots)
- `CJ_LootChest_Wood_Green_Medium` - Medium (10x15 slots)
- `CJ_LootChest_Wood_Green_Large` - Large (10x20 slots)

**Wood Brown (Themed):**
- `CJ_LootChest_Wood_Brown_Tools_Small` - Tools (Small)
- `CJ_LootChest_Wood_Brown_Foods_Small` - Foods (Small)
- `CJ_LootChest_Wood_Brown_Medics_Small` - Medics (Small)
- `CJ_LootChest_Wood_Brown_Tools_Medium` - Tools (Medium)
- `CJ_LootChest_Wood_Brown_Foods_Medium` - Foods (Medium)
- `CJ_LootChest_Wood_Brown_Medics_Medium` - Medics (Medium)
- `CJ_LootChest_Wood_Brown_Tools_Large` - Tools (Large)
- `CJ_LootChest_Wood_Brown_Foods_Large` - Foods (Large)
- `CJ_LootChest_Wood_Brown_Medics_Large` - Medics (Large)

**Wood Green (Themed):**
- `CJ_LootChest_Wood_Green_Tools_Small` - Tools (Small)
- `CJ_LootChest_Wood_Green_Foods_Small` - Foods (Small)
- `CJ_LootChest_Wood_Green_Medics_Small` - Medics (Small)
- `CJ_LootChest_Wood_Green_Tools_Medium` - Tools (Medium)
- `CJ_LootChest_Wood_Green_Foods_Medium` - Foods (Medium)
- `CJ_LootChest_Wood_Green_Medics_Medium` - Medics (Medium)
- `CJ_LootChest_Wood_Green_Tools_Large` - Tools (Large)
- `CJ_LootChest_Wood_Green_Foods_Large` - Foods (Large)
- `CJ_LootChest_Wood_Green_Medics_Large` - Medics (Large)

#### Ammo Boxes

**Small Ammo Boxes (5x8 slots):**
- `CJ_LootChest_Ammo_Small_Brown`
- `CJ_LootChest_Ammo_Small_Green`

**Large Ammo Boxes (10x8 slots):**
- `CJ_LootChest_Ammo_Large_Brown`
- `CJ_LootChest_Ammo_Large_Green`

#### Money Safes (8x8 slots)

- `CJ_LootChest_MoneySafe_Old`
- `CJ_LootChest_MoneySafe_New`
- `CJ_LootChest_MoneySafe_New_Card`
- `CJ_LootChest_MoneySafe_New_Card_L1`
- `CJ_LootChest_MoneySafe_New_Card_L2`
- `CJ_LootChest_MoneySafe_New_Card_L3`
- `CJ_LootChest_MoneySafe_New_Card_L4`

#### Cash Registers (5x4 slots)

- `CJ_LootChest_CashRegister_Old`
- `CJ_LootChest_CashRegister_New`

#### Hidden Stashes

- `CJ_LootChest_HiddenStash_Small` - Small (6x6 slots)
- `CJ_LootChest_HiddenStash_Medium` - Medium (8x8 slots)
- `CJ_LootChest_HiddenStash_Large` - Large (10x10 slots)

---

### Key Classnames

#### Standard Keys (Colored)

- `CJ_Key1` - Black
- `CJ_Key2` - Grey
- `CJ_Key3` - Brown
- `CJ_Key4` - Green
- `CJ_Key5` - Olive
- `CJ_Key6` - Yellow
- `CJ_Key7` - Red
- `CJ_Key8` - Blue

#### Old Keys

- `CJ_Key9` - Old key
- `CJ_Key10` - Old key
- `CJ_Key11` - Old key
- `CJ_Key12` - Old key

#### Special Keys

- `CJ_Key101` - Small key
- `CJ_Key102` - Key with plastic
- `CJ_Key103` - Rusty key

#### Keycards

- `CJ_Key200` - Keycard (black)
- `CJ_Key201` - Keycard level 1 (blue)
- `CJ_Key202` - Keycard level 2 (green)
- `CJ_Key203` - Keycard level 3 (yellow)
- `CJ_Key204` - Keycard level 4 (red)