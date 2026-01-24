# GarageSettings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`Enabled`**
- **Type**: Boolean
- **Values**:
  - `0` = Disable
  - `1` = Enable
- **Description**: Enable/Disable the garage system and its modules

---

### **`AllowStoringDEVehicles`**
- **Type**: Bool
- **Description**: Allow storing vehicles spawned by dynamic CE events (e.g. events.xml)
- **Note**: You should set nominal and min to zero in your events.xml files before enabling this, or each stored vehicle can respawn!

---

### **`GarageMode`**
- **Type**: Enum
- **Values**:
  - `0` = Territory Mode: Player needs to be a member/owner of a territory to store/retrieve vehicles on garage points
  - `1` = Personal Mode: Player can store/retrieve vehicles without any requirement on garage access points

---

### **`GarageStoreMode`**
- **Type**: Enum
- **Values**:
  - `0` = Personal Mode: Only players can store there vehicles
  - `1` = Shared Mode: All territory members can store a vehicles if the vehicle owner was a member
  - `2` = Tyrannical Mode: Only the territory owner and moderators can store vehicles of territory members

---

### **`GarageRetrieveMode`**
- **Type**: Enum
- **Values**:
  - `0` = Personal Mode: Only players can retrieve there vehicles
  - `1` = Shared Mode: All territory members can retrieve vehicles if the vehicle was stored by a territory member
  - `2` = Tyrannical Mode: Only the territory owner and moderators can retrieve vehicles if the vehicle was stored by a territory member

---

### **`MaxStorableVehicles`**
- **Type**: Integer
- **Description**: Max. amount of vehicles a player or territory can store in the vitual garage, depending on the selected garage mode

---

### **`VehicleSearchRadius`**
- **Type**: Float
- **Description**: Max. distance in meters within the the garage access points detects world vehicles. Vehicles standing outside of this range dont get displayed in the menu

---

### **`CanStoreWithCargo`**
- **Type**: Boolean
- **Values**:
  - `0` = Disable
  - `1` = Enable
- **Description**: Allow vehicles to be stored with there cargo items. This does not include the vehicles attachments as these get always stored by default

---

### **`UseVirtualStorageForCargo`**
- **Type**: Boolean
- **Values**:
  - `0` = Disable
  - `1` = Enable
- **Description**: Normally, for if CanStoreWithCargo is enabled the cargo items of the vehicle are transferred to a hidden placeholder in the world, so that count_in_cargo="1" still works. When this setting is enabled, the cargo items are stored in the entity storage with the vehicle instead

---

### **`NeedKeyToStore`**
- **Type**: Boolean
- **Values**:
  - `0` = Disable
  - `1` = Enable
- **Description**: A car key needs to be bound to the vehicle to store it the garage

---

### **`EntityWhitelist`**
- **Type**: Array
- **Description**: List of the entity class names that can be used as garage access point. The action will be displayed on all entities defined in this array

---

### **`EnableGroupFeatures`**
- **Type**: Boolean
- **Values**:
  - `0` = Disable
  - `1` = Enable
- **Description**: If the expansion group mod is loaded the virtual garage includes some additional features that can be enabled/disabled here

---

### **`GroupStoreMode`**
- **Type**: Enum
- **Values**:
  - `0` = Group members can only store vehicles of other group members
  - `1` = Group members can only retrieve vehicles of other group members
  - `2` = Group members can store and retrieve vehicles of other group members

---

### **`EnableMarketFeatures`**
- **Type**: Boolean
- **Values**:
  - `0` = Disable
  - `1` = Enable
- **Description**: If the expansion market mod is loaded the virtual garage includes some additional features that can be enabled/disabled here

---

### **`StorePricePercent`**
- **Type**: Float
- **Description**: Controls the price percantage value for storing a vehicle. The base price is always the max. buy price of the vehicle in the expansion market settings. StaticStorePrice setting value need to be 0

---

### **`StaticStorePrice`**
- **Type**: Integer
- **Description**: Controls the static price for storing a vehicle. StorePricePercent setting value need to be 0

---

## Territory Parking Meter Upgrades

If territories are used the following settings can be used to control the upgrade values for the virtual garage when the Expansion Parking Meter is deployed within a territory. The parking meter can be upgraded and depending on the upgrade the storage and/or detection range of the parking meter access point can be increased.

### **`MaxStorableTier1 - MaxStorableTier3`**
Integer.

Controls how many vehicles can be stored in the territory garage by the territory members when the certain upgrade is installed.

"ParkingMeterEnableFlavor"
Boolean.

0 = Disable
1 = Enable some cosmetic changes to the parking meter which doesnt affect gameplay in anyway. This is just a small easter egg.
