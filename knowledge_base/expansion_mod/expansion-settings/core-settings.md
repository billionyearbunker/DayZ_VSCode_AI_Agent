# Core Settings

## Configuration Parameters

### **`m_Version`**
- **Type:** `Integer`
- **Description:** Used for internal file version tracking, do not edit.

---

### **`ServerUpdateRateLimit`**
- **Type:** `Integer`
- **Description:** This setting is limiting server script update rate (vanilla) per second. If you are using the `-limitFPS` parameter on the command line, then `ServerUpdateRateLimit` should be lower.
- **Values:**
  - `0` = let the game handle normally
  - `40` = minimum allowed

---

### **`FixCELifetime`**
- **Type:** `Bool`
- **Description:** When set to `1` or `true`, corrects the lifetime of items spawned by the central economy (see vanilla bug T194225)

---

### **`EnableInventoryCargoTidy`**
- **Type:** `Bool`
- **Description:** When set to `1` or `true`, shows a "tidy cargo" icon for each clothing/container in inventory on client which players can use to auto-arrange and combine items in a way that maximizes free space.
