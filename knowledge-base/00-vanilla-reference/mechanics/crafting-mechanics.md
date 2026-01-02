# DayZ Vanilla Crafting Mechanics

**Subject:** GameMechanics.Interaction.Crafting  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding item combination, recipe trees, resource management, and base construction logic.

## 1. Core Concept Overview

Unlike many RPGs, DayZ does not have a dedicated crafting menu or UI window. Crafting is entirely Inventory-Based and Context-Sensitive.

### The Logic of "Combining"

- **Hand State:** Agent holds Item A in hands.
- **Drag Action:** Agent drags Item B (from inventory or vicinity) onto Item A.
- **Interaction:** The UI displays an action prompt (e.g., "Craft Fireplace").
- **Cycling Recipes:** If two items have multiple possible outcomes (e.g., Rags + Knife can make Rope OR Bandages), the Agent must press Left Click or F to Cycle Next Recipe before holding to craft.

## 2. The Survival "Golden Path" (Essential Recipes)

These are the high-priority recipes an Agent must know immediately upon spawning to ensure survival.

| Output Item       | Input A        | Input B                      | Utility                                              |
|-------------------|----------------|------------------------------|------------------------------------------------------|
| Stone Knife       | Small Stone    | Small Stone (or Rock surface) | Critical. Allows skinning, opening cans, cutting rags. |
| Rags              | Clothing       | Knife/Sharp Tool             | Medical (Bandage) or Crafting component.             |
| Hand Drill Kit    | Short Stick    | Bark (Dark/Oak)              | Fire starter. Replaces Matches/Lighter.              |
| Fireplace         | Short Stick    | Kindling (Bark/Paper/Rag)    | Basic heat source and cooking point.                 |
| Improvised Rope   | 6 Rags         | 6 Rags (Stack combined)      | Critical. Used for fishing rods, backpacks, and shelters. |
| Splint            | 2 Short Sticks | 4 Rags / 1 Bandage           | Fixes broken legs (allows walking).                  |
| Torch             | Long Stick     | Rags/Fat                     | Light source + Heat.                                 |

**Agent Logic:** If HasKnife == False, the primary directive is: Locate "Train Tracks" or "Hiking Trails" -> Search for Small Stones -> Craft Stone Knife.

## 3. Improvised Gear (Clothing & Storage)

When standard loot is scarce, the Agent must craft storage solutions to carry resources.

### 3.1. Storage Hierarchy

**Burlap Sack:** Found in sheds/industrial.

**Courier Bag (30 Slots):**
- **Recipe:** Burlap Sack + Rope.
- **Profile:** Low profile, decent capacity.

**Improvised Backpack (42 Slots):**
- **Recipe:** Courier Bag + 3 Short Sticks.
- **Profile:** Larger profile, high capacity. Can be deconstructed back to Courier Bag.

### 3.2. Stealth & Protection

**Improvised Hand/Foot Wrappings:**
- **Recipe:** 2 Rags (Interact to craft).
- **Utility:** Quieter footsteps than boots (Stealth). Prevents foot cuts if barefoot. Warmth is low.

**Ghillie Suit (Camouflage):**
- **Components:** Netting + Burlap Strips.
- **Paint:** Can be spray painted Green/Mossy.
- **Logic:** Offers high visual concealment but zero inventory space (replaces backpack).

## 4. Base Building Mechanics (Construction)

Base building is modular. It requires specific tools and raw resources (Logs, Planks, Nails).

### 4.1. The Tool Kit

To build a basic wall/gate, the Agent must possess:

- **Digging Tool:** Shovel, Pickaxe, or Hoe (to place logs).
- **Cutting Tool:** Hatchet or Axe (to chop logs).
- **Hammering Tool:** Hammer, Hatchet, or Meat Tenderizer.
- **Saw:** Handsaw or Hacksaw (to make planks).

### 4.2. Construction Loop (State Machine)

1. **Craft Kit:** Rope + 2 Short Sticks = Fence Kit.
2. **Placement:** Place Fence Kit ghost on flat ground.
3. **Foundation:** Attach 2 Logs to the kit -> Use Shovel -> "Build Base".
4. **Framing:** Attach Planks + Nails. Use Hammer -> "Build Lower Frame" / "Build Upper Frame".
5. **Cladding:** Attach more Planks + Nails. Use Hammer -> "Build Wood Wall".

### 4.3. Secure Gate Logic

- **Convert to Gate:** Requires Metal Wire. Attach wire to frame -> Use Pliers -> "Build Gate".
- **Locking:** Attach Combination Lock (3-dial or 4-dial) to the gate inventory.
- **Raid Logic:** Walls can be destroyed by explosives (Plastic Explosives, Grenades) or enormous amounts of gunfire. They cannot be destroyed by melee tools from the outside (unless the server allows it), but can be dismantled easily from the inside using a Hatchet.

## 5. Repair & Maintenance Logic

Items degrade (Pristine -> Worn -> Damaged -> Badly Damaged -> Ruined). **Rule:** Ruined items cannot be repaired. They must be maintained before they hit Ruined state.

### 5.1. Repair Kits

**Duct Tape:**
- The universal fixer. Repairs almost anything (Clothing, Backpacks, Tools, Bottles).
- **Note:** Cannot repair guns or specific ballistic vests in vanilla.

**Sewing Kit:**
- Repairs fabric clothing.
- **Infection Risk:** If you sew a cut on your body (instead of clothing), it causes wound infection.

**Leather Sewing Kit:**
- Repairs leather items (Boots, Vests, Dried Sacks).

**Epoxy Putty:**
- Repairs plastic (Helmets) and rigid vests (Plate Carrier).

**Whetstone:**
- Repairs knives and axes.

**Weapon Cleaning Kit:**
- Repairs firearms.

## 6. Resources & Harvesting

The Agent must understand where materials come from.

**Bark:**
- Use Knife on Tree.
- **Dark Bark:** For Fireplaces/Torches.
- **Light (Birch) Bark:** Only for Fireplaces (cannot be used for Tanning).

**Long Stick:**
- Cut Bush with Hands or Knife.

**Short Stick:**
- Split Long Stick OR Cut small bush.

**Planks:**
- Cut Log (from big tree) with Hacksaw/Handsaw.

**Stone:**
- Search "Stones" texture on ground.

## 7. Agent Logic: Troubleshooting

**Problem:** "I have the ingredients but no 'Craft' option appears."
- **Cause A:** One of the items is Ruined.
- **Cause B:** You are using the wrong tool interaction (e.g., trying to saw a log without putting the log on the ground first).
- **Cause C:** Inventory is full. Some crafting results (like a fireplace) drop to the ground if hands/bag are full.

**Problem:** "I made a fireplace but it won't start."
- **Cause A:** No fuel (Wood/Bark).
- **Cause B:** It is raining and the fireplace is not under a roof/tree.
- **Cause C:** Wind (High altitude).
- **Cause D:** No ignition source (Matches/Drill Kit).

**Problem:** "I can't put the backpack on."
- **Cause:** You are already wearing a backpack (or Ghillie Suit).

## Actionable Summary for Agent

Crafting is the bridge between "Looting" and "Surviving." The Agent must prioritize the Knife above all else, as it unlocks the ability to craft Fire, Rope, and Food. When managing inventory, the Agent should always carry Duct Tape (for general repairs) and a Sharpening Stone (to keep the knife functional). When attempting to craft, always check the vicinity (floor) if the result does not appear in the inventory.