# Treasure Hunt Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 6,
    "ObjectiveText": "Find the location of the treasure",
    "TimeLimit": -1,
    "Active": 1,
    "ShowDistance": 1,
    "ContainerName": "ExpansionQuestSeaChest",
    "DigInStash": 1,
    "MarkerName": "???",
    "MarkerVisibility": 4,
    "Positions": [
        [
            2936.47998046875,
            350.6139831542969,
            6369.39013671875
        ],
        [
            3143.35009765625,
            365.7760009765625,
            6942.0400390625
        ],
        [
            5233.509765625,
            290.8810119628906,
            6246.3701171875
        ]
    ],
    "Loot": [
        {
            "Name": "AKM",
            "Attachments": [
                "AK_WoodBttstck",
                "AK_WoodHndgrd",
                "Mag_AKM_30Rnd"
            ],
            "Chance": 1.0,
            "QuantityPercent": -2,
            "Max": 1,
            "Min": 0,
            "Variants": []
        },
        {
            "Name": "Mag_AKM_30Rnd",
            "Attachments": [],
            "Chance": 1.0,
            "QuantityPercent": -2,
            "Max": 2,
            "Min": 2,
            "Variants": []
        }
    ],
    "LootItemsAmount": 3,
    "MaxDistance": 10.0
}
```

---

## Objective Parameters

### **`ShowDistance`**
- **Type**: Boolean
- **Description**: Controls whether the distance to the objective position will be displayed in the quest HUD

---

### **`ContainerName`**
- **Type**: String
- **Description**: Container entity class name that will be used for this objective. The entity class always needs to inherit from "ExpansionQuestContainerBase"

---

### **`DigInStash`**
- **Type**: Boolean
- **Description**: Controls if the container will be dug into an underground stash or not

---

### **`MarkerName`**
- **Type**: String
- **Description**: Text for the objective quest marker. Leave empty to create no marker

---

### **`MarkerVisibility`**
- **Type**: Integer
- **Description**: Defines the visibility of the objective quest marker
- **Values**:
  - `4` = visible on map
  - `2` = visible in world
  - `6` = visible on map and in world

---

### **`Positions`**
- **Type**: Array[Vector]
- **Description**: A random position from this array will be selected when the quest with this objective is started and set as the stash and objective position

---

### **`Loot`**
- **Type**: Array[ExpansionLoot]
- **Description**: Loot reward items that will get spawned/attached into/on the stash

---

### **`LootItemsAmount`**
- **Type**: Integer
- **Description**: Number of loot items to spawn in the treasure

---

### **`MaxDistance`**
- **Type**: Float
- **Description**: Maximum distance from the treasure position to complete the objective

**Note**: If a quest player is within a given range of the objective position the stash will be created and spawned
