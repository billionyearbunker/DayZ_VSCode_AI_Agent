# Logs Settings

## Configuration Parameters

### **`m_Version`**
- **Type:** `Integer`
- **Description:** Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`Safezone`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Going in a safezone or leaving a safezone will be logged

---

### **`VehicleCarKey`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Pairing, unlocking, locking a vehicle will be logged

---

### **`VehicleTowing`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Towing a vehicle will be logged

---

### **`VehicleLockPicking`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Trying to lockpick will be logged

---

### **`BaseBuildingRaiding`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Damaging a basebuilding element or a safe will be logged

---

### **`CodeLockRaiding`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Damaging a codelock will be logged

---

### **`Territory`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Creating a territory, inviting someone will be logged

---

### **`Killfeed`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Dying will be logged

---

### **`Party`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Creating a party and inviting someone will be logged

---

### **`Chat`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Disabled
  - `1` = Any messages on the chat will be logged

---

### **`AdminTools`**
- **Type:** `Boolean`

0 = Disabled
1 = Any admin actions with special expansion tools will be logged (admincarkey, admin hammer, ...)
"SpawnSelection"
Boolean.

0 = Disabled
1 = Will create a log when a player will spawn
"MissionAirdrop"
Boolean.

0 = Disabled
1 = Airdrops will be logged
"Market"
Boolean.

0 = Disabled
1 = Will create logs about player transactions with the market
"ATM"
Boolean.

0 = Disabled
1 = Will create logs about player transactions with the ATM
