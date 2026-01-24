# Crafting Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 11,
    "ObjectiveText": "Craft an improvised fishing rod",
    "TimeLimit": -1,
    "Active": 1,
    "ItemNames": [
        "ImprovisedFishingRod"
    ],
    "ExecutionAmount": 1
}
```

---

## Objective Parameters

### **`ItemNames`**
- **Type**: Array[String]
- **Description**: Class names of the items the player can craft to complete this objective

---

### **`ExecutionAmount`**
- **Type**: Integer
- **Description**: How many times does the crafting action need to be executed to complete the objective?
