# Action Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 10,
    "ObjectiveText": "Lockpick a vehicle",
    "TimeLimit": -1,
    "Active": 1,
    "ActionNames": [
        "ExpansionVehicleActionPickLock",
        "ExpansionActionPickVehicleLockBase",
        "ExpansionActionPickVehicleLock"
    ],
    "AllowedClassNames": [],
    "ExcludedClassNames": [],
    "ExecutionAmount": 1
}
```

---

## Objective Parameters

### **`ActionNames`**
- **Type**: Array[String]
- **Description**: Class names of the action classes that will trigger this objective

---

### **`AllowedClassNames`**
- **Type**: Array[String]
- **Description**: Class names of items/entities that are allowed for this action objective
- **Example**: If we would add the name "PotatoSeed" in here and the player would need to execute the "Plant seed" action then the objective would only be completed when the player used a "PotatoSeed" for the plant action

---

### **`ExcludedClassNames`**
- **Type**: Array[String]
- **Description**: Class names of items/entities that are not allowed for this action objective
- **Example**: If we add the name "PotatoSeed" in here and the player would need to execute the "Plant seed" action then the objective would only be completed when the player used any seed but not when he used "PotatoSeed" for the plant action

---

### **`ExecutionAmount`**
- **Type**: Integer
- **Description**: Controls how many times the action needs to be executed to complete this objective
