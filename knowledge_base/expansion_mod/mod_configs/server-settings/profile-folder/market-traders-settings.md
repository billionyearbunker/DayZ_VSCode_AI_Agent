# Trader Settings

---

## Setting Parameters

### **`m_Version`**

- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

### **`DisplayName`**

- **Type**: String
- **Description**: Display name of the trader that will be displayed on the top of the market menu when using this trader
- **Values**: You can use localized strings `#STR_BLABLA` or raw text `Hello World !`

**Examples:**

```json
"DisplayName": "#STR_EXPANSION_MARKET_TRADER_VEHICLE_PARTS"
"DisplayName": "Vehicle Parts"
```

### **`MinRequiredReputation`** (Only if you have Expansion Hardline!)

- **Type**: Integer
- **Description**: The Minimum Reputation Required from the player to be able to interact with this trader

**Example:**

```json
"MinRequiredReputation": 0
```

### **`MaxRequiredReputation`** (Only if you have Expansion Hardline!)

- **Type**: Integer
- **Description**: The Maximum Reputation Required from the player to be able to interact with this trader

**Example:**

```json
"MaxRequiredReputation": 2147483647
```

### **`TraderIcon`**

- **Type**: String
- **Description**: Icon of the trader that will be displayed on the top of the market menu when using this trader. See List of default icon names

**Example:**

```json
"TraderIcon": "Gas"
```

### **`Currencies`**

- **Type**: Array [String]
- **Description**: Classnames of the currencies this trader will accept. These currencies will need to be first configured in your Market folder. For more information please read this guide: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-Setting-up-Custom-Market-Currencies

**Example:**

```json
"Currencies": [
    "expansionbanknotehryvnia",
    "expansionbanknoteeuro"
]
```

---

## Categories and Items

### **`Categories`**

- **Type**: Array [String]
- **Description**: Filenames (without JSON extension) of market categories in ExpansionMod\Market that this trader should show. Can be used instead of or in addition to Items. Also supports the same buy/sell integers (see below) as Items, but has to be entered in a slightly different way (instead of "CategoryFilename", use "CategoryFilename:<value>")

**Values:**

- `0` = Can only be bought from this trader, but not sold
- `1` = Buy and Sell
- `2` = Can only be sold to this trader, but not bought
- `3` = Not visible but still available for item customisation (weapons, vests, backpacks) and attachments (vehicles)

**Example:**

```json
"Categories": [
    "Cars:1",
    "Vehicle_Parts:3"
]
```

### **`Items`**

- **Type**: Map [String, Integer]
- **Description**: A list of items the trader can sell/buy. The integer value controls whether an item can be only be bought (0), bought and sold (1), or only sold (2) at this specific trader. A special value of 3 is also possible, which means the item should not be shown in the trader menu normally and is only sellable/purchasable as attachment

**Values:**

- `0` = Can only be bought from this trader, but not sold
- `1` = Buy and Sell
- `2` = Can only be sold to this trader, but not bought
- `3` = Not visible but still available for item customisation (weapons, vests, backpacks) and attachments

**Example:**

```json
"Items": {
    "expansioncarkey": 0,
    "engineoil": 2
}
```

---

## Additional Information

For further information please take a look at the setup guide for the trader entities/NPCs:

https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-Setting-up-Trader-Entities-and-NPCs
