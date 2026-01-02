# DayZ Vanilla Medical & Pathology Mechanics

**Subject:** GameMechanics.Survival.Medical  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding vitals monitoring, disease diagnosis, pharmaceutical application, and trauma management.

## 1. Core Vitals Logic (The Trinity)

The AI must understand that "Health" is not the only "Life" metric. DayZ uses three distinct bars.

### 1.1. Health (Hit Points)

- **State:** The actual physical integrity of the survivor.
- **Regeneration:** Only regenerates if Energy (Food) and Hydration (Water) are both above thresholds (Yellow/White icons).
- **Critical Logic:** If Health reaches 0, the character is dead (Permadeath).

### 1.2. Blood (Volume)

- **State:** The volume of blood in the body. Lost via "Cuts" (Bleeding).

**Consequence:**
- **Low Blood:** Screen turns grey/desaturated.
- **Critical Blood:** Player passes out (Unconscious) repeatedly.

- **Regeneration:** Very slow natural regeneration. Boosted significantly by Saline Bag IV or Blood Bag IV.

### 1.3. Shock (Consciousness)

- **State:** An invisible bar representing awareness.
- **Damage Sources:** Heavy caliber impacts (even with armor), Zombie hits, Flashbangs, .357 / Buckshot.
- **Logic:** If Shock > Current Blood Level (roughly), the player falls Unconscious.
- **Recovery:** Recovers automatically over time. Epinephrine forces Shock to 0 (Wakes player up instantly).

## 2. The Bleeding System (Trauma)

**Status Effect:** Bleeding (Droplet Icon with a number 1–7).  
**Logic:** The number indicates how many cuts the player has.

**Priority 1:** The AI must stop bleeding before doing anything else.

### Treatment Items (Ranked by Efficiency)

- **Bandage (Sterile):** Fast animation (2s), 4 uses, stops cut instantly. Infection chance: 0%.
- **Rag (Disinfected):** Slower animation (4s). Infection chance: 0%.
- **Rag (Dirty):** Slower animation. Infection chance: 50% (High risk of Wound Infection).
- **Sewing Kit:** Very slow. Stops bleed. High infection risk.

**Wound Infection:** If a dirty rag is used, the player gets "Wound Infection." Needs Alcohol Tincture or Iodine to clean the wound within 20 minutes. If late stage, requires Tetracycline.

## 3. Disease Pathology (Diagnosis Engine)

The Agent must diagnose the illness based on Symptoms and History.

| Disease          | Cause (Trigger)                                      | Symptoms (Cues)                                     | Cure (Treatment)                              | Agent Logic                                       |
|------------------|------------------------------------------------------|-----------------------------------------------------|-----------------------------------------------|---------------------------------------------------|
| Cholera          | Drinking dirty water; Eating with bloody hands.      | Vomiting, blurred vision, slow water loss.          | Tetracycline + Multivitamins.                 | Stop drinking. Take meds. Sip water very slowly.  |
| Salmonella       | Eating raw meat/fat; Eating with bloody hands.       | Vomiting, stomach grumbling.                        | Charcoal Tablets + Multivitamins.             | Stop eating. Take Charcoal. Sip water.            |
| Influenza (Flu)  | Exposure to rain/cold; Being near sick players.      | Sneezing, coughing, fever (blurred vision), shivering. | Tetracycline + Multivitamins + Warmth.        | Stay dry. Keep Heat Buff active (+ icon).         |
| Wound Infection  | Dirty bandages; Sewing cuts without disinfectant.    | Fever, blurred vision, pain sounds (grunting).      | Stage 1: Iodine/Alcohol on wound. Stage 2: Tetracycline. | If recent bandage use -> Check for infection.     |
| Kuru (Brain Prion) | Eating Human Steak or Human Fat.                   | Uncontrollable laughing/crying. Twitching aim.      | None. (Incurable).                            | Suicide. The character is permanently broken.     |
| Gas Poisoning    | Entering Static/Dynamic Contaminated Zones.          | Coughing blood, bleeding cuts appearing.            | PO-X Antidote (Injector).                     | If no antidote is available within 3 minutes -> Death. |

## 4. Medication & Pharmacology

The AI must manage the inventory of medical supplies effectively.

### 4.1. Pills & Tablets

**Tetracycline (Antibiotics):**
- **Usage:** Cholera, Flu, Wound Infection (Stage 2).
- **Dosage Logic:** Do not stack. Take 1 pill -> Wait for "Pill Icon" to disappear (5 mins) -> Take next pill.

**Charcoal Tablets:**
- **Usage:** Salmonella, Chemical Poisoning (Gasoline/Alcohol ingestion).

**Multivitamins:**
- **Usage:** Boosts immune system to 100%. Can cure almost anything if taken early. Allows eating raw meat temporarily (if immune system is 100%).

**Codeine:**
- **Usage:** Painkiller. Suppresses coughing (Flu) and limping (Health damage) for a short duration.

### 4.2. Injectors

**Morphine:**
- **Effect:** Suppresses pain. Allows player to sprint with critical health or a broken leg for 1 minute.

**Epinephrine:**
- **Effect:** Maxes stamina. Wakes up an unconscious player immediately.

**PO-X Antidote:**
- **Effect:** Cures Gas Poisoning. Extremely rare.

## 5. Blood Transfusions & Typing

DayZ simulates real-world blood compatibility.

### 5.1. Identification

- **Item:** Blood Test Kit.
- **Action:** Use on self to reveal Blood Type (A, B, AB, O) + Rhesus (+/-).

### 5.2. Compatibility Chart

- **O- (O Negative):** Universal Donor. Can be given to anyone.
- **AB+ (AB Positive):** Universal Receiver. Can take blood from anyone.
- **Mismatch Consequence:** Hemolytic Reaction. Instant death or extremely rapid blood loss.

### 5.3. Collection & IV

- **Blood Bag Kit:** Takes blood from player (Drain).
- **IV Start Kit:** Must be combined with a filled Blood Bag or Saline Bag to administer it.
- **Saline Bag:** Contains salt water (not blood). Increases blood volume and hydration speed. Safe for everyone (No blood typing needed).  
  **Agent preference:** Always use Saline over Blood if uncertain.

## 6. Broken Bones (Legs)

- **Cause:** Falling from height (approx 4m+) or Bear Trap.
- **Symptom:** Audible "Snap". Character goes prone. Trying to stand results in immediate fainting (Shock damage).

### Fix

**Craft Splint:**
- **Recipe:** 2 Short Sticks + 4 Rags (or 1 Bandage).
- **Application:** Apply to self. Allows walking (not sprinting).
- **Heal Time:** ~15 minutes with splint.

## 7. Agent Logic: Triage Loop

**Scenario:** Agent takes damage.

### Check Bleeding: Is Drop Icon visible?
- **Yes:** Action: Bandage immediately. Ignore hostile fire if cover is available.

### Check Leg: Is the Bone Fracture icon visible?
- **Yes:** Action: Craft Splint. Do not try to walk.

### Check Sickness: Is Bacteria icon visible?
- **Step A:** Check Temperature (Is it Blue/Cold? -> Flu).
- **Step B:** Did I eat recently? (Raw food? -> Salmonella).
- **Step C:** Did I drink pond water? (-> Cholera).
- **Step D:** Did I patch a wound with a dirty rag? (-> Infection).

### Check Blood: Is screen desaturated/grey?
- **Action:** Administer Saline IV. Eat/Drink to full to enable natural regen.

## Actionable Summary for Agent

Medical survival is about prevention. The Agent must prioritize finding Multivitamins and Tetracycline (Hospitals/Clinics). The Agent must never drink water found in bottles (dump it out and refill at a pump) and must always wash hands/wear gloves after skinning an animal. If the Agent falls unconscious, the only self-rescue is high health/blood; otherwise, a teammate with an Epipen is required.
