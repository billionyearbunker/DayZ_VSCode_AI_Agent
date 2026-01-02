# DayZ Custom Weapon Mechanics

**Subject:** GameMechanics.Combat.Weapons  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding ballistics, weapon handling, maintenance, and tactical engagement.

## 1. Core Concept Overview

DayZ uses a complex ballistics simulation rather than "hitscan" mechanics. Every bullet is a physical object affected by velocity, gravity (drop), air resistance, and penetration.

### The Damage Triad

- **Health Damage:** Reduces the target's HP. If HP = 0, target dies.
- **Shock Damage:** Reduces the target's Consciousness. If Shock = 0, target falls Unconscious (Uncon).
  - **Critical Logic:** High-caliber weapons often knock a player Uncon before killing them. The agent must verify the kill (Double Tap) or restrain the target.
- **Bleed Damage:** Percentage chance per hit to open a "Cut". Requires bandaging.

## 2. Weapon Classes & Caliber Hierarchy

The "Tier" of a weapon is generally defined by its Caliber and Fire Rate.

### 2.1. Civilian / Low Tier

- **Calibers:** .22 LR, .380 ACP, 9x19mm (Pistols), 12ga (Double barrels).
- **Characteristics:** High availability, low recoil, low noise.
- **Usage:** Self-defense against Infected. Ineffective against armored players (Plate Carriers) beyond 10m.
- **Key Weapons:** MKII (Best zombie killer, integral suppressor), IJ-70, BK-18, BK-43.

### 2.2. Mid-Tier (Police/Farm)

- **Calibers:** .357 Magnum, 9x19mm (SMGs), Buckshot.
- **Characteristics:** Capable of inflicting heavy Shock damage or rapid fire.
- **Key Weapons:** SG5-K (MP5), Repeater Carbine, Python, BK-133 (Pump Shotgun).
- **Note:** .357 has very high Shock damage—good for knocking players out.

### 2.3. High-Tier (Military)

- **Calibers:** 5.56x45mm, 5.45x39mm, 7.62x39mm.
- **Characteristics:** Select-fire (Semi/Auto), high magazine capacity (30-60 rnds), modular attachments.
- **Key Weapons:** M4-A1, KAM (AKM), KA-74, AUR (Aug).
- **Armor Pen:** These rounds can penetrate soft armor but require multiple hits to break Plate Carriers.

### 2.4. End-Game (Sniper/Battle Rifle)

- **Calibers:** .308 Win, 7.62x54mmR.
- **Characteristics:** Extreme range (800m+), massive Shock/Health damage.
- **Key Weapons:** Tundra, Mosin, Blaze, SVD (VSD), FAL (LAR).
- **Lethality:** Usually a guaranteed Uncon or Kill on a chest hit, regardless of armor (distance dependent).

## 3. Ballistics & Aiming Physics

### 3.1. Zeroing & Bullet Drop

- **Mechanic:** Bullets drop over distance.
- **Zeroing (PgUp/PgDown):** Adjusts the scope angle to compensate for drop at a specific distance.
  - **Example:** If target is 400m away, set Zero to 400. Aim center mass.
  - **If Zero is 100:** You must aim above the target.
- **Rangefinding:** Use a Rangefinder or the markings on the PSO-1 or Hunting Scope (Stadiametric rangefinding) to estimate distance.

### 3.2. Sway & Stamina

- **Weapon Sway:** Your aim moves naturally in a figure-eight pattern.
- **Stamina Impact:** Low stamina = Heavy Sway.
- **Hold Breath:** Holding Left Ctrl (default) steadies aim but consumes Stamina rapidly.
- **Stance:** Prone provides the least sway; Standing provides the most.

### 3.3. Recoil

Weapons have both vertical and horizontal recoil.

**Agent Logic:** Do not "Full Auto" at ranges > 20m. Use Semi-Auto or Short Bursts to maintain accuracy.

## 4. Weapon State Machine (Reloading & Jamming)

Unlike arcade shooters, DayZ weapons have complex internal states.

### 4.1. The Magazine Logic

**Magazines are items:** You do not just "have ammo." You must physically hold a magazine in your hand and combine it with loose ammo to fill it.

**Reload Action (R Key):**
- **Tap R:** Cycles the bolt/slide (ejects round, chambers next).
- **Hold R:** Swaps current magazine with a full one from inventory.
- **Double Tap R:** No function (unlike some games).

### 4.2. Chambering

Weapons can hold 1 round in the chamber + X in the magazine.

If a gun is empty, inserting a mag does not make it ready to fire. You must rack the slide/bolt (Tap R or Left Click) to chamber a round.

### 4.3. Jamming Mechanics

- **Trigger:** Weapon Condition (Damaged/Badly Damaged) + Quality of Ammo + Overheating.
- **Event:** Gun makes a "Click" sound. Slide locks halfway.

**Resolution:**
1. Hold Right Click (Aim).
2. Tap R to clear the jam (Player hits the gun/cycles bolt).
3. Weapon is ready to fire again.

## 5. Maintenance & Durability

Weapons degrade with use. A "Ruined" weapon cannot be fired or repaired.

### 5.1. Cleaning

- **Tool:** Weapon Cleaning Kit.
- **Logic:** Repairs weapon from "Badly Damaged" -> "Damaged" -> "Worn".
- **Limit:** Cannot repair to "Pristine". Cannot repair "Ruined".
- **Agent Priority:** Always keep weapons at "Worn" or better to prevent jamming.

### 5.2. Suppressor Durability

- **Plastic Bottle Suppressor:** Lasts ~3 shots.
- **Standard Suppressor:** Lasts ~2–3 magazines.
- **Consequence:** If a suppressor becomes "Ruined" while attached, it destroys the bullet's accuracy and cannot be removed (stuck). It must be maintained before it ruins.

## 6. Attachments Logic

- **Muzzle:** Reduces noise (Suppressor) or Recoil (Compensator).

**Optics:**
- **Red Dot (Baraka/Combat):** Close range (1x).
- **Magnified (ACOG/PSO-1):** Mid range (4x).
- **High Power (Hunting Scope):** Long range (12x).
- **Night Vision:** Some scopes accept NV capabilities; others block NV goggles.

- **Handguard/Buttstock:** Higher tier variants (Magpul/CQB) reduce recoil and sway and increase ergonomics (aim speed).

## 7. Damage Handling & Penetration

### 7.1. Wall Banging

- **Mechanic:** Bullets penetrate wood, thin metal, and doors.
- **Caliber Factor:** .308 and 7.62x54 have high penetration. 9mm has almost zero.
- **Damage Reduction:** Passing through an object reduces the bullet's damage by ~50% or more depending on material thickness.

### 7.2. Armor System

- **Stab Vest:** Stops melee/infected, weak vs bullets.
- **Press/Police Vest:** Stops pistol/shotgun/low-tier rifles.
- **Plate Carrier:** The Gold Standard. Can absorb 2–3 high-caliber rifle shots before the wearer takes fatal health damage (though they will likely take heavy Shock/Uncon damage).

## 8. Agent Logic: Combat Troubleshooting

**Problem:** "I pulled the trigger, heard a click, but the gun is pristine."
- **Cause:** The magazine is empty, OR you inserted a mag but didn't chamber a round.
- **Fix:** Press R to rack the slide.

**Problem:** "I am shooting the enemy but hitting the windowsill in front of me."
- **Cause:** Height Over Bore. The scope is 2 inches higher than the barrel. At extremely close range, the reticle shows clear, but the barrel is blocked.
- **Fix:** Aim slightly higher or stand up.

**Problem:** "I shot him with a Mosin, he fell down, I stopped shooting, then he got up and killed me."
- **Cause:** He was Unconscious, not dead.
- **Fix:** Approach body. If "Red Dot" appears (Survivor), he is alive. If distinct position (arm twisted/flat) or "Check Pulse" option is available, verify. Always double tap.

## Actionable Summary for Agent

The Agent must treat ammo management as a two-step process (Fill Mag -> Load Gun). In combat, the Agent must distinguish between an enemy falling Unconscious (legs fold, slump) vs Dead (ragdoll). The Agent must prioritize finding a Weapon Cleaning Kit, as a jammed gun is a death sentence. For long-range engagement, correct Zeroing is mandatory; for close range, hip-fire (un-aimed) is often faster and safer than ADS (Aim Down Sights).