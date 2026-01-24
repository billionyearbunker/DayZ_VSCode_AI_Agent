# NameTagsSettings

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`EnablePlayerTags`**
- **Type**: Bool
- **Values**:
  - `0` = Disabled
  - `1` = Players nametags will be enabled. Looking at a player will display his name
- **Note**: If you want this feature to be enabled anywhere. Make sure `ShowPlayerTagsInSafeZones` and `ShowPlayerTagsInTerritories` are disabled (0)

---

### **`PlayerTagViewRange`**
- **Type**: Integer
- **Description**: The maximum distance (in meters) to see the nametags when looking at a player

---

### **`PlayerTagsIcon`**
- **Type**: Integer
- **Description**: The path of a edds icon so you can use your own icon or another expansion icon

---

### **`PlayerTagsColor`**
- **Type**: Integer
- **Description**: The color of the icon, use this website to generate the color you want. Enter the RGBA values and then click on the button "ARGB → int" to generate the color code you will need.
- **Color Values**:
  - **R**: Red
  - **G**: Green
  - **B**: Blue
  - **A**: Opacity from 0 (can't be seen) to 255 (very visible, opaque)
- **Note**: You can use this website to generate the RGBA color, however watch out this website generate the A value from 0 to 1 instead of 255!

---

### **`PlayerNameColor`**
- **Type**: Integer
- **Description**: Color for the name displayed in the tag, use this website to generate the color you want. Enter the RGBA values and then click on the button "ARGB → int" to generate the color code you will need.
- **Color Values**:
  - **R**: Red
  - **G**: Green
  - **B**: Blue
  - **A**: Opacity from 0 (can't be seen) to 255 (very visible, opaque)
- **Note**: You can use this website to generate the RGBA color, however watch out this website generate the A value from 0 to 1 instead of 255!

---

### **`ShowPlayerTagsInSafeZones`**
- **Type**: Bool
- **Values**:
  - `0` = Disabled
  - `1` = Should you only allow players to see the nametags of others while inside a safezone

---

### **`ShowPlayerTagsInTerritories`**
- **Type**: Integer
- **Values**:
  - `0` = Disabled
  - `1` = Should you only allow players to see the nametags of others while inside a territory
