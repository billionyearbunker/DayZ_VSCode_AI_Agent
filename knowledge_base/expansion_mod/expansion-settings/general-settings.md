# GeneralSettings

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

## Gameplay Features

### **`DisableShootToUnlock`**
- **Type**: Bool
- **Values**:
  - `0` = Players can shoot at locked building doors to brute force the door and unlock it
  - `1` = Players can't shoot at a locked building door and will need a lockpick to unlock the door of the building

---

### **`EnableGravecross`**
- **Type**: Bool
- **Values**:
  - `0` = Gravecross will be disabled. The dead player inventory will stay on him
  - `1` = Gravecross will be enabled. When a player will die a Gravecross will spawn on him with all his stuff in it. This is usualy used to prevent body despawn between restarts

---

### **`GravecrossDeleteBody`**
- **Type**: Bool
- **Requirement**: Only work if `EnableGravecross` is enabled
- **Values**:
  - `0` = If you still want the deadbody next to the Gravecross because you want your players to skin deadplayers
  - `1` = This will delete the body of the dead player. Why use this? To only have the Gravecross and not have a naked deadbody next to it

---

### **`GravecrossTimeThreshold`**
- **Type**: Integer
- **Requirement**: Only works if `EnableGravecross` is enabled
- **Description**: How long a player needs to be playing (in seconds) in one session to get the normal cross (Expansion_Gravecross) instead of the low lifetime one (Expansion_Gravecross_LowLifetime)

---

## Mapping and Environment

### **`UseCustomMappingModule`**
- **Type**: Bool
- **Warning**: Doesn't work with NatureOverhaul Mod. Custom mapping have a big impact on server and player performance
- **Values**:
  - `0` = The expansion custom mapping will be disabled, this will not disable custom interiors or ivy
  - `1` = The expansion custom mapping will be enabled, roadblocks, forests, new buildings and more detailed roads will be added. Currently, only ChernarusPlus have custom mapping

---

### **`Mapping`**
- **Type**: Array
- **Description**: List all the locations with custom mapping made by the mod Expansion. If you want to remove a location, just remove the line!

---

### **`ObjectsToDelete`**
- **Type**: Array
- **Description**: You can indicate the position and the name of a specific mapped object to be removed. This action can be done to multiple objects

---

### **`BuildingInteriors`**
- **Type**: Bool
- **Warning**: Doesn't work with NatureOverhaul Mod. Have a huge impact on server and player performance!
- **Values**:
  - `0` = Interiors won't be filled with new props
  - `1` = Interiors will be more detailled

---

### **`Interiors`**
- **Type**: Array
- **Description**: The list of buildings classnames allowed to spawn custom interiors. If you don't want a specific building to spawn custom interiors, just remove his classname from the list

---

### **`BuildingIvys`**
- **Type**: Bool
- **Note**: Only work for ChernarusPlus!
- **Values**:
  - `0` = No custom ivies will be added to the map
  - `1` = Custom Ivies in specific locations will be added to the map

---

## Lighting System

### **`EnableLamps`**
- **Type**: Integer
- **Values**:
  - `0` = Disabled - Street lights are off
  - `1` = Enabled - Street lights are enabled according to LampAmount_OneInX and LampSelectionMode

---

### **`LampAmount_OneInX`**
- **Type**: Integer
- **Default**: 3
- **Description**: Configures how many street lamps will have lights. E.g. the default value 3 will mean 1 in 3 lamps will have lights (33% of all lamps on the map)
- **Note**: It is not recommended to set this value to 1 (= all lamps on the map have lights) as it may cause considerable flicker when lights overlap

---

### **`LampSelectionMode`**
- **Type**: String
- **Default**: FARTHEST_RANDOM
- **Description**: Configures how the lamps with lights are distributed across the map
- **Modes**:
  - **RANDOM**: Completely random. May cause light overlap and thus flicker
  - **FARTHEST**: Uses optimized farthest point sampling to evenly spread out the lights. May generate the same light positions on each server start (not guaranteed)
  - **FARTHEST_RANDOM**: Like FARTHEST, but with random distribution

---

### **`EnableGenerators`**
- **Type**: Bool
- **Warning**: CURRENTLY DOESNT WORK. Currently unused. However you can spawn yourself this generators as events!
- **Values**:
  - `0` = No generators will be spawned inside the towns and villages
  - `1` = Will spawn in towns and villages generators for the mode 1 for `EnableLamps`

---

### **`EnableLighthouses`**
- **Type**: Bool
- **Values**:
  - `0` = the lighthouses won't emit a light beam
  - `1` = turns on the light of every lighthouse of the map

---

## HUD and UI Features

### **`EnableHUDNightvisionOverlay`**
- **Type**: Bool
- **Values**:
  - `0` = Use the NVG vanilla overlay (in short a green screen)
  - `1` = Add a immersive NVG overlay

---

### **`DisableMagicCrosshair`**
- **Type**: Bool
- **Values**:
  - `0` = Will use the current DayZ vanilla aiming system (bullet goes to crosshair when hipfiring)
  - `1` = Enable DayZ Alpha style aiming (bullet goes straight out of the barrel when hipfiring). This setting is needed for the laser sight attachment to be accurate

---

### **`EnableAutoRun`**
- **Type**: Bool
- **Values**:
  - `0` = This feature will be turned off
  - `1` = Allow the player to use the autorun feature. It will still work when they will be in their inventory
- **Controls**:
  - **SHIFT + Z** = Auto Sprint
  - **CTRL + Z** = Auto Walk
  - **Z** = Auto Jog

---

### **`UseDeathScreen`**
- **Type**: Bool
- **Values**:
  - `0` = Deathscreen will be a blackscreen as usual. Vanilla way
  - `1` = Add back the old school deathscreen (with the bloody hand)

---

### **`UseDeathScreenStatistics`**
- **Type**: Bool
- **Values**:
  - `0` = You won't be able to know your stats when dead like in vanilla
  - `1` = When dead you will be able to know your personal stats

---

### **`UseNewsFeedInGameMenu`**
- **Type**: Bool
- **Values**:
  - `0` = The news feed in the pause menu will be removed
  - `1` = The news feed in the pause menu will be enabled

---

## HUD Color Configuration

### **`HUDColors`**

The following color settings allow customization of HUD elements:

#### **`StaminaBarColor`**
- **Description**: Color of the stamina bar

#### **`NotifierDividerColor`**
- **Description**: Color of the notifier divider

#### **`TemperatureBurningColor`**
- **Description**: Color when temperature is burning

#### **`TemperatureHotColor`**
- **Description**: Color when temperature is hot

#### **`TemperatureIdealColor`**
- **Description**: Color when temperature is ideal

#### **`TemperatureColdColor`**
- **Description**: Color when temperature is cold

#### **`TemperatureFreezingColor`**
- **Description**: Color when temperature is freezing

#### **`NotifiersIdealColor`**
- **Description**: Color for notifiers in ideal state

#### **`NotifiersHalfColor`**
- **Description**: Color for notifiers at half state

#### **`NotifiersLowColor`**
- **Description**: Color for notifiers at low state

---

### Color Format

The format for all colors is:
- **Hexadecimal RRGGBBAA** or **RGBA**
- **Decimal R G B A** with range 0-255 (alpha is optional in all cases)

You can use this site to generate the hex color values for these settings: https://color.adobe.com/de/create/color-wheel

**Note**: If you want alpha transparency, you have to add it manually after the first six digits
