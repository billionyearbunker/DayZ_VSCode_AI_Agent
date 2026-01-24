# Trader Mod unofficial config

---

## WARNING!

This config is **not up to date** and is **NOT official**. If anyone among the community wants to share their own trader config we have no issues sharing it here. Same for trader mapping.

---

## Adding an Aircraft Trader to Chernarus

### Step 1: Install Trader Mod

Make sure you have the following trader mod installed: https://steamcommunity.com/sharedfiles/filedetails/?id=1590841260

Follow the install instructions on that page.

### Step 2: Add Trader Marker

Add the following inside of your `TraderObjects.txt`:

```
// North West Aircraft:

<TraderMarker>          6
<TraderMarkerPosition>  4080,    339,    10801
<TraderMarkerSafezone>  30
<VehicleSpawn>          4092,    340,    10782       // Vehicle Spawnpoint for Trader;    Coordinate X,     Coordinate Y,     Coordinate Z (optional)
<VehicleSpawnOri>       -90,     0,      0           // Vehicle Spawnpoint Orientation;   Yaw,              Pitch,            Roll         (optional)
```

Make sure this is under your `// Kumyrna:` config around line 59 (Using Notepad++).

### Step 3: Add Trader NPC and Objects

Add the following also inside of your `TraderObjects.txt`:

```
// North West Aircraft:
<Object>                SurvivorM_Taiki
<ObjectPosition>        4080,    339,    10801
<ObjectOrientation>     90,      0,      0
<ObjectAttachment>      AviatorGlasses
<ObjectAttachment>      BomberJacket_Black
<ObjectAttachment>      Jeans_Black
<ObjectAttachment>      CombatBoots_Black


<Object>                Land_Mil_Fortified_Nest_Small
<ObjectPosition>        4079.080811, 340.034180, 10801.098633
<ObjectOrientation>     80.999992,   0,           0
 
<Object>                Land_Mil_CamoNet_Roof_east
<ObjectPosition>        4079.046143, 340.272644, 10800.850586
<ObjectOrientation>     -98.000015,  0,           0
 
<Object>                Wreck_UH1Y
<ObjectPosition>        4074.843750, 340.806946, 10812.857422
<ObjectOrientation>     -104.000000, 0,           0
 
<Object>                Wreck_Mi8
<ObjectPosition>        4073.852783, 340.647949, 10791.951172
<ObjectOrientation>     -45.000000,  0,           0
 
<Object>                Land_Misc_Well_Pump_Yellow
<ObjectPosition>        4070.367432, 339.726288, 10800.843750
<ObjectOrientation>     0,           0,           0
 
 <Object>               Land_FuelStation_Feed
<ObjectPosition>        4087.541016, 340.008636, 10779.255859
<ObjectOrientation>     63,          0,           0
```

Make sure this is at the bottom of the file just above `// FileName.txt`

### Step 4: Add Trader Configuration

Add the following to your `TraderConfig.txt`:

```
<Trader> Aircraft Trader
    <Category> Helicopters
    ExpansionUh1h, V, 150000, 75000
    ExpansionMh6, V, 150000, 75000
    ExpansionMerlin, v, 150000, 75000
    ExpansionGyrocopter, V, 35000, 17500
    
    <Category> Helicopter Parts
    ExpansionHelicopterBattery, *, 4000, 2000
    CarRadiator, *, 500, 250
    SparkPlug, *, 250, 125
    HeadlightH7, *, 75, 30
    ExpansionHydraulicHoses, *, 300, 150
    ExpansionIgniterPlug, *, 500, 250
```

Make sure this is placed towards the bottom just above the Keys section at around line 1184.

Adjust pricing as you wish.

### Step 5: Add Map Marker

Add the map marker to your map by editing your `MapSettings.json` in your ExpansionMod:

```json
{
    "m_UID": "NWAircraftTrader",
    "m_Visibility": 6,
    "m_Is3D": 1,
    "m_Text": "Aircraft Trader",
    "m_IconName": "Helicopter",
    "m_Color": -13710223,
    "m_Position": [
        4080,
        339,
        10801
    ]
}
```

For help adding markers see the documentation here: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-Adding-server-markers

### Step 6: Vehicle Parts Configuration

```
<VehicleParts> ExpansionUh1h
ExpansionHelicopterBattery
ExpansionHydraulicHoses
CarRadiator
ExpansionIgniterPlug

<VehicleParts> ExpansionGyrocopter
ExpansionHelicopterBattery
CarRadiator
SparkPlug
HeadlightH7

<VehicleParts> ExpansionMh6
ExpansionHelicopterBattery
CarRadiator
ExpansionIgniterPlug
ExpansionHydraulicHoses
HeadlightH7
Expansion_Mh6_Door_1_1
Expansion_Mh6_Door_1_2
Expansion_Mh6_Door_2_1
Expansion_Mh6_Door_2_2

<VehicleParts> ExpansionMerlin
ExpansionHelicopterBattery
CarRadiator
ExpansionHydraulicHoses
ExpansionIgniterPlug
HeadlightH7
HeadlightH7
ExpansionMerlinFrontWheel
ExpansionMerlinFrontWheel
ExpansionMerlinBackWheel
ExpansionMerlinBackWheel
```

---

## Additional Categories Configuration

**Thanks to the user T4nk for this config!**

### Expansion Optics

```
<Category> Expansion Optics
ExpansionDeltapointOptic, *, 500, 250
ExpansionEXPS3HoloOptic, *, 750, 325
ExpansionHAMROptic, *, 1000, 500
ExpansionReflexMRSOptic, *, 750, 325
Expansion_M1A_RailAtt, *, 300, 150
```

### Expansion Weapons

```
<Category> Expansion Weapons
ExpansionRPG7, *, 100000, 10000
ExpansionLAW, *, 100000, 10000
Expansion_M79, *, 100000, 10000
ExpansionFlaregun, *, 1000, 500
Expansion_M9, *, 900, 450
Expansion_G36, *, 1000, 500
Expansion_MPX, *, 1000, 500
Expansion_MP7, *, 1000, 500
Expansion_Kedr, *, 1000, 500
Expansion_M16, *, 1000, 500
Expansion_M1A, *, 1000, 500
Expansion_DT11, *, 1000, 500
Expansion_BenelliM4, *, 1000, 500
Expansion_AWM, *, 1000, 500
```

### Expansion Ammo

```
<Category> Expansion Ammo
AmmoBox_Expansion_46x30_25rnd, *, 500, 250
AmmoBox_Expansion_338_15rnd, *, 500, 250
ExpansionAmmoRPG, *, 1000, 500
ExpansionAmmoLAW, *, 1000, 500
ExpansionAmmoFlare, *, 500, 250
ExpansionAmmoFlareLight, *, 500, 250
Ammo_Expansion_M203_Smoke_White, *, 500, 250
Ammo_Expansion_M203_Smoke_Red, *, 500, 250
Ammo_Expansion_M203_Smoke_Green, *, 500, 250
Ammo_Expansion_M203_Smoke_Yellow, *, 500, 250
Ammo_Expansion_M203_Smoke_Purple, *, 500, 250
Ammo_Expansion_M203_Smoke_Teargas, *, 500, 250
Ammo_Expansion_M203_Sticky_Smoke_White, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Red, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Green, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Yellow, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Purple, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Teargas, *, 900, 450
Ammo_Expansion_M203_HE, *, 1000, 500
Ammo_Expansion_46x30, *, 100, 50
Ammo_Expansion_338, *, 100, 50
```

### Expansion Mags

```
<Category> Expansion Mags
Mag_Expansion_M14_20Rnd, *, 500, 250
Mag_Expansion_M14_10Rnd, *, 500, 250
Mag_Expansion_M9_15Rnd, *, 500, 250
Mag_Expansion_MPX_50Rnd, *, 500, 250
Mag_Expansion_G36_30Rnd, *, 500, 250
Mag_Expansion_Kedr_20Rnd, *, 500, 250
Mag_Expansion_MP7_40Rnd, *, 500, 250
Mag_Expansion_AWM_5Rnd, *, 500, 250
```

### Expansion Food

```
<Category> Expansion Food
ExpansionMilkBottle, *, 100, 50
ExpansionBread1, *, 100, 50
ExpansionBread2, *, 100, 50
ExpansionBread3, *, 100, 50
ExpansionCheese1, *, 100, 50
ExpansionCheese2, *, 100, 50
ExpansionCheese3, *, 100, 50
ExpansionCheese4, *, 100, 50
```

### Expansion Building

```
<Category> Expansion Building
ExpansionFloorKit, *, 500, 250
ExpansionWoodPillarKit, *, 500, 250
ExpansionRampKit, *, 500, 250
ExpansionStairKit, *, 500, 250
ExpansionWallKit, *, 500, 250
ExpansionCamoBoxKit, *, 500, 250
ExpansionBarrierGateKit, *, 500, 250
ExpansionCamoTentKit, *, 500, 250
ExpansionSafeLarge, *, 500, 250
ExpansionSafeMini, *, 500, 250
ExpansionSafeMedium, *, 500, 250
ExpansionGunrack, *, 500, 250
ExpansionHelipadKit, *, 500, 250
ExpansionBarbedWireKit, *, 500, 250
ExpansionHescoKit, *, 500, 250
ExpansionCodeLock, *, 500, 250
ExpansionBarbedWireKit, *, 500, 250
ExpansionHescoKit, *, 500, 250
ExpansionBarrierGateKit, *, 500, 250
ExpansionCamoBoxKit, *, 500, 250
ExpansionATent, *, 500, 250
ExpansionHelipadKit, *, 500, 250
ExpansionWoodPillarKit, *, 500, 250
```
SparkPlug
HeadlightH7

<VehicleParts> ExpansionMh6
ExpansionHelicopterBattery
CarRadiator
ExpansionIgniterPlug
ExpansionHydraulicHoses
HeadlightH7
Expansion_Mh6_Door_1_1
Expansion_Mh6_Door_1_2
Expansion_Mh6_Door_2_1
Expansion_Mh6_Door_2_2

<VehicleParts> ExpansionMerlin
ExpansionHelicopterBattery
CarRadiator
ExpansionHydraulicHoses
ExpansionIgniterPlug
HeadlightH7
HeadlightH7
ExpansionMerlinFrontWheel
ExpansionMerlinFrontWheel
ExpansionMerlinBackWheel
ExpansionMerlinBackWheel
```

---

## Additional Categories Configuration

**Thanks to the user T4nk for this config!**

### Expansion Optics

```
<Category> Expansion Optics
ExpansionDeltapointOptic, *, 500, 250
ExpansionEXPS3HoloOptic, *, 750, 325
ExpansionHAMROptic, *, 1000, 500
ExpansionReflexMRSOptic, *, 750, 325
Expansion_M1A_RailAtt, *, 300, 150
```

### Expansion Weapons

```
<Category> Expansion Weapons
ExpansionRPG7, *, 100000, 10000
ExpansionLAW, *, 100000, 10000
Expansion_M79, *, 100000, 10000
ExpansionFlaregun, *, 1000, 500
Expansion_M9, *, 900, 450
Expansion_G36, *, 1000, 500
Expansion_MPX, *, 1000, 500
Expansion_MP7, *, 1000, 500
Expansion_Kedr, *, 1000, 500
Expansion_M16, *, 1000, 500
Expansion_M1A, *, 1000, 500
Expansion_DT11, *, 1000, 500
Expansion_BenelliM4, *, 1000, 500
Expansion_AWM, *, 1000, 500
```

### Expansion Ammo

```
<Category> Expansion Ammo
AmmoBox_Expansion_46x30_25rnd, *, 500, 250
AmmoBox_Expansion_338_15rnd, *, 500, 250
ExpansionAmmoRPG, *, 1000, 500
ExpansionAmmoLAW, *, 1000, 500
ExpansionAmmoFlare, *, 500, 250
ExpansionAmmoFlareLight, *, 500, 250
Ammo_Expansion_M203_Smoke_White, *, 500, 250
Ammo_Expansion_M203_Smoke_Red, *, 500, 250
Ammo_Expansion_M203_Smoke_Green, *, 500, 250
Ammo_Expansion_M203_Smoke_Yellow, *, 500, 250
Ammo_Expansion_M203_Smoke_Purple, *, 500, 250
Ammo_Expansion_M203_Smoke_Teargas, *, 500, 250
Ammo_Expansion_M203_Sticky_Smoke_White, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Red, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Green, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Yellow, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Purple, *, 800, 400
Ammo_Expansion_M203_Sticky_Smoke_Teargas, *, 900, 450
Ammo_Expansion_M203_HE, *, 1000, 500
Ammo_Expansion_46x30, *, 100, 50
Ammo_Expansion_338, *, 100, 50
```

### Expansion Mags

```
<Category> Expansion Mags
Mag_Expansion_M14_20Rnd, *, 500, 250
Mag_Expansion_M14_10Rnd, *, 500, 250
Mag_Expansion_M9_15Rnd, *, 500, 250
Mag_Expansion_MPX_50Rnd, *, 500, 250
Mag_Expansion_G36_30Rnd, *, 500, 250
Mag_Expansion_Kedr_20Rnd, *, 500, 250
Mag_Expansion_MP7_40Rnd, *, 500, 250
Mag_Expansion_AWM_5Rnd, *, 500, 250
```

### Expansion Food

```
<Category> Expansion Food
ExpansionMilkBottle, *, 100, 50
ExpansionBread1, *, 100, 50
ExpansionBread2, *, 100, 50
ExpansionBread3, *, 100, 50
ExpansionCheese1, *, 100, 50
ExpansionCheese2, *, 100, 50
ExpansionCheese3, *, 100, 50
ExpansionCheese4, *, 100, 50
```

### Expansion Building

```
<Category> Expansion Building
ExpansionFloorKit, *, 500, 250
ExpansionWoodPillarKit, *, 500, 250
ExpansionRampKit, *, 500, 250
ExpansionStairKit, *, 500, 250
ExpansionWallKit, *, 500, 250
ExpansionCamoBoxKit, *, 500, 250
ExpansionBarrierGateKit, *, 500, 250
ExpansionCamoTentKit, *, 500, 250
ExpansionSafeLarge, *, 500, 250
ExpansionSafeMini, *, 500, 250
ExpansionSafeMedium, *, 500, 250
ExpansionGunrack, *, 500, 250
ExpansionHelipadKit, *, 500, 250
ExpansionBarbedWireKit, *, 500, 250
ExpansionHescoKit, *, 500, 250
ExpansionCodeLock, *, 500, 250
ExpansionBarbedWireKit, *, 500, 250
ExpansionHescoKit, *, 500, 250
ExpansionBarrierGateKit, *, 500, 250
ExpansionCamoBoxKit, *, 500, 250
ExpansionATent, *, 500, 250
ExpansionHelipadKit, *, 500, 250
ExpansionWoodPillarKit, *, 500, 250
```
