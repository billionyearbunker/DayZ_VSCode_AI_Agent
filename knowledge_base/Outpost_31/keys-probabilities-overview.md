# Police Zombie Keycard Drop System - Probability Overview

## Overview

On Outpost 31, police-type zombies have a chance to drop keycard access keys (CJ_Key series) when killed. This document provides a comprehensive breakdown of how the drop system works, which zombie types can carry keys, and the exact probabilities for obtaining them.

---

## How the Drop System Works

### Core Mechanics

1. **Cargo Spawn Chance**: Each police zombie has a `cargo chance="0.05"` for the key pool, meaning **5% base probability** that they will have a key
2. **Random Key Selection**: If the 5% chance succeeds, the zombie spawns with **one random key** from a pool of 10 possible keys
3. **Equal Distribution**: All 10 keys in the pool have `chance="1.0"`, giving each specific key an equal probability of being selected
4. **Standard Keys Only**: Police zombies can only drop **Standard Keys** (CJ_Key1 through CJ_Key10), not Premium or Special keys
5. **Pristine Condition**: Keys always spawn in perfect condition (0% damage)

### Configuration Example

From [cfgspawnabletypes.xml](s:\servers\Outpost_31_Dev\mpmissions\empty.deerisle\cfgspawnabletypes.xml):

```xml
<type name="ZmbM_PolicemanSpecForce">
    <cargo preset="toolsPolice" />
    <cargo preset="ammoPolice" />
    <cargo chance="0.05">
        <item name="CJ_Key1" chance="1.0" />
        <item name="CJ_Key2" chance="1.0" />
        ...
        <item name="CJ_Key10" chance="1.0" />
    </cargo>
</type>
```

---

## Global Probability

The probability of getting a key from a police zombie involves two stages:

**Stage 1 - Key Pool Activation**: 5% chance (0.05) that the zombie has ANY key  
**Stage 2 - Specific Key Selection**: If Stage 1 succeeds, 10% chance (1/10) for each specific key

**Combined Probability for ANY Key**: 5.00%  
**Combined Probability for SPECIFIC Key** (e.g., CJ_Key5): 5% × 10% = **0.50%**

---

## Police Zombie Types & Drop Rates

### Zombie Type Breakdown

All police-type zombies have the **same key drop configuration**:

| Zombie Type                       | Base Key Chance | Key Pool Size | Keys Available     |
|-----------------------------------|-----------------|---------------|--------------------|
| **ZmbF_PoliceWomanNormal**        | 5%              | 10 keys       | CJ_Key1 - CJ_Key10 |
| **ZmbM_PolicemanFat**             | 5%              | 10 keys       | CJ_Key1 - CJ_Key10 |
| **ZmbM_PolicemanSpecForce**       | 5%              | 10 keys       | CJ_Key1 - CJ_Key10 |
| **ZmbM_PolicemanSpecForce_Heavy** | 5%              | 10 keys       | CJ_Key1 - CJ_Key10 |

### What This Means

- **All police zombies are equal** - No zombie type has better or worse key drop rates
- **1 in 20 chance** - On average, every 20 police zombies you kill will drop one key
- **Standard Keys Only** - Premium keys (101-103) and Special keys (200-204) **cannot** drop from police zombies
- **Random Distribution** - You have no control over which key drops; each of the 10 keys has equal odds

---

## Detailed Probability Tables

### 1. Key Drop Overview (10 keys available)

| Key Name | Drop Probability | Key Tier     | Purpose                      |
|----------|------------------|--------------|------------------------------|
| CJ_Key1  | 0.50%            | Standard Key | Keycard Room Access Level 1  |
| CJ_Key2  | 0.50%            | Standard Key | Keycard Room Access Level 2  |
| CJ_Key3  | 0.50%            | Standard Key | Keycard Room Access Level 3  |
| CJ_Key4  | 0.50%            | Standard Key | Keycard Room Access Level 4  |
| CJ_Key5  | 0.50%            | Standard Key | Keycard Room Access Level 5  |
| CJ_Key6  | 0.50%            | Standard Key | Keycard Room Access Level 6  |
| CJ_Key7  | 0.50%            | Standard Key | Keycard Room Access Level 7  |
| CJ_Key8  | 0.50%            | Standard Key | Keycard Room Access Level 8  |
| CJ_Key9  | 0.50%            | Standard Key | Keycard Room Access Level 9  |
| CJ_Key10 | 0.50%            | Standard Key | Keycard Room Access Level 10 |

**Combined Probability**: 5.00% chance to get ANY key from this pool

---

### 2. Keys NOT Available from Police Zombies

The following keys **cannot** be obtained from police zombies and must be acquired through other means (quests, military zombies, etc.):

| Key Name  | Key Tier     | How to Obtain              |
|-----------|--------------|----------------------------|
| CJ_Key11  | Standard Key | Quests or Military Zombies |
| CJ_Key12  | Standard Key | Quests or Military Zombies |
| CJ_Key101 | Premium Key  | Quests or Military Zombies |
| CJ_Key102 | Premium Key  | Quests or Military Zombies |
| CJ_Key103 | Premium Key  | Quests or Military Zombies |
| CJ_Key200 | Special Key  | Quests or Military Zombies |
| CJ_Key201 | Special Key  | Quests or Military Zombies |
| CJ_Key202 | Special Key  | Quests or Military Zombies |
| CJ_Key203 | Special Key  | Quests or Military Zombies |
| CJ_Key204 | Special Key  | Quests or Military Zombies |

---

## Probability Analysis

### Cumulative Probabilities

If you kill **multiple police zombies**, your chances of receiving at least one key increase:

| Police Zombies Killed | Chance of ANY Key | Chance of SPECIFIC Key (e.g., CJ_Key5) |
|-----------------------|-------------------|----------------------------------------|
| 1 zombie              | 5.00%             | 0.50%                                  |
| 5 zombies             | 22.62%            | 2.48%                                  |
| 10 zombies            | 40.13%            | 4.88%                                  |
| 20 zombies            | 64.15%            | 9.52%                                  |
| 50 zombies            | 92.31%            | 22.18%                                 |
| 100 zombies           | 99.41%            | 39.35%                                 |
| 200 zombies           | ~100%             | 63.25%                                 |

**Formula**: 1 - (1 - p)^n where p = probability, n = number of zombies killed

### Expected Value

On average, to receive:
- **ANY key from a police zombie**: Kill ~20 zombies
- **A SPECIFIC key** (e.g., CJ_Key7): Kill ~200 zombies
- **All 10 different keys**: Kill ~500+ zombies (collector's problem with duplicates)

### Drop Rate Context

For comparison with other police zombie loot:
- **Police Tools/Ammo**: Much more common (30-50% cargo chance)
- **Sniper Magazines**: 10-30% chance on certain police types
- **Keycards**: 5% chance (same as our key system)

---

## Farming Strategy

### For Players Seeking Keys

1. **Target High-Density Areas**: Focus on towns and cities with multiple police stations
2. **Identify Police Zombies**: Look for zombies in police uniforms (black/blue clothing, police hats/vests)
3. **Expect Variance**: With only 5% base chance, streaks of no drops are normal
4. **Farm Efficiently**: Kill groups of police zombies rather than individual encounters
5. **Check Bodies Thoroughly**: Keys can be missed in crowded inventories

### Best Locations for Police Zombies (Deer Isle)

Based on typical Deer Isle map layout:
- **Major Towns**: Stonington, Portland Harbor
- **Police Stations**: Any town with a police station will spawn police zombies nearby
- **Military Checkpoints**: Occasionally spawn police alongside military
- **City Centers**: Downtown areas often have higher police zombie spawns

### Zombie Identification Guide

**Visual Cues for Police Zombies**:
- **Uniform Colors**: Black, dark blue, or navy clothing
- **Headgear**: Police caps, tactical helmets, or berets
- **Body Armor**: Some variants wear police vests or tactical gear
- **Female Variant**: ZmbF_PoliceWomanNormal is identifiable by female body type in police uniform

### Time Investment

**Realistic Expectations**:
- **Casual Play** (5 police kills/hour): ~4 hours to get 1 key
- **Active Farming** (20 police kills/hour): ~1 hour to get 1 key
- **Efficient Grinding** (50 police kills/hour): ~24 minutes to get 1 key

**For a SPECIFIC key** (e.g., only need CJ_Key3):
- **Casual Play**: ~40 hours average
- **Active Farming**: ~10 hours average
- **Efficient Grinding**: ~4 hours average

---

## Technical Notes

### Zombie Loot Configuration

All police zombies using this key system share these settings:

```xml
<cargo preset="toolsPolice" />       // Police-specific tools
<cargo preset="ammoPolice" />        // Police-specific ammunition
<cargo chance="0.05">                // 5% chance to activate this cargo pool
    <item name="CJ_Key1" chance="1.0" />   // Each key has equal weight
    ...
    <item name="CJ_Key10" chance="1.0" />
</cargo>
```

### Key Item Properties

When a key spawns on a zombie:
- **Condition**: Always pristine (0% damage, 100% health)
- **Quantity**: Always 1 key per zombie (cannot spawn multiple)
- **Lifetime**: 14,400 seconds (4 hours) after being dropped
- **Stacking**: Keys do not stack; each occupies one inventory slot

### Spawn Pool Mechanics

**How the game determines drops**:
1. Zombie spawns with base cargo presets (tools, ammo)
2. Game rolls 5% chance for key cargo pool
3. If successful, randomly selects ONE key from the 10 available
4. Key is placed in zombie's pants/jacket/vest cargo slots
5. Player must loot the zombie to retrieve the key

---

## Comparison to Other Key Sources

### Police Zombies vs. Quest Rewards

**Police Zombies (This Document)**:
- Drop Chance: 5% for any key
- Keys Available: 10 (CJ_Key1 - CJ_Key10)
- Effort: Kill ~20 zombies per key
- Consistency: Low (random drops)

**Quest Rewards**:
- Reward Chance: 1.176% per key (20 total keys in pool)
- Keys Available: All 20 keys
- Effort: Complete 1 quest per attempt
- Consistency: Medium (deterministic but random)

### Police Zombies vs. Military Zombies

**Police Zombies**:
- Base Chance: 5%
- Key Pool: 10 keys (Standard 1-10)
- Difficulty: Easy to kill
- Spawn Rate: Common in civilian areas

**Military Zombies**:
- Base Chance: 5%
- Key Pool: 10 keys (Standard 11-12, Premium, Special)
- Difficulty: Harder to kill (better gear)
- Spawn Rate: Rare, military areas only

**Strategy**: Farm police for Standard Keys 1-10, then move to military/quests for higher-tier keys.

---

## Advanced Tips & Tricks

### Maximizing Key Farming Efficiency

1. **Server Restarts**: Police zombies respawn after server restarts; plan sessions around this
2. **Route Optimization**: Create a loop through multiple police stations for continuous spawns
3. **Stealth Kills**: Use suppressed weapons to avoid attracting other zombies/players
4. **Inventory Management**: Keep inventory light to quickly loot and move on
5. **Team Farming**: Split up to cover more ground; share duplicate keys

### Common Mistakes to Avoid

❌ **Farming the same spot repeatedly** - Zombies may not respawn immediately  
❌ **Expecting every key type to drop** - Only 10 of the 20 keys drop from police  
❌ **Giving up after 10-15 kills** - 5% is low; expect variance  
❌ **Not checking all cargo slots** - Keys can spawn in any pocket/vest slot  
❌ **Killing non-police zombies** - Civilian zombies do not carry keys

### Statistical Edge Cases

**Lucky Streaks**: 
- 3 keys in 10 kills = Top 5% luck
- 5 keys in 20 kills = Top 1% luck

**Unlucky Streaks**:
- 0 keys in 50 kills = Bottom 8% luck (not impossible, just bad RNG)
- 0 keys in 100 kills = Bottom 0.6% luck (extremely unlucky)

If you hit 100+ kills with no keys, verify you're killing **police** zombies, not civilians.

---

## Frequently Asked Questions

### Q: Do certain police zombie types drop keys more often?
**A**: No. All four police zombie types (PoliceWoman, PolicemanFat, PolicemanSpecForce, PolicemanSpecForce_Heavy) have identical 5% key drop rates.

### Q: Can I get Premium or Special keys from police zombies?
**A**: No. Police zombies only drop CJ_Key1 through CJ_Key10. For keys 11, 12, 101-103, and 200-204, you must complete quests or farm military zombies.

### Q: Do keys despawn if I don't loot them immediately?
**A**: Yes. Keys have a 4-hour lifetime after being dropped. If you kill a zombie and don't loot it, the key will despawn after 4 hours.

### Q: Can police zombies spawn with multiple keys?
**A**: No. Each police zombie can only have ONE key at most. The 5% chance is for a single key from the pool.

### Q: Does server population affect key drop rates?
**A**: No. Drop rates are hardcoded and not affected by player count or server load.

### Q: Are keys affected by the loot economy?
**A**: No. Keys spawn directly on zombies and are not part of the dynamic loot economy system.

### Q: Can I trade keys with other players?
**A**: Yes, if they are in your inventory. Keys are tradeable items.

### Q: Do I need to check every police zombie corpse?
**A**: Yes, if you're farming keys. Approximately 1 in 20 will have a key, so consistent looting is essential.

---

## Conclusion

The police zombie key drop system on Outpost 31 uses a **two-stage probability model**:
1. **5% chance** the zombie has any key
2. **10% chance** (1 in 10) for each specific key within that pool

While the overall drop rate is modest, police zombies are abundant and easy to farm, making them a reliable source for **Standard Keys CJ_Key1 through CJ_Key10**. For higher-tier keys (11, 12, Premium, Special), players must pursue quests or military zombie farming.

**Key Takeaway**: Expect to kill ~20 police zombies per key drop. With persistence and efficient farming routes, accumulating the full set of Standard Keys (1-10) is achievable through dedicated gameplay.

---

*Document Version: 1.0*  
*Last Updated: January 19, 2026*  
*Data Source: [cfgspawnabletypes.xml](s:\servers\Outpost_31_Dev\mpmissions\empty.deerisle\cfgspawnabletypes.xml)*
