# DayZ Vanilla Hunting Mechanics

**Subject:** GameMechanics.Survival.Hunting  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding tracking, engaging, and harvesting wildlife.

## 1. Core Concept Overview

Hunting is the primary source of high-calorie food and crafting materials (Leather, Bones, Guts). Unlike fishing, hunting involves dynamic AI targets that can flee or counter-attack.

### Target Classification

- **Passive (Prey):** Flee upon detection. (Deer, Cow, Pig, Sheep, Goat, Chicken, Rabbit).
- **Aggressive (Predator):** Attack upon detection. (Wolf, Bear).

### AI Detection Logic

DayZ animal AI operates on two main sensors:

- **Visual:** Cone of vision. Camouflage clothing reduces detection radius slightly, but breaking Line of Sight (LoS) is more effective.
- **Audio:** Footsteps, gunshots, and environmental noise. Animals have distinct hearing thresholds.

**Note:** Wind direction/Scent is not a primary factor in Vanilla DayZ AI detection (unlike modded servers), though players often roleplay it. Noise and Movement are the dominant variables.

## 2. Equipment & Ballistics Data

### 2.1. Weapon Classes

Success depends on matching the caliber to the target size to ensure a clean kill without ruining the meat (excessive damage to the body can lower yield in some simulations, but primarily the goal is to prevent the animal from fleeing).

**Small Game (Chicken/Rabbit):**
- **Ideal:** .22 LR, Melee, or Improvised Bow (if available/modded).
- **Result:** One-shot kill.

**Medium Game (Sheep/Goat/Pig/Deer):**
- **Ideal:** 5.56x45mm, 7.62x39mm, .357, Buckshot.
- **Minimum:** .308 or 7.62x54mm for guaranteed one-shot drops.

**Large Game (Cow/Bear/Elk):**
- **Ideal:** .308 Win (Tundra/Savanna/FAL), 7.62x54mm (Mosin/SVD), or 12ga Slug.
- **Requirement:** High "Shock" damage is needed to knock the animal unconscious if the health damage doesn't kill it instantly.

### 2.2. Essential Gear

- **Knife:** Mandatory for harvesting. (Hunting Knife, Combat Knife, Stone Knife).
- **Gloves:** Mandatory to prevent "Bloody Hands" status.
- **Rangefinder (Optional):** Highly valuable for shots over 200m to adjust Zeroing.

## 3. The Hunting Loop (Logic Flow)

This process describes the state machine for the player action ActionHunting.

### Phase 1: Detection (The Search)

**Audio Scan:** Stop moving and listen.
- **Cues:** Elk bugle (high pitch scream), Deer grunt, Rooster crow, Wolf howl.
- **Logic:** Sound direction indicates target vector.

**Visual Scan:** Scan forest edges and open fields.
- **Sign:** Animals spawn in groups (herds) usually. If one is spotted, others are nearby.

### Phase 2: The Stalk (Approach)

- **Stance:** Crouch (Ctrl) or Prone.
- **Movement:** Slow movement reduces noise.
  - **Sneakers/Wrappings:** Quietest.
  - **Boots:** Louder.
- **Threshold:** The "Flee Radius" is typically ~30–50 meters for deer. The agent must stop approach before this threshold.

### Phase 3: Engagement (The Shot)

**Target Selection:** Identify the static target (stationary grazing is the best window).

**Zeroing:** Estimate distance. Adjust weapon Zeroing (PgUp/PgDown).

**Aim Point:**
- **Thoracic Cavity (Heart/Lungs):** Best balance of target size and lethality. Triggers heavy bleed or instant death.
- **Head:** Instant kill, but smaller target. High risk of miss.
- **Spine:** Paralyzes animal (Instant Unconscious), but ruins pelt quality often.

**Fire:** Execute shot.

### Phase 4: Post-Shot State

**Scenario A (Drop):** Animal falls instantly. Approach and confirm death.

**Scenario B (Run):** Animal flees.
- **Action:** Do not chase immediately. Watch direction.
- **Bleed Logic:** If hit in vital organs, the animal will bleed out within 100–300 meters. Track the body.

## 4. Harvesting & Processing

**Pre-requisite:** Dead Animal + Knife in hand.

### 4.1. The "Skin and Quarter" Action

- **Input:** Interact with body -> "Skin and Quarter".
- **Time:** Takes ~10–15 seconds. Player is locked in animation (Vulnerable).
- **Hygiene Trigger:** If player is NOT wearing gloves, hands become Bloody.
  - **Consequence:** If player eats/drinks with bloody hands -> Salmonella (High probability).
  - **Fix:** Wash hands at pump/pond or with water bottle before eating.

### 4.2. Harvest Items

| Item          | Utility  | Notes                                       |
|---------------|----------|---------------------------------------------|
| Meat (Steak)  | Food     | Must be cooked. High protein.               |
| Animal Fat    | Food     | Highest Calorie item in game. Do not eat raw. |
| Bones         | Crafting | Craft into Hooks, Knives, or Arrowheads.    |
| Guts          | Crafting | Craft into Rope.                            |
| Pelt/Hide     | Crafting | Must be tanned with Garden Lime to make Leather. |

## 5. Predator Logic (Wolf & Bear)

AI Agents must treat these targets differently. They are not prey; they are threats.

### Wolves

- **Behavior:** Pack mentality (3–6 wolves). They circle the player.
- **Agro Logic:** If the "Alpha" (often distinct color) is killed, the pack may flee, but usually, you must kill 70% of the pack to break their morale.
- **Defense:** Put back against a tree/wall. Do not run (they are faster). Melee is viable if ammo is low.

### Bears

- **Behavior:** Solitary or with cubs. Extremely high health and shock resistance.
- **Agro Logic:** Bears charge on sight.
- **The "Play Dead" Mechanic:** If a bear charges and you have not shot at it, you can go Prone and do not move. The bear may hit you once (knockout) and leave. If you shoot, the bear will kill you.
- **Kill Strategy:** Requires automatic fire (7.62x39 or higher) or multiple .308 headshots.

## 6. Nutrition & Cooking Values

Cooking removes disease risk and boosts caloric uptake.

### Nutritional Values

- **Animal Fat (Baked):** ~1400 Calories. (The "Gold Standard" of survival food).
- **Venison Steak (Baked):** ~400 Calories + High Water content.
- **Guts/Bones:** Do not eat.

### Cooking Methods

- **Stick:** Roast over open fire (Slow, 1 slot).
- **Cooking Pot:** Boil or Bake multiple slots at once (Efficient).
- **Smoking:** Requires building a Stone Oven or Smokehouse. Preserves food for weeks.

## 7. Agent Logic: Troubleshooting

**Problem:** "I shot the deer but it ran away and I can't find it."
- **Cause:** Non-vital hit (Leg/Gut) or caliber too small.
- **Fix:** Increase caliber size. Aim for the "front shoulder" area to hit heart/lungs.

**Problem:** "I am sick after eating cooked deer."
- **Cause:** You likely had bloody hands when you ate the food, or the food was burnt.
- **Fix:** Check glove status. Consume Charcoal Tablets or Multivitamins.

**Problem:** "I have a knife but can't skin the animal."
- **Cause:** Knife is ruined or you are desurced (lag).
- **Fix:** Check tool condition. Relog if tool is pristine but action fails.

## Actionable Summary for Agent

Hunting requires patience and audio awareness. The agent must prioritize finding Animal Fat as the highest ROI (Return on Investment) resource. Always wear gloves before skinning to avoid sickness loops. If a Bear is encountered, do not shoot unless armed with high-capacity automatic weaponry; otherwise, lay prone and submit.