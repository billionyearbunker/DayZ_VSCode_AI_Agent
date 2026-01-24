# AI VIP Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 9,
    "ObjectiveText": "Bring the VIP to the marked location.",
    "TimeLimit": 180,
    "Active": 1,
    "Position": [
        3193.590087890625,
        296.7070007324219,
        6090.56982421875
    ],
    "MaxDistance": 20.0,
    "MarkerName": "Escort VIP",
    "ShowDistance": 1,
    "CanLootAI": 0,
    "NPCLoadoutFile": "BanditLoadout",
    "NPCClassName": "",
    "NPCName": "Survivor"
}
```

---

## Objective Parameters

### **`Position`**
- **Type**: Vector
- **Description**: Objective position to where the VIP AI needs to be escorted

---

### **`MaxDistance`**
- **Type**: Float
- **Description**: If the escorted AI is within the given range from the objective position the objective will be triggered as completed

---

### **`MarkerName`**
- **Type**: String
- **Description**: Text for the objective quest marker. Leave empty to create no marker

---

### **`ShowDistance`**
- **Type**: Boolean
- **Description**: Controls whether the distance to the objective position will be displayed in the quest HUD

---

### **`CanLootAI`**
- **Type**: Boolean
- **Description**: Controls if spawned AI can be looted or not

---

### **`NPCLoadoutFile`**
- **Type**: String
- **Description**: NPC loadout file. Same as for AI patrol settings

---

### **`NPCClassName`**
- **Type**: String
- **Description**: NPC class name of the eAI entity that should be used to spawn in the VIP NPC. Leave the field empty to get a random AI unit

---

### **`NPCName`**
- **Type**: String
- **Description**: Name of the AI units that will be displayed in all name tags and tooltips for the spawned AI unit
