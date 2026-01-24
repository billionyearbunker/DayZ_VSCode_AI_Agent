# Collection Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 4,
    "ObjectiveText": "Collect 5 apples",
    "TimeLimit": -1,
    "Active": 1,
    "Collections": [
        {
            "Amount": 5,
            "ClassName": "Apple",
            "QuantityPercent": -1,
            "MinQuantityPercent": 0
        }
    ],
    "ShowDistance": 1,
    "AddItemsToNearbyMarketZone": 0,
    "NeedAnyCollection": 0
}
```

---

## Objective Parameters

### **`Collections`**
- **Type**: Array[ExpansionQuestObjectiveDelivery]
- **Description**: Items the quest players need to/can collect for this objective

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

### **`NeedAnyCollection`**
- **Type**: Boolean
- **Description**: Controls if the quest players need to collect all the items defined in the "Collections" array or only one. If this parameter is enabled and players still have more than one objective item then they will need to select the item they want to use to complete this quest when turning the quest in
