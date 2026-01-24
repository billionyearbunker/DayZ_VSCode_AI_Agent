# Adding a New Category to the Market

---

## Overview

To add a new category you will need to create and configure one json file per category.

**Note**: A category shouldn't have items from another category.

---

## Steps

1. Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Market`
2. Create a file named **MyCategory_Name.json**
3. In this file add the following lines:

```json
{
    "m_Version": 12,
    "DisplayName": "My Category Name Players Will See",
    "Icon": "Deliver",
    "Color": "FBFCFEFF",
    "IsExchange": 0,
    "InitStockPercent": 75.0,
    "Items": [
        {
            "ClassName": "MyClassName",
            "MaxPriceThreshold": 30,
            "MinPriceThreshold": 15,
            "SellPricePercent": -1,
            "MaxStockThreshold": 250,
            "MinStockThreshold": 1,
            "QuantityPercent": -1,
            "SpawnAttachments": [
                "MyAttachment_Classname",
                "MyAttachment_Classname"
            ],
            "Variants": [
                "MyClassname_Variant",
                "MyClassname_Variant"
            ]
        }
    ]
}
```

---

## Parameter Details

### **`Color`**
- **Type**: Hex Color Code
- **Description**: This is using hex color coding. You can use online hex color pickers to find quickly the desired color you want to use
- **Tool**: https://www.color-hex.com/

---

### **`Icon`**
- **Type**: String
- **Reference**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-List-of-default-icon-names
