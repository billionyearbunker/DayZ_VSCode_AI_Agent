# Market TraderZones Settings

---

## File Location

Unlike most other settings that may not be map-specific, you can find the **traderzones** folder in your `mpmission\dayzOffline.<mapname>\expansion` folder.

**Important**: Traders will only act as traders if they are within the radius of a traderzone. NOTE that zones are spheres, so altitude for Position needs to be set correctly!

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`m_DisplayName`**
- **Type**: String
- **Description**: Market zone display name, can be whatever you want. Used for logging

---

### **`Position`**
- **Type**: Vector
- **Description**: Center position of the market zone in the game world

---

### **`Radius`**
- **Type**: Float
- **Description**: Used to define the size of the trader zone in the game world

---

### **`BuyPricePercent`**
- **Type**: Float
- **Description**: This controls the buy price for all market items in this specific zone. By default this value is 100% of the buy price as calculated from an item's stock, min price, max price, and min/max stock thresholds (see market categories settings)

---

### **`SellPricePercent`**
- **Type**: Float
- **Description**: This controls the sell price for all market items in this specific zone. By default this value is -1.0, meaning the global value from market settings will be used, but can be overridden by setting this to the desired percentage

---

### **`Stock`**
- **Type**: Map<String, Integer>
- **Description**: Contains all the items that can be purchased in this market zone and the current stock of each item. You can set the stock for each individual item or set it to 0 (meaning traders in this zone will only start selling the item after players have sold at least one of the respective item to the trader)
