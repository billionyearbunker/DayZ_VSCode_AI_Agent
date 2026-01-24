# Delivery Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 5,
    "ObjectiveText": "Deliver the note to Steve",
    "TimeLimit": -1,
    "Active": 1,
    "Collections": [
        {
            "Amount": 1,
            "ClassName": "ExpansionQuestItemPaper",
            "QuantityPercent": -1,
            "MinQuantityPercent": 0
        }
    ],
    "ShowDistance": 1,
    "AddItemsToNearbyMarketZone": 0,
    "MaxDistance": 10.0,
    "MarkerName": "Deliver Items"
}
```

---

## Objective Parameters

### **`Collections`**
- **Type**: Array[ExpansionQuestObjectiveDelivery]
- **Description**: Items the quest players need to deliver for this objective and that will be spawned on the main quest player when the quest with this objective is accepted/started. There is always a class name and amount needed to define an entry correctly. "QuantityPercent" is needed when the player delivers items such as ammo or pills that can be stacked, "QuantityPercent" controls the stack size amount that gets spawned on the quest player when starting the quest. 10 should be used here as a value when the item has a quantity to match with the needed amount

---

### **`Collections` -> `Amount`**
- **Type**: Integer
- **Description**: Amount needed for the objective item

---

### **`Collections` -> `ClassName`**
- **Type**: String
- **Description**: Class name of the item needed

---

### **`Collections` -> `QuantityPercent`**
- **Type**: Integer
- **Description**: Max. quantity percentage of the item so it gets counted by the objective

---

### **`Collections` -> `MinQuantityPercent`**
- **Type**: Integer
- **Description**: Min. quantity percentage of the item so it gets counted by the objective

---

### **`ShowDistance`**
- **Type**: Boolean
- **Description**: Controls whether the distance to the objective position will be displayed in the quest HUD

---

### **`AddItemsToNearbyMarketZone`**
- **Type**: Boolean
- **Description**: Only used when the market mod is loaded and the quest turn-in NPC is within a market zone. Controls if the objective items get added to the nearby market zone after the quest with this objective has been completed. The stock and items given in the "Collections" array will then be added to the related market zone on the next server restart

---

### **`MaxDistance`**
- **Type**: Float
- **Description**: Max. distance to the turn-in NPC position to complete the distance check for the objective

---

### **`MarkerName`**
- **Type**: String
- **Description**: Given text is used for the quest objective marker when the Expansion-Navigation mod is loaded and 2D or 3D markers are enabled
