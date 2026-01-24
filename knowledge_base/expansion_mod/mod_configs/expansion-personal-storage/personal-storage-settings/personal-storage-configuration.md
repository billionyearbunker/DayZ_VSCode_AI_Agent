# Personal Storage Configuration

---

## Overview

You can name a personal storage configuration file to whatever you want as long as it has the `.json` file extension and is placed in the `mpmissions\MISSIONNAME.MAPNAME\storage_x\expansion\personalstorage` folder - it will get loaded by the personal storage system.

---

## Configuration Parameters

### **`ConfigVersion`**
- **Type**: Integer
- **Description**: Current config file version. NEVER CHANGE THIS UNLESS YOU KNOW WHAT YOU ARE DOING!

---

### **`StorageID`**
- **Type**: Integer
- **Description**: Unique storage ID for this personal storage. Never use the same ID twice!

---

### **`ClassName`**
- **Type**: String
- **Description**: Class name of the object that will be used to spawn the personal storage object
- **Requirement**: Need to inherit from `ExpansionPersonalStorageBase`

---

### **`DisplayName`**
- **Type**: String
- **Description**: Display name that will be used in the personal storage menu or when the name-tags mod loaded and enabled next to the personal storage mod

---

### **`DisplayIcon`**
- **Type**: String
- **Description**: Display icon that will be used in the personal storage menu or when the name-tags mod loaded and enabled next to the personal storage mod. Can be a ExpansionIcon or any valid image path

---

### **`Position`**
- **Type**: Vector
- **Description**: World position where the personal storage object will be created at

---

### **`m_Orientation`**
- **Type**: Vector
- **Description**: World orientation where the personal storage object will be facing at

---

### **`QuestID`**
- **Type**: Integer
- **Description**: If the player needs to unlock this storage by completing a certain expansion quest mod quest then add the quest ID here

---

### **`Reputation`**
- **Type**: Integer
- **Description**: If the player needs to have a certain reputation to use this storage add the min. value here

---

### **`Faction`**
- **Type**: String
- **Description**: If the player needs to be a member of a certain faction add the faction name here

---

### **`IsGlobalStorage`**
- **Type**: Boolean
- **Description**: If this storage should display all items from the player he deposited in any storage in the world then set this to 1

---

## Example Configuration JSON

```json
{
    "ConfigVersion": 2,
    "StorageID": 0,
    "ClassName": "ExpansionPersonalStorageChest",
    "DisplayName": "Jalovisco - Personal Storage",
    "DisplayIcon": "Backpack",
    "Position": [
        8619.3095703125,
        14.788700103759766,
        10518.400390625
    ],
    "Orientation": [
        -54.31999969482422,
        0.0,
        0.0
    ],
    "QuestID": -1,
    "Reputation": 0,
    "Faction": "Survivors",
    "IsGlobalStorage": 1
}
