# Quest Reward System - Probability Overview

## Overview

The Expansion Mod quest system on Outpost 31 uses a **random reward pool** mechanism. When a player completes a quest, they receive a randomly selected item (or items) from a predefined pool of 85 possible rewards. This document provides a detailed breakdown of how the system works and the probabilities for each reward.

---

## How the Reward System Works

### Core Mechanics

1. **Random Selection**: Each quest is configured with `"RandomReward": 1`, meaning the reward is randomly selected from the pool
2. **Equal Probability**: All 85 rewards have `"Chance": 1.0`, giving each item an equal probability of being selected
3. **Single Reward**: Most quests use `"RandomRewardAmount": 1`, meaning players receive **one random item** per quest completion
4. **No Player Choice**: With `"NeedToSelectReward": 0`, the system automatically selects the reward (players don't choose)
5. **Full Item Condition**: All rewards spawn at `"HealthPercent": 100` and `"DamagePercent": 0` (pristine condition)

### Quest Configuration Example

From [011-BlareBloodCollection-Quest.json](s:\servers\Outpost_31_Dev\profiles\ExpansionMod\Quests\Quests\011-BlareBloodCollection-Quest.json):

```json
"Rewards": {
    "value": [ /* 85 items */ ],
    "Count": 85
},
"NeedToSelectReward": 0,
"RandomReward": 1,
"RandomRewardAmount": 1
```

---

## Global Probability

Since all 85 rewards have equal weight (`Chance: 1.0`), the probability for any single item is:

**Per-Item Probability: 1/85 = 0.01176 (1.176%)**

---

## Reward Categories & Probabilities

### Category Breakdown

| Category                  | Item Count | Category Probability | Individual Item Probability |
|---------------------------|------------|----------------------|-----------------------------|
| **Ammunition Boxes**      | 16         | 18.82%               | 1.176% each                 |
| **Firearms**              | 18         | 21.18%               | 1.176% each                 |
| **Keycard Access Keys**   | 20         | 23.53%               | 1.176% each                 |
| **Tactical Knives**       | 15         | 17.65%               | 1.176% each                 |
| **Medical Supplies**      | 10         | 11.76%               | 1.176% each                 |
| **Food Items**            | 8          | 9.41%                | 1.176% each                 |
| **Total**                 | **85**     | **100%**             | —                           |

### What This Means

- **Keycard Keys** are the most common category you'll receive (nearly 1 in 4 rewards)
- **Firearms** are the second most common (about 1 in 5 rewards)
- **Food Items** are the rarest category (about 1 in 11 rewards)
- Any specific item (like a particular gun or knife) has a 1.176% chance of being rewarded

---

## Detailed Reward Tables

### 1. Ammunition Boxes (16 items, 18.82% category probability)

| Item Name                      | Quantity | Individual Probability | Notes              |
|--------------------------------|----------|------------------------|--------------------|
| AmmoBox_12gaSlug_10Rnd         | 2        | 1.176%                 | 12 Gauge Slug      |
| AmmoBox_00buck_10rnd           | 2        | 1.176%                 | 12 Gauge Buckshot  |
| AmmoBox_22_50Rnd               | 2        | 1.176%                 | .22 LR             |
| AmmoBox_308Win_20Rnd           | 2        | 1.176%                 | .308 Winchester    |
| AmmoBox_357_20Rnd              | 2        | 1.176%                 | .357 Magnum        |
| AmmoBox_380_35rnd              | 2        | 1.176%                 | .380 ACP           |
| AmmoBox_45ACP_25rnd            | 2        | 1.176%                 | .45 ACP            |
| AmmoBox_545x39_20Rnd           | 2        | 1.176%                 | 5.45x39mm          |
| AmmoBox_556x45_20Rnd           | 2        | 1.176%                 | 5.56x45mm NATO     |
| AmmoBox_762x39_20Rnd           | 2        | 1.176%                 | 7.62x39mm          |
| AmmoBox_762x54_20Rnd           | 2        | 1.176%                 | 7.62x54mmR         |
| AmmoBox_9x19_25rnd             | 2        | 1.176%                 | 9x19mm             |
| AmmoBox_9x39_20Rnd             | 2        | 1.176%                 | 9x39mm             |
| AmmoBox_9x39AP_20Rnd           | 2        | 1.176%                 | 9x39mm AP          |
| ExpansionAmmoBox_338_20Rnd     | 2        | 1.176%                 | .338 Lapua Magnum  |
| ExpansionAmmoBox_50BMG_10Rnd   | 2        | 1.176%                 | .50 BMG            |

**Note**: All ammo boxes award **2 boxes** of the specified ammunition type.

---

### 2. Firearms (18 items, 21.18% category probability)

| Item Name            | Individual Probability | Weapon Type        | Included Attachments                       |
|----------------------|------------------------|--------------------|--------------------------------------------|
| Expansion_M9         | 1.176%                 | Pistol             | Mag, Suppressor, TLR Light                 |
| Expansion_Longhorn   | 1.176%                 | Pistol/Revolver    | Pistol Optic                               |
| Expansion_G36        | 1.176%                 | Assault Rifle      | Mag, MRS Optic, Suppressor, Light          |
| Expansion_MPX        | 1.176%                 | SMG                | 50Rnd Mag, MRS Optic, Suppressor           |
| Expansion_MP5SD      | 1.176%                 | SMG                | 30Rnd Mag, Rail Attachment                 |
| Expansion_MP7        | 1.176%                 | SMG                | 40Rnd Mag, MRS Optic, Suppressor, Light    |
| Expansion_Kedr       | 1.176%                 | SMG                | 20Rnd Mag, Suppressor                      |
| Expansion_VityazSN   | 1.176%                 | SMG                | 30Rnd Mag, Rail, Stock, Suppressor         |
| Expansion_M16        | 1.176%                 | Assault Rifle      | STANAG Mag, HAMR Optic, Suppressor, Light  |
| Expansion_M1A        | 1.176%                 | Battle Rifle       | 20Rnd Mag, Rail, HAMR Optic, Suppressor    |
| Expansion_M14        | 1.176%                 | Battle Rifle       | 20Rnd Mag, Rail Attachment                 |
| Expansion_DT11       | 1.176%                 | Shotgun            | No attachments                             |
| Expansion_Kar98      | 1.176%                 | Bolt-Action Rifle  | Scope, Bayonet                             |
| Expansion_BenelliM4  | 1.176%                 | Shotgun            | MRS Optic, Light                           |
| Expansion_AWM        | 1.176%                 | Sniper Rifle       | 5Rnd Mag, PMII25 Optic                     |
| ExpansionLAW         | 1.176%                 | Launcher           | No attachments                             |

**Key Points**:
- All firearms spawn with **full attachments** pre-installed (magazines, optics, suppressors, lights where listed)
- Weapons are fully functional and ready to use immediately
- All weapons spawn in pristine condition (100% health, 0% damage)

---

### 3. Keycard Access Keys (20 items, 23.53% category probability)

| Item Name  | Individual Probability | Key Type     |
|------------|------------------------|--------------||
| CJ_Key1    | 1.176%                 | Standard Key |
| CJ_Key2    | 1.176%                 | Standard Key |
| CJ_Key3    | 1.176%                 | Standard Key |
| CJ_Key4    | 1.176%                 | Standard Key |
| CJ_Key5    | 1.176%                 | Standard Key |
| CJ_Key6    | 1.176%                 | Standard Key |
| CJ_Key7    | 1.176%                 | Standard Key |
| CJ_Key8    | 1.176%                 | Standard Key |
| CJ_Key9    | 1.176%                 | Standard Key |
| CJ_Key10   | 1.176%                 | Standard Key |
| CJ_Key11   | 1.176%                 | Standard Key |
| CJ_Key12   | 1.176%                 | Standard Key |
| CJ_Key101  | 1.176%                 | Premium Key  |
| CJ_Key102  | 1.176%                 | Premium Key  |
| CJ_Key103  | 1.176%                 | Premium Key  |
| CJ_Key200  | 1.176%                 | Special Key  |
| CJ_Key201  | 1.176%                 | Special Key  |
| CJ_Key202  | 1.176%                 | Special Key  |
| CJ_Key203  | 1.176%                 | Special Key  |
| CJ_Key204  | 1.176%                 | Special Key  |

**Note**: These keys are used for accessing locked areas in the Keycard Rooms mod. Keys are the **single most common reward category** at 23.53%.

---

### 4. Tactical Knives (15 items, 17.65% category probability)

All knives are from the **Scara Knives Collection** mod.

| Item Name        | Individual Probability | Knife Style |
|------------------|------------------------||-------------|
| Scara_Karambit   | 1.176%                 | Karambit    |
| Scara_Butterfly  | 1.176%                 | Butterfly   |
| Scara_Huntsman   | 1.176%                 | Huntsman    |
| Scara_Classic    | 1.176%                 | Classic     |
| Scara_M9Bayonet  | 1.176%                 | M9 Bayonet  |
| Scara_Paracord   | 1.176%                 | Paracord    |
| Scara_Skeleton   | 1.176%                 | Skeleton    |
| Scara_Stiletto   | 1.176%                 | Stiletto    |
| Scara_Survival   | 1.176%                 | Survival    |
| Scara_Talon      | 1.176%                 | Talon       |
| Scara_Nomad      | 1.176%                 | Nomad       |
| Scara_Bowie      | 1.176%                 | Bowie       |
| Scara_Falchion   | 1.176%                 | Falchion    |
| Scara_Ursus      | 1.176%                 | Ursus       |
| Scara_Gut        | 1.176%                 | Gut         |

---

### 5. Medical Supplies (10 items, 11.76% category probability)

| Item Name                | Quantity | Individual Probability | Medical Type         |
|--------------------------|----------|------------------------|----------------------|
| BandageDressing          | 1        | 1.176%                 | Wound Care           |
| BloodBagIV               | 1        | 1.176%                 | Blood Transfusion    |
| BloodTestKit             | 1        | 1.176%                 | Diagnostic           |
| SalineBagIV              | 1        | 1.176%                 | Hydration/Volume     |
| Epinephrine              | 1        | 1.176%                 | Emergency Injection  |
| Morphine                 | 1        | 1.176%                 | Pain Relief          |
| TetracyclineAntibiotics  | 1        | 1.176%                 | Infection Treatment  |
| VitaminBottle            | 1        | 1.176%                 | Immune Support       |
| CharcoalTablets          | 1        | 1.176%                 | Poison Treatment     |
| PurificationTablets      | 1        | 1.176%                 | Water Treatment      |

---

### 6. Food Items (8 items, 9.41% category probability)

| Item Name            | Quantity | Individual Probability | Food Type          |
|----------------------|----------|------------------------||--------------------|
| ExpansionMilkBottle  | 1        | 1.176%                 | Beverage           |
| ExpansionBread1      | 1        | 1.176%                 | Bread (Variant 1)  |
| ExpansionBread2      | 1        | 1.176%                 | Bread (Variant 2)  |
| ExpansionBread3      | 1        | 1.176%                 | Bread (Variant 3)  |
| ExpansionCheese1     | 1        | 1.176%                 | Cheese (Variant 1) |
| ExpansionCheese2     | 1        | 1.176%                 | Cheese (Variant 2) |
| ExpansionCheese3     | 1        | 1.176%                 | Cheese (Variant 3) |
| ExpansionCheese4     | 1        | 1.176%                 | Cheese (Variant 4) |

**Note**: Food items are the **rarest category** in the reward pool.

---

## Probability Analysis

### Cumulative Probabilities

If you complete **multiple quests**, your chances of receiving at least one item from a category increase:

| Quests Completed | Chance of ANY Firearm | Chance of SPECIFIC Firearm | Chance of ANY Key |
|------------------|------------------------|----------------------------|-------------------|
| 1 quest          | 21.18%                 | 1.176%                     | 23.53%            |
| 5 quests         | 69.79%                 | 5.71%                      | 73.72%            |
| 10 quests        | 89.82%                 | 11.10%                     | 91.44%            |
| 20 quests        | 98.68%                 | 20.93%                     | 98.99%            |
| 50 quests        | ~100%                  | 43.92%                     | ~100%             |

**Formula**: 1 - (1 - p)^n where p = probability, n = number of attempts

### Expected Value

On average, to receive:
- **Any specific item** (e.g., AWM sniper): ~85 quest completions
- **Any firearm**: ~5 quest completions
- **Any keycard key**: ~4 quest completions
- **All 18 firearms**: ~400+ quest completions (collector's problem)

---

## Quest Reward Strategy

### For Players Seeking Specific Items

1. **Target High-Value Quests**: Focus on quests that can be repeated or completed quickly
2. **Expect Variance**: With 85 items, you may get duplicates before completing a "set"
3. **Keys Are Common**: Expect to accumulate many keycard keys over time
4. **Food Is Rare**: Don't rely on quests for food—loot it instead

### For Players Seeking Firearms

- You have a **21.18% chance** (~1 in 5) of getting a firearm per quest
- All firearms come **fully kitted** with attachments
- Statistically, expect a gun every **5 quests** on average
- High-end snipers (AWM) are as common as pistols (M9)—no rarity tiers within firearms

### For Players Seeking Medical Supplies

- Medical items are relatively uncommon at **11.76%** (~1 in 9 quests)
- Each specific medical item (e.g., Blood Bag) has only a **1.176% chance**
- For reliable medical supplies, loot hospitals rather than relying on quests

---

## Technical Notes

### Quest Configuration Details

All quests using this reward system share these settings:

```json
"NeedToSelectReward": 0        // No player choice, automatic selection
"RandomReward": 1               // Random selection enabled
"RandomRewardAmount": 1         // Number of items awarded (typically 1)
"RewardsForGroupOwnerOnly": 1   // Only quest owner gets reward
"RewardBehavior": 0             // Standard behavior
"DeleteQuestItems": 1           // Quest items removed after turn-in
```

### Reward Item Properties

Every reward entry includes:
- **ClassName**: The item's class name in DayZ
- **Amount**: Quantity of that item (1 for most, 2 for ammo boxes)
- **Attachments**: Array of pre-attached items (magazines, optics, etc.)
- **DamagePercent**: Always 0 (pristine)
- **HealthPercent**: Always 100 (full health)
- **QuestID**: Always -1 (applies to all quests using this pool)
- **Chance**: Always 1.0 (equal weight)

---

## Comparison to Other Reward Systems

### This System vs. Tiered Rarity

**Traditional MMO Model** (Not Used Here):
- Common items: 50% chance
- Uncommon: 30% chance
- Rare: 15% chance
- Epic: 4.5% chance
- Legendary: 0.5% chance

**Outpost 31 Model** (Current):
- All items: 1.176% chance (equal)
- No rarity tiers
- Category frequency determined by pool size

### Advantages of Equal Weight System

✅ **Pros**:
- Simple and transparent
- High-value items (guns, medical) have same odds as low-value (keys, food)
- No "grind for weeks" for best items
- Encourages quest completion for all players

❌ **Cons**:
- No progression feeling (rare → epic → legendary)
- High variance (unlucky players may get many keys/food)
- Devalues high-tier weapons (AWM as common as M9)

---

## Frequently Asked Questions

### Q: Can I get the same reward twice in a row?
**A**: Yes. Each quest completion is an independent random selection. You could theoretically get the same item multiple times.

### Q: Do harder quests give better rewards?
**A**: No. All quests using this reward pool have the exact same odds, regardless of difficulty.

### Q: Can I trade duplicate rewards with other players?
**A**: Yes, if the items are tradeable in-game. This is a good strategy for getting items you want.

### Q: Are any items excluded from certain quests?
**A**: No. All 85 items are available in every quest that uses this reward template.

### Q: What happens if I complete a quest in a group?
**A**: With `"RewardsForGroupOwnerOnly": 1`, only the quest owner receives the reward, not group members.

---

## Conclusion

The Outpost 31 quest reward system uses a **flat probability model** where all 85 rewards have equal 1.176% chance of being awarded. While this means firearms and medical supplies are statistically harder to obtain than in tiered systems, it also means every quest completion has a chance at the best gear. The system rewards consistent play and encourages trading between players to fill gaps in their collections.

**Key Takeaway**: Complete more quests = more chances at rare items. With 85 equally-weighted rewards, variance is high, but persistence pays off.

---

*Document Version: 1.0*  
*Last Updated: January 19, 2026*  
*Data Source: [all-rewards-combined.json](s:\servers\Outpost_31_Dev\profiles\ExpansionMod\Quests\reward-templates\all-rewards-combined.json)*
