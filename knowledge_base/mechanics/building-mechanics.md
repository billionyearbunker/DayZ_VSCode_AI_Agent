# DayZ Vanilla Base Building Mechanics

**Subject:** GameMechanics.Environment.Construction  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding territory control, structural defense, resource gathering, and persistence maintenance.

## 1. Core Concept Overview

Base building in DayZ is modular. Players do not place pre-fabricated buildings; they construct components (Walls, Gates, Towers) sequentially.

### Key Directives

- **Persistence:** Bases are persistent (save across server restarts).
- **Decay (Despawn):** Without interaction or a Flag Pole, base objects despawn after 45 days (default vanilla setting).
- **Territory:** Building allows players to secure loot, vehicles, and a safe logout zone.

## 2. Tool & Material Hierarchy

The Agent must acquire specific tools before attempting construction. The "Tech Tree" is gated by tool availability.

### 2.1. The "Must-Have" Tool Kit

| Tool                 | Function                                | Criticality                         |
|----------------------|-----------------------------------------|-------------------------------------|
| Shovel / Pickaxe / Hoe | Digging foundations (placing logs).     | High (Cannot start without one).    |
| Hatchet / Axe        | Chopping trees for Logs.                | High.                               |
| Hammer / Hatchet     | Driving nails (building frames/walls).  | High.                               |
| Handsaw / Hacksaw    | Converting Logs to Planks.              | High (Major bottleneck).            |
| Pliers               | Creating Gates (wiring) and Barbed Wire.| Medium (Required for security).     |
| Sharpening Stone     | Maintaining tool durability.            | High.                               |

### 2.2. Raw Materials

- **Log:** Cut from large trees. Heavy (can only carry 1 or 2). Used for Pillars/Foundations.
- **Plank:** Crafted from Logs (1 Log = 4 Planks). Used for Frames and Coverings.
- **Nails:** Looted in boxes (Industrial/Garages). Consumed in quantity (approx 20–35 per wall).
- **Sheet Metal:** Industrial loot. Alternative to wood planks (higher durability).
- **Metal Wire:** Industrial loot. Required for Gates.
- **Combination Lock:** Required to secure a Gate.

## 3. The Fence (Wall) Construction Loop

The Fence is the fundamental unit of base building. The Agent uses the following State Machine to construct it.

### Phase 1: Planning

- **Craft Kit:** Combine Rope + 2 Short Sticks = Fence Kit.
- **Placement:** Equip Kit. Choose location.
- **Logic:** Must be flat ground. Use Scroll Wheel to rotate.
- **Result:** A white "ghost" outline appears.

### Phase 2: Foundation

- **Resource:** Drag 2 Logs to the Fence Kit inventory.
- **Action:** Equip Shovel/Pickaxe. Look at Logs -> "Build Base".
- **Result:** Two vertical pillars stand up. The Kit is returned to the ground (can be reused).

### Phase 3: Framing (The Skeleton)

**Resource:** Drag Planks and Nails to the Fence inventory.

**Action:** Equip Hammer/Hatchet.
- "Build Lower Frame" (Requires 4 Planks, 8 Nails).
- "Build Upper Frame" (Requires 4 Planks, 8 Nails).

**Result:** A see-through wooden skeleton. Players can walk through it unless fully paneled.

### Phase 4: Cladding (The Defense)

- **Resource:** More Planks (or Sheet Metal) and Nails.
- **Action:** Equip Hammer/Hatchet.
  - "Build Wooden Wall (Lower)" / "Build Wooden Wall (Upper)".
- **Result:** A solid wall. Blocks vision and movement.

## 4. Gates & Security Logic

A Wall blocks everyone (including the owner). To enter, it must be a Gate.

### 4.1. Gate Transformation

- **Prerequisite:** A completed Fence Frame (cladding optional but recommended).
- **Resource:** Metal Wire.
- **Tool:** Pliers.
- **Action:** Drag Wire to Fence inventory. Equip Pliers -> "Build Gate".
- **Result:** The entire wall section becomes a hinged door.

### 4.2. Locking Mechanism

- **Item:** Combination Lock (3-Dial or 4-Dial).
- **Action:** Attach Lock to the Gate's inventory slot.
- **State:** The Gate is now LOCKED. It cannot be opened without entering the code.

**Agent Strategy:**
- **3-Dial Lock (Red):** 1,000 combinations. Can be "brute forced" by a raider in ~15 minutes. Insecure.
- **4-Dial Lock (Cyan):** 10,000 combinations. Takes ~2.5 hours to brute force. Secure.

## 5. The Watchtower (Verticality)

Watchtowers allow shooting over walls and scouting. They function similarly to fences but have 3 Levels.

- **Kit:** Rope + 4 Short Sticks = Watchtower Kit.

**Structure:**
- **Level 1:** Frames, Walls, Stairs, Roof.
- **Level 2/3:** Same as Level 1 but built on top.

- **Resource Cost:** Extremely high. Requires roughly 4x the wood of a Fence.
- **Tactical Value:** Allows the Agent to see over high walls. Often used as a sniper nest.

## 6. Base Persistence: The Flag Pole

This is the most critical component for long-term survival logic.

- **Problem:** Server cleanup deletes items after 45 days (or 14 days for buried loot).
- **Solution:** The Flag Pole.

**Radius:** Maintains all items within a 60-meter radius.

**Mechanism:**
- The flag slowly lowers over 45 days.
- **Refresher:** The Agent must "Raise Flag" periodically. This resets the despawn timers for all items in the radius to maximum.

**Construction:** Requires a Sledgehammer (to place the base) + Logs + stones + Metal Wire + Rope + 60 Nails.

## 7. Raiding & Dismantling Logic (Attack & Defense)

The Agent must distinguish between "Soft Side" and "Hard Side."

### 7.1. Dismantling (Soft Side/Inside)

- **Concept:** If you are standing inside the base (the side with the visible frame/planks), you can take it apart.
- **Tool:** Hatchet or Crowbar.
- **Action:** "Dismantle Wall".
- **Yield:** Returns most materials (Planks/Logs/Nails).

**Security Logic:** If a raider boosts over your wall, they can dismantle your exit gate from the inside out.  
**Design Guideline:** Use Barbed Wire on top of walls to prevent boosting.

### 7.2. Destruction (Hard Side/Outside)

**Concept:** From the outside, tools do not work. You must use brute force.

**Explosives:**
- **Plastic Explosive (C4):** The most efficient. ~2 charges destroy a wall.
- **Grenades:** Requires ~6–12 grenades per wall section.
- **Improvised Explosive Device (IED):** Crafted with Protective Case + Explosives.

**Bullets:**
- It takes thousands of rounds to break a wall. Generally inefficient.

**Melee:**
- Technically possible but takes hundreds of hits and multiple tools. (Often disabled on community servers).

## 8. Electricity & Utilities

Bases can be powered for lighting and utility.

- **Generator:** Uses Gasoline + Spark Plug.
- **Cable Reel:** Connects Generator to devices.
- **Construction Light:** Provides massive floodlighting for night defense.
- **Xmas Lights:** Can be strung on tents/fences for low-light ambiance.
- **Battery Charger:** Used to recharge 9V and Car Batteries using the Generator.

## 9. Agent Logic: Construction Strategy

### Location Choice

- **Existing Building:** Boarding up a Barn or Church is cheaper (fewer walls needed) but obvious to raiders.
- **Woods:** Harder to find, but requires building 4 walls (more resources).

### Airlock Design

- **Rule:** Never have a single door leading to loot.
- **Design:** Outer Gate -> Small "Hallway" -> Inner Gate.
- **Logic:** Open Outer Gate -> Close it -> Open Inner Gate. This prevents players from rushing in while you enter.

### Storage

- **Tents (Car/Large/Medium):** High capacity, easily movable.
- **Barrels:** Waterproof, 150 slots. Must be open to access.
- **Wooden Crates:** 50 slots. Crafted (Planks + Nails). Can be Buried (lifespan 14 days) or stored in water to hide them.

## Actionable Summary for Agent

Building is a resource sink. The Agent should not commence building until a Sharpening Stone (to fix the Axe/Hatchet) and a Box of Nails are secured. The priority build order is: Storage Box (Buried) -> Gate (Airlock) -> Walls -> Flag Pole. Always build a 4-Dial Lock; 3-Dial locks are essentially unlocked doors to experienced players.
