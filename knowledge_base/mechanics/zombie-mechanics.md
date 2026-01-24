# DayZ Vanilla Infected (Zombie) Mechanics

**Subject:** GameMechanics.Environment.Infected  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding Infected detection, avoidance, combat, and loot potential.

## 1. Core Concept Overview

The "Zombies" in DayZ are technically "Infected" humans. They are alive, not undead. This distinction matters because they can bleed, they can be knocked unconscious, and they are governed by biological sensory inputs (sight/sound) rather than supernatural tracking.

### Spawn Logic

- **Dynamic Spawning:** Infected spawn in a radius around the player (approx. 300m) as the player enters a zone.

**Zone Tiers:**
- **Coastal/Village:** Weakest variants (Civilian).
- **City/Industrial:** Medium difficulty.
- **Military:** Highest difficulty (Armored, high damage).

- **Persistence:** If a player leaves the area, Infected usually despawn to save server performance, unless interacting with a persistent object or player.

## 2. Sensory Systems (AI Detection)

The Infected AI operates on a Stealth/Noise threshold system.

### 2.1. Visual Detection

- **Daytime:** High visibility. Infected can spot a sprinting player at ~50–80 meters.
- **Nighttime:** Significantly reduced visibility. Players can crouch-walk within ~5–10 meters without detection if light sources (Glowsticks, Flashlights) are off.
- **Line of Sight (LoS):** Solid objects break aggro. Bushes provide "soft" cover (reduced visibility).

**Stance:**
- **Standing/Sprinting:** Max visibility.
- **Crouching:** Medium visibility.
- **Prone (Crawling):** Lowest visibility.

### 2.2. Audio Detection

**Footwear:**
- **Barefoot:** Quietest (but causes foot cuts).
- **Sneakers/Running Shoes:** Quiet.
- **Boots:** Loud.

- **Surface:** Walking on grass is quieter than walking on concrete/road.

**Gunshots:**
- **Unsuppressed:** Attracts all Infected within ~200–500m (Cascade Effect).
- **Suppressed:** Attracts only Infected within ~20–50m.

- **Rain:** Heavy rain dampens player noise, allowing closer stealth approach.

## 3. The Aggro Cycle (State Machine)

### State 1: Idle

- Infected stands still or shambles in a short loop.
- **Agent Action:** Safe to bypass at distance.

### State 2: Alert (Investigation)

- **Trigger:** Player steps too loud or enters peripheral vision.
- **Behavior:** Infected stops, screams/grunts, looks in direction of noise, and walks toward the noise source.
- **Agent Action:** Freeze movement immediately. If player freezes, Infected may lose interest and return to Idle.

### State 3: Aggro (Combat)

- **Trigger:** Visual confirmation or loud noise (Gunshot).
- **Behavior:** The "Scream" (calls nearby Infected) followed by a full sprint toward the player.
- **Note:** Infected can now vault fences and climb on low objects (hoods of cars). They cannot climb ladders.

## 4. Combat Mechanics

### 4.1. Melee Combat & Blocking

**CRITICAL LOGIC:** The most important mechanic for the agent to understand is Blocking.

- **The Block:** Hold Right Click (Raise Hands) + Walk Backwards (S key).
- **Effect:** Blocks 100% of light melee damage from Infected. Prevents cuts and health damage (Shock damage still applies slowly).
- **Strategy:** Block the combo attack -> Wait for Infected to pause -> Strike (Heavy Hit) -> Resume Block.

### 4.2. Stealth Kill

- **Requirement:** Player must be behind an unaware Infected.
- **Weapon:** Knife/Blade in hand.
- **Input:** Crouch walk close -> Raise hands -> Attack.
- **Result:** One-shot kill animation. Silent (does not alert others).

### 4.3. Damage Types

- **Headshots:** 1-Shot kill for most calibers and heavy melee.
- **Body Shots:** Inefficient. Requires multiple hits.
- **Knockout:** Heavy melee attacks can knock an Infected to the ground. They will stand up after 5–10 seconds. Double-tap to confirm kill.

## 5. Infected Variants & Data

| Variant                   | Health | Threat  | Notes                                                                                                                              |
|---------------------------|--------|---------|------------------------------------------------------------------------------------------------------------------------------------|
| Civilian (Casual)         | Low    | Low     | Basic drop table (Food, small tools).                                                                                              |
| Industrial (Hardhat/Vest) | Medium | Medium  | Slightly higher shock resistance.                                                                                                  |
| Runner                    | Low    | High    | Sprints faster and attacks more frequently.                                                                                        |
| Priest                    | Low    | Medium  | High chance to spawn impossible-to-find items.                                                                                     |
| Military (Camo)           | High   | Extreme | Often wear Helmets/Plate Carriers. Bullet resistant. Requires armor-piercing rounds or high-caliber headshots. High melee damage. |
| NBC (Yellow/Grey Suits)   | Medium | Special | Found in Gas Zones. Do not engage in melee (hitting them can release gas/disease).                                                |
| Screamer (Officer)        | Medium | High    | Their agro scream has a larger radius, pulling more zombies.                                                                       |

## 6. Loot Logic

Infected are "Walking Containers." Their loot inventory is based on their class.

- **Civilian:** Canned food, Sewing Kits, Knives, Batteries, Rope.
- **Paramedic/Doctor:** Bandages, Tetracycline, Codeine, Blood Test Kits.
- **Police:** 9mm ammo, Police vests, Handcuffs.
- **Military:** Ammo (5.56, 7.62, .45), Grenades, Magazines, Repair Kits.
- **Priest:** Low probability, but high chance for unique items (Teddy Bears, specialized clothing).

**Agent Strategy:** Looting Infected is a viable strategy early-game for food and knives when houses are empty.

## 7. Agent Logic: Survival Strategies & Edge Cases

### Strategy: The "Lock-In"

- If overwhelmed, run into a house and close the door.
- Infected cannot open doors (unless the server is modded).
- You can hit them through windows, but they can hit you back.

### Strategy: The "Car Top"

- Jump on top of a car/truck.
- **Warning:** In recent patches (1.20+), Infected can climb onto hoods. Roofs are safer, but not guaranteed.

### Safe Zone: Climb a Ladder

- Infected cannot climb ladders.

### Troubleshooting

**Problem:** "I hit the military zombie in the head but he didn't die."
- **Cause:** He is wearing a Ballistic Helmet.
- **Fix:** Switch to melee (blunt force bypasses ballistic resistance better) or shoot the Face (Hitbox is precise).

**Problem:** "I am bleeding after one hit."
- **Cause:** Infected have a high chance to cause a "Bleeding" status effect (simulating scratches/bites).
- **Fix:** Prioritize Blocking. Bandage immediately after combat.

### Logic Loop for Engagement

1. Can I stealth kill it? -> Yes -> Execute.
2. If No: Do I have a suppressor? -> Yes -> Headshot.
3. If No: Is it alone? -> Yes -> Melee (Block/Strike).
4. If No (Group): -> Evade/Sprint to break LoS or find a ladder.

## Actionable Summary for Agent

Infected are dangerous primarily in groups or when they trap the player in a corner. The Agent must master the Block Mechanic (Right Click + S) to survive melee encounters without taking damage. Stealth is always the preferred state; firing an unsuppressed weapon in a town is a "Death Spiral" action that attracts exponentially more threats. Prioritize killing Military infected for high-tier ammo loot.