# DayZ Vanilla Fishing Mechanics

**Subject:** GameMechanics.Survival.Fishing  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making and query resolution regarding fishing.

## 1. Core Concept Overview

Fishing is a survival mechanic divided into two distinct methods:

- **Active Fishing:** Requires a player to hold a rod and react to audio/visual cues. High yield, high calorie expenditure, high vulnerability.
- **Passive Fishing:** Uses deployed traps. Low yield per hour, zero calorie expenditure during wait time, low vulnerability.

### Water Salinity Logic

- **Freshwater:** Inland lakes, ponds, rivers.
- **Saltwater:** Ocean coastlines.
- **Significance:** Determines the loot table (Carp/Bitterlings vs. Mackerel/Sardines).
## 2. Equipment & Crafting Data

### 2.1. Rods

**Fishing Rod (Standard):**
- **Source:** Loot (Boats, Docks, Coast).
- **Durability:** High.
- **Pros:** Best durability, standard animation speed.

**Improvised Fishing Rod:**
- **Source:** Crafting only.
- **Recipe:** Long Stick + Rope.
- **Durability:** Low (prone to breaking after several catches).
- **Note:** Rope can be crafted from 6 + 6 Rags or Guts + Knife.

### 2.2. Hooks

**Fishing Hook (Metal):**
- **Source:** Loot (Industrial, Hunting, Boathouses) or attached to boonie hats.
- **Durability:** High (approx. 6–10 catches).

**Bone Fishing Hook:**
- **Source:** Crafting.
- **Recipe:** Bones + Knife.
- **Durability:** Medium (approx. 3–4 catches).

**Wooden Fishing Hook (1.26+):**
- **Source:** Crafting.
- **Recipe:** Small Stick + Knife.
- **Durability:** Low (1–2 catches, emergency use only).

### 2.3. Bait & Lures

**Earthworm (Bait):**
- **Acquisition:** Look at ground (Dirt/Grass) with a digging tool (Knife, Shovel, Hoe, Pickaxe) -> Action: "Dig up worms."
- **Usage:** Must be combined with a Hook to create Baited Hook.
- **Consumption:** Consumed on every catch (successful or failed).

**Fishing Lure (Jig) (1.26+):**
- **Acquisition:** Loot.
- **Usage:** Attaches directly to the hook slot. Replaces worms.
- **Durability:**
Durability: Degrades over time; does not require re-baiting after every catch.

3. The Active Fishing Loop (Logic Flow)
This process describes the state machine for the player action ActionFishingNew.

Preparation Phase:

Craft/Loot Rod.

Craft/Loot Hook.

Acquire Bait (Worm) or Lure.

Combine Worm + Hook = Baited Hook.

Attach Baited Hook (or Lure) to Rod.

Equip Rod in hands.

## 3. The Active Fishing Loop (Logic Flow)

This process describes the state machine for the player action ActionFishingNew.

### Preparation Phase

1. Craft/Loot Rod.
2. Craft/Loot Hook.
3. Acquire Bait (Worm) or Lure.
4. Combine Worm + Hook = Baited Hook.
5. Attach Baited Hook (or Lure) to Rod.
6. Equip Rod in hands.

### Action Phase (The Loop)

**Approach Water:**
- Stand at the edge of a valid water surface.

**Cast Line:**
- Hold Left Click (Action Button) to cast bobber.
- **State:** Waiting for Bite. (Animation: Idle holding rod).

**Monitoring:** The agent must monitor for Events.
- **Splash Sound (Minor):** "Glug" or small splash. **IGNORE.** (This is ambient noise/bait check).
- **Bobber Movement (Minor):** Bobber dips slightly. **IGNORE.**
- **Splash Sound (Major) + Taut Line:** Sharp splash sound, rod bends, distinct water agitation. **TRIGGER.**

### Hooking

- **Input:** Click/Hold Action Button immediately upon TRIGGER.
- **Timing:** The reaction window is approximately 1–2 seconds.

**Result Calculation (RNG):**
- **Success:** Fish or Item lands at player's feet. Hook durability -1. Bait consumed.
- **Failure:** "The fish got away." Bait lost. Hook durability -1.
- **Line Break:** "The line snapped." Hook and bait lost. Rod durability -1.

### Cycle Reset

1. Check Hook durability.
2. If using worms: Re-combine Worm + Hook.
3. Recipe: Netting + Metal Wire.

Bait: Optional (increases yield chance).

Catch: Carp (Fresh), Mackerel (Salt).

Placement: Requires deeper water than bottle trap.

Yield: Higher calorie fish than the bottle trap.

5. Loot Tables & Probabilities
Loot is determined by Water Type and RNG Roll.

5.1. Variables Affecting Success
## 4. Passive Fishing (Traps)

Traps function on a timer and do not require player presence.

### 4.1. Small Fish Trap

- **Recipe:** Plastic Bottle (Empty) + Knife.
- **Bait:** Optional (increases yield chance significantly).
- **Catch:** Bitterlings (Fresh), Sardines (Salt).
- **Placement:** In water (approx. knee deep).
- **Timer:** Checks for catch every ~10-15 minutes.

### 4.2. Fish Net Trap

- **Recipe:** Netting + Metal Wire.
- **Bait:** Optional (increases yield chance).
- **Catch:** Carp (Fresh), Mackerel (Salt).
- **Placement:** Requires deeper water than bottle trap.
- **Yield:**es: Low calorie.

Junk (The "Trash" Pool):

Wellies (Boots): Random condition.

Cooking Pot: Valuable utility item.
## 5. Loot Tables & Probabilities

Loot is determined by Water Type and RNG Roll.

### 5.1. Variables Affecting Success

- **Bait:** Mandatory for rods (unless using Lure). Without bait/lure, catch rate is 0%.
- **Time of Day:**
  - **Morning/Evening (Dawn/Dusk):** Catch chance multiplier ~1.5x.
  - **Mid-day/Night:** Standard base chance.
- **Weather:** Rain increases catch chance slightly.
- **Location:** No specific "hotspots" per lake, but depth matters for casting distance.

### 5.2. Catch Categories

**Freshwater (Inland):**
- **Carp:** High calorie, common.
- **Bitterlings:** Low calorie, mostly trap bait.

**Saltwater (Coast):**
- **Mackerel:** High calorie, safest food source (often safe to eat raw if immune system is 100%, but cooking is recommended).
- **Sardines:** Low calorie.

**Junk (The "Trash" Pool):**
- **Wellies (Boots):** Random condition.
- **Cooking Pot:** Valuable utility item.
- **Rusty Can / Waste:** Useless.
- **Probability:**have no knife for worms."

Fix: Look for stones on hiking trails -> Craft Stone Knife.

Problem: "I keep catching Wellies."

Cause: Bad RNG.

Fix: Move 10m down the shore (superstitious, but resets the server interaction point).

Actionable Summary for Agent:
To fish successfully, the agent requires a cutting tool (for worms/crafting) and a long stick + rope. The agent must prioritize Dawn/Dusk windows for maximum efficiency and must recognize the distinct "Splash/Bend" event trigger to avoid premature reeling.## 6. Nutritional Values & Processing

### Preparation

- **Fish cannot be eaten whole.**
## 7. Agent Logic: Troubleshooting & Edge Cases

**Problem:** "I am casting but the line immediately reels back in."
- **Cause:** Water is too shallow or the cast is hitting an obstacle (rocks/reeds).
- **Fix:** Reposition to deeper water or clear line of sight.

**Problem:** "I have a rod but no hook."
- **Fix:** Find a bush -> Gather Small Stick -> Combine with Knife -> Craft Wooden Hook (1.26+).

**Problem:** "I have no knife for worms."
- **Fix:** Look for stones on hiking trails -> Craft Stone Knife.

**Problem:** "I keep catching Wellies."
- **Cause:** Bad RNG.
- **Fix:** Move 10m down the shore (superstitious, but resets the server interaction point).

## Actionable Summary for Agent
