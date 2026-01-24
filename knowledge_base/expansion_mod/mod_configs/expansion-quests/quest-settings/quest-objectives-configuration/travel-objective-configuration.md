# Travel Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 3,
    "ObjectiveText": "Get to the Village",
    "TimeLimit": -1,
    "Active": 1,
    "Position": [
        4333.3701171875,
        311.77899169921877,
        6299.8798828125
    ],
    "MaxDistance": 20.0,
    "MarkerName": "Get to the Village",
    "ShowDistance": 1,
    "TriggerOnEnter": 1,
    "TriggerOnExit": 0
}
```

---

## Objective Parameters

### **`Position`**
- **Type**: Vector
- **Description**: Objective positions where the quest players need to travel to

---

### **`MaxDistance`**
- **Type**: Float
- **Description**: If a quest player is within the given range to the objective position the objective will get triggered as completed

---

### **`MarkerName`**
- **Type**: String
- **Description**: Text for the objective quest marker. Leave empty to create no marker

---

### **`ShowDistance`**
- **Type**: Boolean
- **Description**: Controls whether the distance to the objective position will be displayed in the quest HUD

---

### **`TriggerOnEnter`**
- **Type**: Bolean
- **Description**: Controls if the distance check will trigger when entering the defined objective area. Should always be enabled as this objective type will not be complete otherwise!

---

### **`TriggerOnExit`**
- **Type**: Boolean
- **Description**: Controls if the distance check will trigger and set the objective to incomplete when leaving the defined objective area
