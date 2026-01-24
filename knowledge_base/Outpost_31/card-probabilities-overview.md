# Military Zombie Keycard Drop System - Probability Overview

## Overview

On Outpost 31, military-type zombies have a chance to drop advanced keycard access keys when killed. Unlike police zombies which drop Standard Keys (1-10), military zombies drop the **higher-tier keys**: Standard Keys 11-12, Premium Keys (101-103), and Special Keys (200-204). This document provides a comprehensive breakdown of how the military drop system works and the exact probabilities for obtaining these advanced keys.

---

## How the Drop System Works

### Core Mechanics

1. **Cargo Spawn Chance**: Each military zombie has a `cargo chance="0.05"` for the key pool, meaning **5% base probability** that they will have a key
2. **Random Key Selection**: If the 5% chance succeeds, the zombie spawns with **one random key** from a pool of 10 possible keys
3. **Equal Distribution**: All 10 keys in the pool have `chance="1.0"`, giving each specific key an equal probability of being selected
4. **Advanced Keys Only**: Military zombies can only drop **Standard Keys 11-12, Premium Keys (101-103), and Special Keys (200-204)** - NOT the lower-tier Standard Keys 1-10
5. **Pristine Condition**: Keys always spawn in perfect condition (0% damage)

### Configuration Example

From [cfgspawnabletypes.xml](s:\servers\Outpost_31_Dev\mpmissions\empty.deerisle\cfgspawnabletypes.xml):

```xml
<type name="ZmbM_SoldierNormal">
    <cargo preset="foodArmy" />
    <cargo preset="ammoArmy" />
    <cargo chance="0.05">
        <item name="CJ_Key11" chance="1.0" />
        <item name="CJ_Key12" chance="1.0" />
        <item name="CJ_Key101" chance="1.0" />
        <item name="CJ_Key102" chance="1.0" />
        <item name="CJ_Key103" chance="1.0" />
        <item name="CJ_Key200" chance="1.0" />
        <item name="CJ_Key201" chance="1.0" />
        <item name="CJ_Key202" chance="1.0" />
        <item name="CJ_Key203" chance="1.0" />
        <item name="CJ_Key204" chance="1.0" />
    </cargo>
</type>
```

---

## Global Probability

The probability of getting a key from a military zombie involves two stages:

**Stage 1 - Key Pool Activation**: 5% chance (0.05) that the zombie has ANY key  
**Stage 2 - Specific Key Selection**: If Stage 1 succeeds, 10% chance (1/10) for each specific key

**Combined Probability for ANY Key**: 5.00%  
**Combined Probability for SPECIFIC Key** (e.g., CJ_Key101): 5% × 10% = **0.50%**

---

## Military Zombie Types & Drop Rates

### Zombie Type Breakdown

All military-type zombies have the **same key drop configuration**:

| Zombie Type                       | Base Key Chance | Key Pool Size | Keys Available                  |
|-----------------------------------|-----------------|---------------|---------------------------------|
| **ZmbM_PatrolNormal_Autumn**      | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_PatrolNormal_Flat**        | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_PatrolNormal_PautRev**     | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_PatrolNormal_Summer**      | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_SoldierNormal**            | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_usSoldier_Officer_Desert** | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_usSoldier_Officer_Convoy** | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **ZmbM_usSoldier_Heavy_Woodland** | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **InfectedSoldierHardJMC**        | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |
| **InfectedSoldierHardJMCWinter**  | 5%              | 10 keys       | Keys 11-12, 101-103, 200-204    |

### What This Means

- **All military zombies are equal** - No zombie type has better or worse key drop rates
- **1 in 20 chance** - On average, every 20 military zombies you kill will drop one key
- **Advanced Keys Only** - Basic Standard Keys (1-10) **cannot** drop from military zombies
- **Random Distribution** - You have no control over which key drops; each of the 10 keys has equal odds
- **Harder to Farm** - Military zombies are tougher to kill, often wear armor, and spawn in dangerous areas

---

## Detailed Probability Tables

### 1. Key Drop Overview (10 keys available)

| Key Name  | Drop Probability | Key Tier          | Purpose                           |
|-----------|------------------|-------------------|-----------------------------------|
| CJ_Key11  | 0.50%            | Standard Key      | Keycard Room Access Level 11      |
| CJ_Key12  | 0.50%            | Standard Key      | Keycard Room Access Level 12      |
| CJ_Key101 | 0.50%            | Premium Key       | Keycard Room Access - Premium T1  |
| CJ_Key102 | 0.50%            | Premium Key       | Keycard Room Access - Premium T2  |
| CJ_Key103 | 0.50%            | Premium Key       | Keycard Room Access - Premium T3  |
| CJ_Key200 | 0.50%            | Special Key       | Keycard Room Access - Special T1  |
| CJ_Key201 | 0.50%            | Special Key       | Keycard Room Access - Special T2  |
| CJ_Key202 | 0.50%            | Special Key       | Keycard Room Access - Special T3  |
| CJ_Key203 | 0.50%            | Special Key       | Keycard Room Access - Special T4  |
| CJ_Key204 | 0.50%            | Special Key       | Keycard Room Access - Special T5  |

**Combined Probability**: 5.00% chance to get ANY key from this pool

### Key Tier Breakdown

| Tier Type     | Key Count | Category Probability | Individual Key Probability |
|---------------|-----------|----------------------|----------------------------|
| **Standard**  | 2         | 1.00%                | 0.50% each                 |
| **Premium**   | 3         | 1.50%                | 0.50% each                 |
| **Special**   | 5         | 2.50%                | 0.50% each                 |
| **Total**     | **10**    | **5.00%**            | —                          |

---

### 2. Keys NOT Available from Military Zombies

The following keys **cannot** be obtained from military zombies and must be acquired through other means (quests or police zombies):

| Key Name | Key Tier     | How to Obtain        |
|----------|--------------|----------------------|
| CJ_Key1  | Standard Key | Quests or Police     |
| CJ_Key2  | Standard Key | Quests or Police     |
| CJ_Key3  | Standard Key | Quests or Police     |
| CJ_Key4  | Standard Key | Quests or Police     |
| CJ_Key5  | Standard Key | Quests or Police     |
| CJ_Key6  | Standard Key | Quests or Police     |
| CJ_Key7  | Standard Key | Quests or Police     |
| CJ_Key8  | Standard Key | Quests or Police     |
| CJ_Key9  | Standard Key | Quests or Police     |
| CJ_Key10 | Standard Key | Quests or Police     |

---

## Probability Analysis

### Cumulative Probabilities

If you kill **multiple military zombies**, your chances of receiving at least one key increase:

| Military Zombies Killed | Chance of ANY Key | Chance of SPECIFIC Key (e.g., CJ_Key101) |
|-------------------------|-------------------|------------------------------------------|
| 1 zombie                | 5.00%             | 0.50%                                    |
| 5 zombies               | 22.62%            | 2.48%                                    |
| 10 zombies              | 40.13%            | 4.88%                                    |
| 20 zombies              | 64.15%            | 9.52%                                    |
| 50 zombies              | 92.31%            | 22.18%                                   |
| 100 zombies             | 99.41%            | 39.35%                                   |
| 200 zombies             | ~100%             | 63.25%                                   |

**Formula**: 1 - (1 - p)^n where p = probability, n = number of zombies killed

### Expected Value

On average, to receive:
- **ANY key from a military zombie**: Kill ~20 zombies
- **A SPECIFIC key** (e.g., CJ_Key200): Kill ~200 zombies
- **All 10 different keys**: Kill ~500+ zombies (collector's problem with duplicates)

### Tier-Specific Probabilities

For players seeking specific tiers:

| Target                      | Kills Needed (Average) | Cumulative Chance (20 kills) | Cumulative Chance (50 kills) |
|-----------------------------|------------------------|------------------------------|------------------------------|
| **Any Standard Key (11-12)**| ~100 zombies           | 19.92%                       | 63.96%                       |
| **Any Premium Key (101-103)**| ~67 zombies           | 27.60%                       | 77.69%                       |
| **Any Special Key (200-204)**| ~40 zombies           | 39.58%                       | 87.78%                       |

### Drop Rate Context

For comparison with other military zombie loot:
- **Military Food/Ammo**: Much more common (100% cargo presets)
- **Quest Items (STAG)**: Varies by zombie type
- **Advanced Keys**: 5% chance (same as police key system)
- **Officer Punched Cards**: 40% chance (ZmbM_usSoldier_Officer_Convoy only)

---

## Farming Strategy

### For Players Seeking Advanced Keys

1. **Target Military Zones**: Focus on military bases, airfields, checkpoints
2. **Identify Military Zombies**: Look for camouflage uniforms, tactical gear, helmets
3. **Prepare for Combat**: Military zombies are harder to kill than civilians/police
4. **Expect Variance**: With only 5% base chance, long dry spells are normal
5. **Risk vs. Reward**: Military areas often have PvP encounters; farm with caution

### Best Locations for Military Zombies (Deer Isle)

Based on typical Deer Isle map layout:
- **Military Bases**: Paris Island Base, Area 42
- **Airfields**: Deer Isle Airfield
- **Military Checkpoints**: Various roadblocks and fortifications
- **Crash Sites**: Helicopter crash sites spawn military zombies
- **Convoy Locations**: Special convoy-themed zombies in specific areas

### Zombie Identification Guide

**Visual Cues for Military Zombies**:
- **Uniform Colors**: Camouflage patterns (woodland, desert, urban)
- **Headgear**: Military helmets, berets, patrol caps
- **Body Armor**: Plate carriers, tactical vests, heavy armor
- **Variants**:
  - **Patrol**: Standard camo uniforms (Autumn, Flat, Summer variants)
  - **Soldier**: Combat uniforms with tactical gear
  - **Officer**: Command uniforms, sometimes with different colored attire
  - **Heavy**: Plate armor and heavy helmets
  - **JMC**: Modded elite soldiers with enhanced gear (Hard variants)

### Time Investment

**Realistic Expectations** (accounting for difficulty):
- **Casual Play** (3 military kills/hour): ~6.7 hours to get 1 key
- **Active Farming** (10 military kills/hour): ~2 hours to get 1 key
- **Efficient Grinding** (25 military kills/hour): ~48 minutes to get 1 key

**For a SPECIFIC key** (e.g., only need CJ_Key200):
- **Casual Play**: ~67 hours average
- **Active Farming**: ~20 hours average
- **Efficient Grinding**: ~8 hours average

**Note**: These times are longer than police farming due to:
- Lower spawn density in military zones
- Zombies are harder to kill (take more ammo/time)
- Travel between military zones takes longer
- Higher risk of player encounters

---

## Technical Notes

### Zombie Loot Configuration

All military zombies using this key system share these settings:

```xml
<cargo preset="foodArmy" />          // Military food rations
<cargo preset="ammoArmy" />          // Military ammunition
<cargo chance="0.05">                // 5% chance to activate this cargo pool
    <item name="CJ_Key11" chance="1.0" />    // Each key has equal weight
    ...
    <item name="CJ_Key204" chance="1.0" />
</cargo>
```

### Special Military Zombie Notes

**ZmbM_usSoldier_Officer_Convoy**:
- Has additional 100% cargo chance for PunchedCard (40% probability)
- Does NOT have ammoArmy preset (only foodArmy)
- Still has same 5% key drop rate

**InfectedSoldierHardJMC (Modded Elite)**:
- Has multiple cargo presets (STAG_Clothing, ammoArmyJMC, mixArmyJMC, STAG_QuestItem)
- Tougher to kill than standard military
- Same 5% key drop rate despite being "elite"

**InfectedSoldierHardJMCWinter**:
- Winter variant with WinterSoldier preset
- Spawns with winter gear
- Same 5% key drop rate

### Key Item Properties

When a key spawns on a military zombie:
- **Condition**: Always pristine (0% damage, 100% health)
- **Quantity**: Always 1 key per zombie (cannot spawn multiple)
- **Lifetime**: 14,400 seconds (4 hours) after being dropped
- **Stacking**: Keys do not stack; each occupies one inventory slot

### Spawn Pool Mechanics

**How the game determines drops**:
1. Zombie spawns with base cargo presets (foodArmy, ammoArmy, etc.)
2. Game rolls 5% chance for key cargo pool
3. If successful, randomly selects ONE key from the 10 available
4. Key is placed in zombie's pants/jacket/vest cargo slots
5. Player must loot the zombie to retrieve the key

---

## Comparison to Other Key Sources

### Military Zombies vs. Police Zombies

**Military Zombies (This Document)**:
- Drop Chance: 5% for any key
- Keys Available: 10 (CJ_Key11-12, 101-103, 200-204)
- Effort: Kill ~20 zombies per key
- Difficulty: Hard (armored, better AI, dangerous zones)
- Spawn Rate: Rare, military areas only

**Police Zombies**:
- Drop Chance: 5% for any key
- Keys Available: 10 (CJ_Key1-10)
- Effort: Kill ~20 zombies per key
- Difficulty: Easy (standard zombies)
- Spawn Rate: Common in civilian areas

**Strategy**: Farm police first for Standard Keys 1-10, then progress to military zones for advanced keys.

### Military Zombies vs. Quest Rewards

**Military Zombies (This Document)**:
- Drop Chance: 5% for any key (0.5% specific)
- Keys Available: 10 (advanced tier)
- Effort: Kill ~20 zombies per key attempt
- Consistency: Low (random drops)
- Risk: High (PvP, tough zombies)

**Quest Rewards**:
- Reward Chance: 1.176% per key (20 total keys in pool)
- Keys Available: All 20 keys (including military-tier)
- Effort: Complete 1 quest per attempt
- Consistency: Medium (deterministic but random)
- Risk: Varies by quest

**Strategy**: Use both methods. Farm military zombies while completing quests in military areas for double chances at advanced keys.

---

## Advanced Tips & Tricks

### Maximizing Key Farming Efficiency

1. **Night Raids**: Fewer players in military zones at night; use NVGs for advantage
2. **Route Optimization**: Create a circuit between multiple military zones
3. **Suppressed Weapons**: Essential for stealth; avoid attracting hordes
4. **Squad Farming**: Team up to handle tougher zombies; share duplicate keys
5. **Server Restarts**: Military zombies respawn after restarts; time your sessions
6. **Loot Priority**: Check officer zombies first (they often have quest items too)

### Combat Tips for Military Zombies

**Gear Recommendations**:
- **Weapons**: High-damage firearms (5.56mm+) or headshot-capable rifles
- **Ammo**: Bring 2-3x normal amount (military zombies are bullet sponges)
- **Armor**: Plate carrier or tactical vest (for PvP encounters)
- **Medical**: Extra bandages/blood bags (combat is riskier)

**Tactical Approach**:
- **Heavy Zombies**: Aim for headshots; body shots waste ammo
- **Groups**: Separate and kill individually; avoid being overwhelmed
- **Officer Zombies**: Priority targets (may have quest items + keys)
- **Retreat Option**: Always have an exit strategy; military zones attract PvP

### Common Mistakes to Avoid

❌ **Farming solo without backup gear** - One death = lost progress  
❌ **Shooting without suppressors** - Attracts players and more zombies  
❌ **Checking only vest/pants** - Keys can spawn in any cargo slot  
❌ **Staying in one spot too long** - Respawn times vary; rotate zones  
❌ **Fighting during peak hours** - Higher PvP risk; farm during off-hours  
❌ **Killing non-military zombies** - Civilian/police zombies don't drop these keys

### Statistical Edge Cases

**Lucky Streaks**: 
- 3 keys in 10 kills = Top 5% luck
- 5 keys in 20 kills = Top 1% luck
- Getting 2+ Special keys in 30 kills = Top 5% luck

**Unlucky Streaks**:
- 0 keys in 50 kills = Bottom 8% luck (bad RNG but not impossible)
- 0 keys in 100 kills = Bottom 0.6% luck (extremely unlucky)
- 0 Premium/Special keys in 50 kills = ~37% chance (more common than you think)

If you hit 100+ kills with no keys, verify you're killing **military** zombies, not civilian variants.

---

## Frequently Asked Questions

### Q: Do certain military zombie types drop keys more often?
**A**: No. All 10 military zombie types have identical 5% key drop rates. Officers, heavies, and elite JMC variants have the same odds as standard patrol zombies.

### Q: Can I get Standard Keys (1-10) from military zombies?
**A**: No. Military zombies only drop CJ_Key11, 12, 101-103, and 200-204. For keys 1-10, you must farm police zombies or complete quests.

### Q: Are Special Keys (200-204) rarer than Premium Keys (101-103)?
**A**: No. All 10 keys in the military pool have equal 0.50% drop chance. Special keys seem rarer only because there are 5 of them (more variety = harder to get a specific one).

### Q: Do heavy/armored military zombies drop keys more often?
**A**: No. ZmbM_usSoldier_Heavy_Woodland and other armored variants have the same 5% rate. The extra difficulty doesn't increase drop chances.

### Q: Does loot cycling in military zones help?
**A**: Not for zombie drops. Keys spawn ON zombies when they spawn, not from ground loot. You need zombie respawns, not loot cycling.

### Q: Can military zombies spawn with multiple keys?
**A**: No. Each military zombie can only have ONE key at most. The 5% chance is for a single key from the pool.

### Q: Do quest items affect key drop rates on JMC zombies?
**A**: No. The STAG_QuestItem cargo preset is separate from the key cargo pool. Both can roll independently.

### Q: Are keys affected by server loot economy settings?
**A**: No. Keys spawn directly on zombies via cfgspawnabletypes.xml and are not part of the dynamic loot economy.

### Q: Can I trade these advanced keys with other players?
**A**: Yes, if they are in your inventory. All keys are tradeable items.

### Q: What's the fastest way to get a full set of military keys?
**A**: Combine methods: farm military zombies in high-density areas while completing quests nearby. Trade duplicates with other players.

---

## Key Acquisition Roadmap

### Recommended Progression Path

**Phase 1: Police Keys (Easier)**
- Farm police zombies for CJ_Key1 through CJ_Key10
- Estimated time: 40-60 hours casual, 10-20 hours active
- Low risk, high availability

**Phase 2: Military Standard Keys**
- Target CJ_Key11 and CJ_Key12 from military zombies
- Estimated time: 10-15 hours for both
- Medium risk, medium availability

**Phase 3: Premium Keys**
- Farm for CJ_Key101, 102, 103
- Estimated time: 15-25 hours for all three
- Medium-high risk

**Phase 4: Special Keys**
- Farm for CJ_Key200-204
- Estimated time: 25-40 hours for all five
- High risk, highest variance

**Phase 5: Quest Supplementation**
- Complete quests for any missing keys
- Use quests as "bad luck protection"
- Trade duplicates with other players

**Total Expected Time** (all 20 keys via farming):
- Casual: 150-200 hours
- Active: 50-80 hours
- Efficient + Trading: 30-50 hours

---

## Conclusion

The military zombie key drop system on Outpost 31 uses a **two-stage probability model** identical to police zombies:
1. **5% chance** the zombie has any key
2. **10% chance** (1 in 10) for each specific key within that pool

However, military farming presents unique challenges:
- **Tougher zombies** requiring more resources and time per kill
- **Dangerous zones** with high PvP risk
- **Lower spawn density** compared to civilian areas
- **Advanced keys only** - no overlap with police drops

Despite these challenges, military zombies are the **primary source** for Standard Keys 11-12, Premium Keys (101-103), and Special Keys (200-204), making them essential for accessing high-tier keycard rooms.

**Key Takeaway**: Budget ~20 kills per key drop, prepare for combat, and use military farming as part of a comprehensive strategy that includes quests and trading. The advanced keys are worth the effort for the rewards they unlock.

---

*Document Version: 1.0*  
*Last Updated: January 19, 2026*  
*Data Source: [cfgspawnabletypes.xml](s:\servers\Outpost_31_Dev\mpmissions\empty.deerisle\cfgspawnabletypes.xml)*
