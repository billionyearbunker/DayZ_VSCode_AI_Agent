# Adding a New Item to the Market

---

## Overview

To add a new item you will need to follow two steps:

1. Add the item in ONE of the categories available in the Market folder. This section is used to store all the information related to the item and its category
2. Add the item in the Traders you want to display this item (this step can be skipped if you are using the Categories config instead of the Items in these files, explained later in this guide)

---

## 1. Adding Your Item to the MARKET Folder

Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Market` and open **MyCategoryIWishToModify.json**

In this example we will add a new automatic weapon to the **Assault_Rifles.json**

### Example File Structure

The file you wish to modify should be similar to this example but with more items in it:

```json
{
    "m_Version": 12,
    "DisplayName": "My Category Name",
    "Icon": "Deliver",
    "Color": "FBFCFEFF",
    "IsExchange": 0,
    "InitStockPercent": 75.0,
    "Items": [
        {
            "ClassName": "MyItem_ClassName",
            "MaxPriceThreshold": 2000,
            "MinPriceThreshold": 1000,
            "SellPricePercent": -1,
            "MaxStockThreshold": 100,
            "MinStockThreshold": 1,
            "QuantityPercent": -1,
            "SpawnAttachments": [
                "MyAttachments_ClassName",
                "MyAttachments_ClassName2"
            ],
            "Variants": []
        },
        {
            "ClassName": "akm",
            "MaxPriceThreshold": 3000,
            "MinPriceThreshold": 1500,
            "SellPricePercent": -1,
            "MaxStockThreshold": 100,
            "MinStockThreshold": 1,
            "QuantityPercent": -1,
            "SpawnAttachments": [
                "ak_woodbttstck",
                "ak_woodhndgrd",
                "mag_akm_30rnd"
            ],
            "Variants": []
        }
    ]
}
```

### Adding New Item

All you need to add in this file to have your new item in the Market are the following lines:

```json
{
    "ClassName": "MyItem_ClassName",
    "MaxPriceThreshold": 2000,
    "MinPriceThreshold": 1000,
    "SellPricePercent": -1,    // from 0.0 (0%) to 1.0 (100%). -1 means it will use the GLOBAL sell price which will be in your traderzone json file
    "MaxStockThreshold": 100,  // To make this item have a static stock, have this number equal (the same as) MinStockThreshold
    "MinStockThreshold": 1,
    "QuantityPercent": -1,
    "SpawnAttachments": [
        "MyAttachments_ClassName",  // if your item doesn't have attachments, simply remove these two lines
        "MyAttachments_ClassName2"  // remove the comma if it's the last item from your list
    ],
    "Variants": []
}  // remove the comma if it's the last item from your list
```
2) Adding your item to the TRADERS folder
Go to DayZServer\ServerProfile (or config)\ExpansionMod\Traders and open MyTraderIWishToModify.json. In this example we will add a new automatic weapon to the Weapons.json

{
    "m_Version": 10,
    "TraderName": "Weapons",
    "DisplayName": "My Weapon Trader",
    "TraderIcon": "Shotgun",
    "Currencies": [
        "ExpansionBanknoteEuro"
    ],
    "Categories": ["Assault_Rifles:1","Buttstocks:3"],
    "Items": {
        "mag_akm_30rnd": 3,
        "ak_woodbttstck": 3,
        "ak_woodhndgrd": 3,
        "akm": 1,
        "MyItem_ClassName": 1,
        "MyAttachments_ClassName": 3,
        "MyAttachments_ClassName2": 3
    }
}
There are two ways to add a new item to a trader. The manual way and the automatic way !

The manual (items) solution will always override the automatic (categories) way.

Manual way
"Items": {
    "mag_akm_30rnd": 3,
    "ak_woodbttstck": 3,
    "ak_woodhndgrd": 3,
    "akm": 1,
    "MyItem_ClassName": 1,
    "MyAttachments_ClassName": 3,
    "MyAttachments_ClassName2": 3,  <== remove the comma if it's the last item from your list
}
This numbers mean:

0 = Player can only Buy
1 = Buy and Sell
2 = Player can only Sell
3 = Not visible but still available for item customisation (weapons, vests, backpacks) and attachments
Automatic way
In this case, we are not going to add the item but the category name. And more exactly the name of the file containing the category (for example: Assault_Rifles.json and Buttstocks.json)

"Categories": ["Assault_Rifles:1","Buttstocks:3"],
