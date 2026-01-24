# SafeZoneSettings

**Note**: Unlike most other settings that may not be map-specific, you can find the SafeZoneSettings.json in your `mpmission\dayzOffline.<mapname>\expansion\settings` folder.

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`Enabled`**
- **Type**: Bool
- **Values**:
  - `0` = Safezones will be turned off
  - `1` = Safezones will be enabled, however they still need to be configured

---

### **`FrameRateCheckSafeZoneInMs`**
- **Type**: Integer
- **Description**: How often safezone checks for players, zombies and vehicles run. Should be left at default 0 (= check each tick) for best responsiveness. Granularity is 25ms

---

## Zone Configuration

### **`CircleZones`**
- **Type**: Array
- **Description**: A list of Circles Zones acting as safezones

**Format**:
```json
{
    "Center": [
        3728.27001953125,
        403.0,
        6003.60009765625
    ],
    "Radius": 500.0
}
```

#### **`Center`**
- **Type**: Vector
- **Description**: The position of the Zone in a 3D space (X,Y,Z)

#### **`Radius`**
- **Type**: Float
- **Description**: The size of this zone in meters

---

### **`CylinderZones`**
- **Type**: Array
- **Description**: A list of Cylinder Zones acting as safezones

**Format**:
```json
{
    "Center": [
        3728.27001953125,
        403.0,
        6003.60009765625
    ],
    "Radius": 500.0,
    "Height": 120.0
}
```

#### **`Center`**
- **Type**: Vector
- **Description**: The position of the Zone in a 3D space (X,Y,Z)

#### **`Radius`**
- **Type**: Float
- **Description**: The size of this zone in meters

#### **`Height`**
- **Type**: Float
- **Description**: The height of this zone in meters

---

### **`PolygonZones`**
- **Type**: Array
- **Description**: A list of Polygones Zones acting as safezones

**Format**:
```json
{
    "Positions": [
        [
            12288.900390625,
            142.39999389648438,
            12804.400390625
        ],
        [
            12068.400390625,
            139.8000030517578,
            12923.400390625
        ],
        [
            11680.599609375,
            141.10000610351563,
            12650.599609375
        ],
        [
            11805.2998046875,
            146.3000030517578,
            12258.900390625
        ],
        [
            12327.7001953125,
            140.0,
            12453.7998046875
        ]
    ]
}
```

#### **`Positions`**
- **Type**: Array of Vectors
- **Description**: A list of positions of the Zone in a 3D space (X,Y,Z)

---

## Performance Settings

### **`ActorsPerTick`**
- **Type**: Integer
- **Description**: How many safezone actors (players, zombies and vehicles combined) are checked each interval (FrameRateCheckSafeZoneInMs)

---

## Vehicle Settings

### **`DisableVehicleDamageInSafeZone`**
- **Type**: Bool
- **Values**:
  - `0` = Vehicles will take damage even when inside safezones
  - `1` = Vehicles can't be damaged inside safezones

---

## Cleanup Settings

### **`EnableForceSZCleanup`**
- **Type**: Bool
- **Values**:
  - `0` = Items dropped to the ground won't be removed automatically if in a safezone
  - `1` = Any items dropped to the ground in a safezone will be removed

---

### **`ItemLifetimeInSafeZone`**
- **Type**: Integer
- **Description**: Items dropped in a safezone will have this lifetime instead of their default lifetime. This time is in second(s)

---

### **`EnableForceSZCleanupVehicles`**
- **Type**: Bool
- **Values**:
  - `0` = Vehicles wont be removed from safezones
  - `1` = Vehicles will be removed from the safezones (deleted) once their lifetime will have reached 0

---

### **`VehicleLifetimeInSafeZone`**
- **Type**: Float
- **Description**: How long this vehicle will stay in the safezone before being removed. Time in seconds

---

### **`ForceSZCleanup_ExcludedItems`**
- **Type**: Array
- **Description**: A list of classnames which cannot be impacted by the safezone cleanup system

**Example**:
```json
"ForceSZCleanup_ExcludedItems": [
    "ClassName",
    "ClassName",
    "ClassName",
    "ClassName"
]
```
