# TerritorySettings

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`EnableTerritories`**
- **Type**: Bool
- **Values**:
  - `0` = The Territory flag will only have the vanilla functionnality
  - `1` = Will enable Expansion Territory system

---

### **`UseWholeMapForInviteList`**
- **Type**: Bool
- **Values**:
  - `0` = The player can only invite players in his territory if they are near him
  - `1` = The player can invite anyone in his territory, even if they are on the other side of the map

---

### **`TerritorySize`**
- **Type**: Float
- **Description**: The radius of territory in meters

---

### **`TerritoryPerimterSize`**
- **Type**: Float
- **Description**: A perimeter surrounding a territory to prevent other territories to be built in. It will prevent territories to overlap if the value set is the same as TerritorySize or higher. [perimeter sheet]

---

### **`MaxMembersInTerritory`**
- **Type**: Integer
- **Description**: The max amount of members allowed per territories. If <= 0, unlimited territory size

---

### **`MaxTerritoryPerPlayer`**
- **Type**: Integer
- **Description**: The max amount of territories allowed per player. If <= 0, unlimited territory allowed

---

### **`TerritoryAuthenticationRadius`**
- **Type**: Float
- **Description**: The radius from where a player can accept a territory invite
