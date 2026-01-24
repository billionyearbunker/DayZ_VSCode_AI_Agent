# MVS (Modular Vest System) Items - Organized by Color

This directory contains individual XML files for each color variant of MVS gear. Each file is formatted according to the DayZ types.xml standard and contains all accessories, clothing, bags, and gear for that specific color.

## Files Created

### Primary Color Variants
- **MVS_OD.xml** (40 items) - Olive Drab/Green military gear
  - Combat vests, pouches, helmets, packs, belts, holsters, sheaths, canteens
  - S10 Respirator, OpsCore helmet, Combat Vest Heavy variants
  - Assault Pack, Radio Pack, Rucksack, Compact carriers, Chest Rigs
  - Balaclavas and shrouds

- **MVS_Tan.xml** (40 items) - Desert Tan/Coyote Brown gear
  - Same item types as OD variant
  - Includes Tan_Worn helmet variant (see MVS_Tan_Worn.xml)

- **MVS_Black.xml** (43 items) - Black tactical gear
  - Same item types as OD/Tan variants
  
- **MVS_Snow.xml** (39 items) - Winter/Snow camouflage
  - Same item types as OD/Tan/Black variants

### Camouflage Patterns
- **MVS_ERDL.xml** (29 items) - ERDL camouflage pattern
  - Combat vests, pouches, helmets, packs, accessories
  - OpsCore helmets, armored helmets, warrior helmets

- **MVS_Multicam.xml** (34 items) - Multicam camouflage pattern
  - Full loadout including chest rigs, compact carriers, rucksacks
  - Helmets (Warrior, Armored), flat caps, boonie hats
  - BDU shirts, Gorka pants and jackets, canteens
  - All standard pouches and packs

- **MVS_Multicam_Tropic.xml** (34 items) - Multicam Tropic (green) variant
  - Same item types as standard Multicam

- **MVS_Multicam_Black.xml** (34 items) - Multicam Black variant
  - Same item types as standard Multicam

### Specialty Items
- **MVS_Patches.xml** (36 items) - Decorative patches (Patch_01 through Patch_35)
  
- **MVS_Brown.xml** (4 items) - Brown colored items
  - Pakol hats and similar brown-specific gear

- **MVS_FS.xml** (1 item) - Forest/Special variant
  - MVS_S10Respirator_FS

- **MVS_Wraith.xml** (1 item) - Special Wraith variant
  - MVS_Balaclava_Wraith

- **MVS_Tan_Worn.xml** (1 item) - Worn/weathered variant
  - MVS_Helmet_01_Tan_Worn

- **MVS_Other.xml** (221 items) - Base items without color suffixes
  - Radio, base BDU clothing, FlatCaps, GorkaJackets, BoonieHats
  - Items that serve as base models or don't have color-specific variants
  - Generic items that can be used with any color loadout

## Usage

These files are organized to make it easier to:
1. Enable/disable specific color variants on your server
2. Adjust spawn rates for specific color loadouts
3. Create trader configurations for color-coordinated gear sets
4. Manage loot economy by color variant

## Format

Each file follows the standard DayZ types.xml format:
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<types>
  <!-- MVS Gear - [Color] Color Variant -->
  <type name="MVS_Item_Name">
    <nominal>0</nominal>
    <lifetime>7200</lifetime>
    <restock>0</restock>
    <min>0</min>
    <quantmin>-1</quantmin>
    <quantmax>-1</quantmax>
    <cost>100</cost>
    <flags count_in_cargo="0" count_in_hoarder="0" count_in_map="1" count_in_player="0" crafted="0" deloot="0"/>
    <category name="clothes"/>
    <usage name="Military"/>
  </type>
  ...
</types>
```

## Total Items
**557 MVS items** organized across 14 files

## Notes
- All items are currently set to nominal=0 (disabled by default)
- Most items use lifetime=7200 (2 hours), packs use 21600 (6 hours)
- All items are categorized as Military usage
- Patches have shorter lifetime (3600 = 1 hour)

---
Generated from: `mpmissions/empty.deerisle/ModTypes/Clothing-types.xml`
Location: `mpmissions/empty.deerisle/ModTypes/MVS_by_color/`
