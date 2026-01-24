# P2P Market Trader Configuration

---

## Overview

You can name a P2P market trader configuration file to whatever you want as long as it has the `.json` file extension and is placed in the `mpmissions\MISSIONNAME.MAPNAME\storage_x\expansion\p2pmarket` folder - it will get loaded by the personal storage system.

---

## Configuration Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Current config file version. NEVER CHANGE THIS UNLESS YOU KNOW WHAT YOU ARE DOING!

---

### **`m_TraderID`**
- **Type**: Integer
- **Description**: Unique trader ID for this trader. Never use the same ID twice!

---

### **`m_ClassName`**
- **Type**: String
- **Description**: Class name of the trader object that will be used to spawn the trader object
- **Requirements**:
  - Need to inherit from `ExpansionP2PMarketTraderNPCAI` when an AI NPC
  - Need to inherit from `ExpansionP2PMarketTraderNPC` when a normal NPC
  - Need to inherit from `ExpansionP2PMarketTraderStatic` when a static object

---

### **`m_Position`**
- **Type**: Vector
- **Description**: World position where the P2P market trader object will be created at

---

### **`m_Orientation`**
- **Type**: Vector
- **Description**: World orientation where the P2P market trader object will be facing at

---

### **`m_LoadoutFile`**
- **Type**: String
- **Description**: Loadout file for the trader NPC if it is an AI or normal NPC

---

### **`m_VehicleSpawnPosition`**
- **Type**: Vector
- **Description**: World positions where the P2P market will spawn land vehicles at when purchased

---

### **`m_WatercraftSpawnPosition`**
- **Type**: Vector
- **Description**: World positions where the P2P market will spawn watercrafts at when purchased

---

### **`m_AircraftSpawnPosition`**
- **Type**: Vector
- **Description**: World positions where the P2P market will spawn aircrafts at when purchased

---

### **`m_DisplayName`**
- **Type**: String
- **Description**: Display name that will be used in the P2P market menu or when the name-tags mod loaded and enabled next to the P2P market mod

---

### **`m_DisplayIcon`**
- **Type**: String
- **Description**: Display icon that will be used in the P2P market menu or when the name-tags mod loaded and enabled next to the P2P market mod. Can be a ExpansionIcon or any valid image path

---

### **`m_Faction`**
- **Type**: String
- **Description**: Faction for the NPC if it is an AI

---

### **`m_IsGlobalTrader`**
- **Type**: Boolean
- **Description**: If this trader should display all sale listings from all P2P market traders in the world then set this to 1

---

## Example Configuration JSON

```json
{
    "m_Version": 4,
    "m_TraderID": -1,
    "m_ClassName": "ExpansionP2PTraderAIJudy",
    "m_Position": [
        8551.580078125,
        15.703399658203125,
        10529.900390625
    ],
    "m_Orientation": [
        120.0,
        0.0,
        0.0
    ],
    "m_LoadoutFile": "SurvivorLoadout",
    "m_VehicleSpawnPosition": [
        3741.679931640625,
        402.8330078125,
        5996.14013671875
    ],
    "m_WatercraftSpawnPosition": [
        0.0,
        0.0,
        0.0
    ],
    "m_AircraftSpawnPosition": [
        0.0,
        0.0,
        0.0
    ],
    "m_DisplayName": "Unknown",
    "m_DisplayIcon": "Deliver",
    "m_Faction": "InvincibleObservers",
    "m_IsGlobalTrader": 0
}
