# SpawnSettings

**Note**: Unlike most other settings that may not be map-specific, you can find the SpawnSettings.json in your `mpmission\dayzOffline.<mapname>\expansion\settings` folder.

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

## Starting Clothing

### **`EnableCustomClothing`**
- **Type**: Bool
- **Values**:
  - `0` = The player will spawn with the vanilla default clothing items attached to his character
  - `1` = The player will spawn with the configured clothing items in this file

---

### **`SetRandomHealth`**
- **Type**: Bool
- **Values**:
  - `0` = All the clothing items with that the player spawns are in a pristine condition
  - `1` = All the clothing items with that the player spawns are in a random condition

---

### **`Headgear`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be headgear attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Glasses`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be eyewear attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Masks`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to masks attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Tops`**
- **Type**: Array
- **Description**: List of class names used for custom clothing. Need to be top/shirts/jackets attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Vests`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be vests attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Gloves`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be gloves attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Pants`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be pants/shorts attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Belts`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be belt attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Shoes`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be shoes attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Armbands`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be armbands attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

### **`Backpacks`**
- **Type**: Array
- **Description**: List of class names used for the custom clothing. Need to be backpacks attachments/items! If the array only contains one item class name it the characters will always spawn with this item when `UseCustomClothing` is enabled otherwise, the item will be selected randomly.

---

## Spawn Selection

### **`EnableSpawnSelection`**
- **Type**: Bool
- **Values**:
  - `0` = Players will spawn randomly on the map like in vanilla
  - `1` = Players will be able to choose where to spawn on the map according the config done bellow

---

### **`SpawnOnTerritory`**
- **Type**: Bool
- **Values**:
  - `0` = Players can't respawn at their territories
  - `1` = You can respawn at your territory

---

### **`SpawnLocations`**
- **Type**: Array
- **Description**: List of spawn locations that will get displayed in the spawn selection menu of the player

#### **`Name`**
- **Type**: String
- **Description**: The name of the location

#### **`Positions`**
- **Type**: Array
- **Description**: List of positions

**Example**:
```json
{
    "Name": "My Location Name",
    "Positions": [
        [
            100,         // Potential spawn position 1
            2,           // If only one position is set, the player will always spawn at this position
            50           // Also, the first spawn position will be used to create the 2d marker on the map
        ],
        [
            250,         // Potential spawn position 2
            2.75,
            100
        ]
    ],
    "UseCooldown": 0     // Bool. Gives this position a cooldown if enabled and when the "EnableRespawnCooldowns" setting is enabled too.
}
```

---

## Starting Gear

### **`EnableStartingGear`**
- **Type**: Bool
- **Values**:
  - `0` = The player will spawn with the vanilla default gear
  - `1` = The player will spawn with the configured gear in this file

---

### **`UseUpperGear`**
- **Type**: Bool
- **Values**:
  - `0` = The "UpperGear" will not be used. Nothing from this list will spawn on the player character
  - `1` = The items from "UpperGear" will be added into the inventory of the player in his Upper inventory (shirt inventory)

---

### **`UsePantsGear`**
- **Type**: Bool
- **Values**:
  - `0` = The "PantsGear" will not be used. Nothing from this list will spawn on the player character
  - `1` = The items from "PantsGear" will be added into the inventory of the player in his Pant inventory

---

### **`UseBackpackGear`**
- **Type**: Bool
- **Values**:
  - `0` = The "BackpackGear" will not be used. Nothing from this list will spawn on the player character
  - `1` = The items from "BackpackGear" will be added into the inventory of the player in his backpack inventory

---

### **`UseVestGear`**
- **Type**: Bool
- **Values**:
  - `0` = The "VestGear" will not be used. Nothing from this list will spawn on the player character
  - `1` = The items from "VestGear" will be added into the inventory of the player in his vest inventory

---

### **`UsePrimaryWeapon`**
- **Type**: Bool
- **Values**:
  - `0` = The "PrimaryWeapon" will not be used. Player will not spawn with a primary weapon
  - `1` = The item defined at "PrimaryWeapon" will be added into the inventory of the player in his primary weapon slot

---

### **`UseSecondaryWeapon`**
- **Type**: Bool
- **Values**:
  - `0` = The "SecondaryWeapon" will not be used. Player will not spawn with a secondary weapon
  - `1` = The item defined at "SecondaryWeapon" will be added into the inventory of the player in his secondary weapon slot

---

### **`UpperGear`**
- **Type**: Array
- **Description**: List of Items used for the upper gear

**Example**:
```json
{
    "ClassName": "Rag",
    "Quantity": 4,
    "Attachments": []
},
{
    "ClassName": "FNX45",
    "Quantity": 1,
    "Attachments": [
        "Mag_FNX45_15Rnd",
        "PistolSuppressor"
    ]
}
```

---

### **`PantsGear`**
- **Type**: Array
- **Description**: List of Items used for the pants gear

---

### **`BackpackGear`**
- **Type**: Array
- **Description**: List of Items used for the backpack gear

---

### **`VestGear`**
- **Type**: Array
- **Description**: List of Items used for the vest gear

---

### **`PrimaryWeapon`**
- **Type**: Array
- **Description**: Item that gets attached to the player's primary weapon slot. Need to be a Fire- or Meele Weapon like an Axe

---

### **`SecondaryWeapon`**
- **Type**: Array
- **Description**: Item that gets attached to the player's secondary weapon slot. Need to be a Fire- or Meele Weapon like an Axe

---

### **`ApplyEnergySources`**
- **Type**: Bool
- **Values**:
  - `0` = Nothing happens here
  - `1` = All gear items with that the player character spawned get a V9 batterie when they can fit and need one

---

### **`SetRandomHealth`**
- **Type**: Bool
- **Values**:
  - `0` = All the gear items with that the player spawns are in a pristine condition
  - `1` = All the gear items with that the player character spawned are in a random condition

---

## Loadouts

### **`UseLoadouts`**
- **Type**: Bool
- **Values**:
  - `0` = When respawning, the system wont use loadouts
  - `1` = When respawning, the loadouts will be used. You can combine the starting gear and starting clothing with loadouts if you want. You could use loadouts to pick a random outfit set and use the above settings to give the generic items you want players to always have for example

---

### **`MaleLoadouts`**
- **Type**: Array
- **Description**: List of loadouts and chance to be picked
- **Properties**:
  - Loadout Name
  - Chance from 0.0 to 1.0

---

### **`FemaleLoadouts`**
- **Type**: Array
- **Description**: List of loadouts and chance to be picked
- **Properties**:
  - Loadout Name
  - Chance from 0.0 to 1.0

---

## Spawn Stats

### **`SpawnHealthValue`**
- **Type**: Float
- **Description**: How much Health (not the blood icon) the player will spawn with

---

### **`SpawnEnergyValue`**
- **Type**: Float
- **Description**: How much Energy (food) the player will spawn with

---

### **`SpawnWaterValue`**
- **Type**: Float
- **Description**: How much Water (thirst) the player will spawn with

---

## Respawn Cooldowns

### **`EnableRespawnCooldowns`**
- **Type**: Bool
- **Values**:
  - `0` = The Cooldown system will be disabled
  - `1` = Enable the cooldown system and adds a cooldown for the player for all spawn points within the "SpawnLocations" array which have the "UseCooldown" bolean enabled

---

### **`RespawnCooldown`**
- **Type**: Integer
- **Description**: Cooldown seconds. Once the player spawned on that spawn location, a cooldown of `RespawnCooldown` seconds will start and when the `UseCooldown` boolean is enabled for that spawn location in the "Positions" list

---

### **`RespawnUTCTime`**
- **Type**: Bool
- **Values**:
  - `0` = The Spawn Selection cooldowns will be calculated based on the server Local time
  - `1` = The Spawn Selection cooldowns will be calculated based on the UTC time

---

### **`PunishMultispawn`**
- **Type**: Bool
- **Values**:
  - `0` = This feature will be disabled
  - `1` = Punish the player with an additional cooldown time defined in the "PunishCooldown" setting when they use the same spawn location point multiple times

---

### **`PunishCooldown`**
- **Type**: Integer
- **Description**: Additional Cooldown in seconds if the spawn location has been used too many times by the player. This mean the player will have the time of `PunishCooldown` AND `RespawnCooldown` combined

---

### **`PunishTimeframe`**
- **Type**: Integer
- **Description**: Time in seconds. If the player try to respawn to the same spawn location too quickly the player will trigger the `PunishCooldown` if `PunishMultispawn` is enabled. This `PunishTimeframe` is the amount of time required between two respawns at the same location to not trigger this punishment

---

## Additional Features

### **`CreateDeathMarker`**
- **Type**: Bool
- **Values**:
  - `0` = This feature will be disabled
  - `1` = Create a marker on the players latest death location on the spawn selection menu map
