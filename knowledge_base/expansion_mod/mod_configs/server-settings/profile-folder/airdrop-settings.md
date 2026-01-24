# AirdropSettings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`ServerMarkerOnDropLocation`**
- **Type**: Bool
- **Values**:
  - `0` = No marker will be created to show the exact location of the airdrop drop point
  - `1` = The server will create a marker on the map on the airdrop drop location (where the crate will land)

---

### **`Server3DMarkerOnDropLocation`**
- **Type**: Bool
- **Note**: If `ServerMarkerOnDropLocation` is set to 0 you can ignore this setting
- **Values**:
  - `0` = The marker will not be displayed in 3D
  - `1` = The marker will be also in 3D

---

### **`ShowAirdropTypeOnMarker`**
- **Type**: Bool
- **Note**: If `ServerMarkerOnDropLocation` is set to 0 you can ignore this setting
- **Values**:
  - `0` = The marker name will not have the airdrop type in his name
  - `1` = The marker name will specify what type of airdrop it is (Military, Medical, Basebuilding for example)

---

### **`HeightIsRelativeToGroundLevel`**
- **Type**: Bool
- **Values**:
  - `0` = The plane will not try to adapt his altitude based on the elevation of the ground
  - `1` = The plane will try to adapt his altitude based on the elevation of the ground

---

### **`Height`**
- **Type**: Float
- **Description**: The altitude the plane will fly at

---

### **`FollowTerrainFraction`**
- **Type**: Float
- **Description**: From 0 to 1. How accurate the plane will follow the ground elevation (if HeightIsRelativeToGroundLevel is set to 1)

---

### **`Speed`**
- **Type**: Float
- **Description**: The speed of the plane in m/s. This will not change the speed of the crate falling

---

### **`Radius`**
- **Type**: Float
- **Description**: The radius in meters where the plane will drop the crate

---

### **`InfectedSpawnRadius`**
- **Type**: Float
- **Description**: The radius in meters where the enemy entities will spawn around the crate once landed

---

### **`InfectedSpawnInterval`**
- **Type**: Float
- **Description**: Time in ms between each enemy entity spawn (used to stagger the spawn)

---

### **`ItemCount`**
- **Type**: Float
- **Description**: The amount of items the dropped crate will have. This is a general setting in case if the crate itself doesnt have a configured ItemCount or is set to -1 (set to use this setting instead)

**ItemCount has two modes**:
- The number is positive (25 for example), the crate will have exactly 25 items in it
- The number is negative (-25 for example), the crate will have between 1 and 25 in it

---

### **`Containers`**
- **Type**: Array
- **Description**: A list of airdrop containers with their loot and types of enemy entities

---

### **`Containers` -> `Container`**
- **Type**: String
- **Description**: The classname of the container

**We are currently providing 12 different containers skins**:
- ExpansionAirdropContainer
- ExpansionAirdropContainer_Grey
- ExpansionAirdropContainer_Blue
- ExpansionAirdropContainer_Olive
- ExpansionAirdropContainer_Medical
- ExpansionAirdropContainer_Military
- ExpansionAirdropContainer_Military_GreenCamo
- ExpansionAirdropContainer_Military_MarineCamo
- ExpansionAirdropContainer_Military_OliveCamo
- ExpansionAirdropContainer_Military_OliveCamo2
- ExpansionAirdropContainer_Military_WinterCamo
- ExpansionAirdropContainer_Basebuilding

---

### **`Containers` -> `Usage`**
- **Type**: Integer
- **Values**:
  - `0` = missions & player called (can be spawned in RANDOM airdrops and by players)
  - `1` = only missions (can only be spawned in RANDOM airdrops)
  - `2` = only player called

---

### **`Containers` -> `Weight`**
- **Type**: Float
- **Description**: How likely this container will be spawned

---

### **`Containers` -> `Loot`**
- **Type**: Array
- **Description**: A list of items that can spawn in this crate

**Sub-Parameters**:
- **Name**: You have to give the exact Classname of the item
- **Attachments**: His attachements if you want it to spawn with items attached to it
- **Chance**: The chance of spawning (1.00 = 100% and 0.00 = 0%)
- **QuantityPercent**: 
  - 0 to 100 will be the quantity of this item in percent. ( My desired quantity / Max quantity of the item ) * 100 = My Percentage
  - -1 will be it's default value (100%)
  - -2 will use the quantmin and quandmax from your types.xml and any values between 0 and 100 will be the quantity in percentage
- **Max**: The maximum amount of time this item is allowed to be spawned in the container. -1 will skip this condition
- **Variants**: Variants of the items. It could be different colors of the same item, or different attachments for the same gun

**Example**:
```json
"Loot": [
    {
        "Name": "FirstAidKit",
        "Attachments": [
            "BandageDressing"
        ],
        "Chance": 0.38,
        "QuantityPercent": -1,
        "Max": -1,
        "Variants": [
            {
                "Name": "FirstAidKit",
                "Attachments": [
                    "BandageDressing",
                    "SalineBagIV"
                ],
                "Chance": 0.13
            },
            {
                "Name": "FirstAidKit",
                "Attachments": [],
                "Chance": 0.13
            }
        ]
    },
],
"Containers" -> "Infected"
Array. A list of enemy entity classnames (any valid class will do, can be actual Infected, animals, and even AI if you are using the DayZ-Expansion-AI mod).

To spawn AI when using the DayZ-Expansion-AI mod, specify each string like this (example):

"eAI_SurvivorM_Mirek|faction:Mercenaries,loadout:BanditLoadout"

"eAI_SurvivorM_Mirek|faction:Mercenaries,loadout:BanditLoadout,canbelooted:false,name:JenkinsLeeroy"

For more informations, you can read more at https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-Expansion-AI

"Containers" -> "ItemCount"
Integer. How many items can spawn in this container. You can also set it to -1 to use the ItemCount from the top of the airdropsettings file.

ItemCount has two modes:

the number is positive (25 for example), the crate will have exactly 25 items in it
the number is negative (-25 for example), the crate will have between 1 and 25 in it
"Containers" -> "InfectedCount"
Integer. How many enemy entities can spawn at this container

"Containers" -> "SpawnInfectedForPlayerCalledDrops"
Boolean.

0 = Enemy entities won't spawn if it's a player called airdrop
1 = Enemy entities will also spawn if it's a player called airdrop
Please make sure the last } of the loot list doesn't have the , in }, like in the example !
