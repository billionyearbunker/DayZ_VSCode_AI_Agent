# Setting up Custom Market Currencies

---

## Overview

If you plan on using different currency (or currencies) than the gold/silver bars and nuggets we provide by default with the Expansion Core mod, then you need to make some slight adjustments to the Exchange category configuration as well as the individual Trader settings files.

---

## Exchange/Currency Settings

The default file containing the currency configured by default is in your `YOUR_SERVER_PROFILE_DIRECTORY/ExpansionMod/Market/Exchange.JSON`. While we recommend using this file for your currencies, you can use any other files with any other names if you want to.

To flag a market file as an Exchange file (currency file) all you will have to do is make sure the setting **IsExchange** is set to `1`.

Then all you will have to do is configure your items and how much they are worth as shown here:

```json
    "m_Version": 12,
    "DisplayName": "My Custom Currencies",
    "Icon": "Deliver",
    "Color": "FBFCFEFF",
    "IsExchange": 1,
    "InitStockPercent": 75,
    "Items": [
        {
            "ClassName": "Example_moneyeuro_1000",
            "MaxPriceThreshold": 1000,
            "MinPriceThreshold": 1000,
            "SellPricePercent": -1,
            "MaxStockThreshold": 1,
            "MinStockThreshold": 1,
            "SpawnAttachments": [],
            "Variants": []
        },
        {
            "ClassName": "Example_moneyeuro_100",
            "MaxPriceThreshold": 100,
            "MinPriceThreshold": 100,
            "SellPricePercent": -1,
            "MaxStockThreshold": 1,
            "MinStockThreshold": 1,
            "SpawnAttachments": [],
            "Variants": []
        },
        {
            "ClassName": "Example_moneyeuro_10",
            "MaxPriceThreshold": 10,
            "MinPriceThreshold": 10,
            "SellPricePercent": -1,
            "MaxStockThreshold": 1,
            "MinStockThreshold": 1,
            "SpawnAttachments": [],
            "Variants": []
        },
        {
            "ClassName": "Example_moneyeuro_1",
            "MaxPriceThreshold": 1,
            "MinPriceThreshold": 1,
            "SellPricePercent": -1,
            "MaxStockThreshold": 1,
            "MinStockThreshold": 1,
            "SpawnAttachments": [],
            "Variants": []
        }
    ]
}
ClassName

The class name of the currency item you want to add. Case insensitive, does not need to be lowercase like in the example above.

MaxPriceThreshold and MinPriceThreshold

Defines the value of the item.

MaxPriceThreshold and MinPriceThreshold always need to have the same values like in the example above.

MaxStockThreshold and MinStockThreshold

Needs to be 1, or else the exchange of currency at an exchange trader will not work as expected!

Trader Settings
To define which type of currency will be accepted by each trader, we need to add the desired currency items to the Currencies array of the individual traders. The Market Trader settings files are located in your servers profile directory (YOUR_SERVER_PROFILE_DIRECTORY/ExpansionMod/Traders/).

Example:

"Currencies": [
    "Example_moneyeuro_1000",
    "Example_moneyeuro_100",
    "Example_moneyeuro_10",
    "Example_moneyeuro_1"
],
For further information about the trader settings, please take a look at this Wiki page:

https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-Trader-Settings

ATM Currencies
To define which type of currency will be accepted by the ATM, we need to add the desired currency items to the Currencies array of the MarketSettings. The MarketSettings file is located in your mission directory (mpmissions/dayzoffline.mapname/expansion/settings/).

Example:

"Currencies": [
    "Example_moneyeuro_1000",
    "Example_moneyeuro_100",
    "Example_moneyeuro_10",
    "Example_moneyeuro_1"
],
For further information about the trader settings, please take a look at this Wiki page:

https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-General-Market-Settings
