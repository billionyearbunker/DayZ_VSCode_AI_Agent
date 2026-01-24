# MissionSettings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`Enabled`**
- **Type**: Bool
- **Values**:
  - `0` = All the missions will be disabled
  - `1` = It will enable missions, currently only airdrop missions are available but more are planned in the future

---

### **`InitialMissionStartDelay`**
- **Type**: Integer
- **Description**: After a server restart, how long the mission need to wait to start. This number is in milliseconds

---

### **`TimeBetweenMissions`**
- **Type**: Integer
- **Description**: Time in milliseconds before a new mission start

---

### **`MinMissions`**
- **Type**: Integer
- **Description**: Minimum mission allowed at once. The number should not be greater than `MaxMissions`

---

### **`MaxMissions`**
- **Type**: Integer
- **Description**: Maximum mission allowed at once

---

### **`MinPlayersToStartMissions`**
- **Type**: Integer
- **Description**: Minimum required of players to start a mission
