# DayZ Vanilla Base Raiding Mechanics

**Subject:** GameMechanics.Combat.Raiding  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding offensive siege tactics, structural durability calculations, and breach methodologies.

## 1. Core Concept Overview

Raiding is the act of breaching another player's secure perimeter to access their loot. In Vanilla DayZ, this is an intentional, high-cost, high-reward loop.

### The Golden Rule of Raiding

The Agent must calculate the Return on Investment (ROI).

- **Cost:** Explosives/Ammo + Time + Risk of counter-attack.
- **Reward:** Enemy loot.
- **Logic:** If the cost to enter exceeds the potential value of the loot, the raid is logically a failure, even if the wall is breached.

## 2. Wall Durability & Health Pools

Understanding the "HP" of base parts is critical for calculating ammo requirements.

### 2.1. Structural Health

Base parts have two health states: Health (Structure) and frame/covering integrity.

**Wood Wall:**
- **Frame:** High HP.
- **Planks (Covering):** Medium HP.

**Metal Wall:**
- **Sheet Metal:** Significantly higher HP than wood.

**Combination Lock:**
- Cannot be shot off or destroyed directly. The Gate itself must be destroyed to remove the lock (unless the code is guessed).

### 2.2. Damage Tiers

- **Pristine:** No visible damage.
- **Damaged:** Visual cracks/holes.
- **Destruction:** The covering (planks) falls off first, revealing the frame. Then the frame must be destroyed to allow passage.

## 3. Offensive Tools (The Breaching Kit)

Raiding is rarely done with melee in Vanilla (too slow/inefficient). Explosives and high-caliber fire are the standards.

### 3.1. Explosives (The Primary Method)

Explosives deal massive "Splash Damage," often hitting the frame and the wall simultaneously.

**Plastic Explosive (PE / C4):**
- **Trigger:** Requires Remote Detonator Unit.
- **Damage:** Highest structure damage.
- **Efficiency:** ~2 units usually clear a full wood wall.

**Claymore Mine:**
- **Trigger:** Remote Detonator Unit or Tripwire.
- **Directional:** Must face the wall. Deals slightly less structural damage than PE but covers a wider area.

**Grenades (Frag / EGD-5):**
- **Usage:** Must be dropped on the ground directly at the base of the wall.
- **Unpinning Logic:** To drop a live grenade: Equip -> Unpin (Left Click) -> Drop (G). Do not throw.
- **Quantity:** Requires ~6 per wood wall layer (12 for full breach of frame + wall).
- **Chain Reaction:** You can drop 5 grenades and unpin the 6th. The explosion of the 6th will detonate the other 5 simultaneously ("The Cluster Method").

**Improvised Explosive Device (IED):**
- **Recipe:** Protective Case + Electrical Repair Kit (Trigger) + Explosives (Grenades/Plastic Explosive inside).
- **Power:** Massive damage scaling based on what is packed inside.

### 3.2. Ballistics (The Brute Force Method)

Shooting a wall is loud, slow, and expensive, but viable if explosives are unavailable.

**Efficiency Tier List:**
- **Buckshot (12ga):** Surprisingly high structure damage per shell at point-blank range.
- **7.62x39mm (KAM):** Good damage, cheap ammo (Green box).
- **5.56x45mm (M4/AUR):** Expensive, but high fire rate allows fast breaching.
- **.308 / 7.62x54mm:** Too valuable. Do not waste sniper ammo on walls.

**Quantity:** Expect to fire 300–500 rounds to break a single wall section (Frame + Wall).

## 4. The "Boosting" Mechanic (Physics Exploits)

Before destroying a wall, the Agent should check if it can be bypassed physically.

- **Player Stacking:** One player crouches; the other jumps on their head. Allows vaulting over single-height walls.
- **Vehicle Boosting:** Parking a truck/car next to a wall to climb on the roof.
- **Item Boosting:** Dropping large items (Tires, Barrels) to create stairs. Note: Patched in many versions, but physics glitches sometimes allow it.

**Counter-Measure:** Defenders build "Double Stacked" walls (Fence on top of Fence) or place Barbed Wire on the top slot.

## 5. Code Breaking (Social Engineering)

**3-Dial Locks (Red):**
- **Combinations:** 000 to 999.
- **Time to Crack:** ~10–15 minutes of scrolling.
- **Agent Strategy:** Always attempt to "Cycle" a 3-dial lock before wasting explosives.

**4-Dial Locks (Cyan):**
- **Combinations:** 0000 to 9999.
- **Time to Crack:** ~2.5 hours.
- **Agent Strategy:** Do not attempt unless you have multiple agents rotating shifts.

**Prediction Logic:** Humans are predictable. Try these codes first:
- 1990 - 2005 (Birth years)
- 6969, 0420, 6666, 1111, 1234.

## 6. Dismantling (The "Soft Side")

If the Agent manages to enter the base (via boosting or a window left open), they are on the "Soft Side."

- **Tool:** Hatchet, Crowbar, or Hammer.
- **Action:** Look at the frame/wall -> "Dismantle".
- **Speed:** Very fast (10 seconds).
- **Noise:** Quiet (comparable to chopping wood).
- **Result:** The wall deconstructs into lootable materials.

**Note:** You cannot dismantle a gate if the lock is attached. You must saw off the lock (Hacksaw) or destroy the gate first.

## 7. Watchtower & Tent Raiding

- **Tents:** Tents cannot be locked. If you reach the tent, you own the loot. Tents can be destroyed by cutting/shooting to ruin the items inside (Scorched Earth tactic).
- **Barrels/Crates:** Cannot be locked.
- **Watchtowers:** Usually only 3 walls. The 4th side (stairs) is often open.
- **Weak Point:** Attack the bottom level walls. If the bottom supports break, the upper levels do NOT collapse (floating physics), but access is cut off.

## 8. Agent Logic: The Raiding Algorithm

### Phase 1: Recon

**Scout:** Observe base for 10 minutes. Look for active players (smoke from chimney, movement).

**Scan:** Use Binoculars. Identify:
- Is it Wood or Metal? (Metal = 2x Explosives).
- Are there 3-Dial locks?
- Is there a window open?
- Are there gaps in the wall (terrain clipping)?

### Phase 2: Breach

**Selection:** Choose the weakest point (usually a back wall, not the main gate which might be an airlock).

**Execution:**
1. Place Explosive.
2. Retreat to cover.
3. Detonate.
4. **Wait:** Wait 30 seconds for defenders to peek.
5. Rush through breach.

### Phase 3: Loot & Scoot

**Priority:** Do not take everything.

**Filter:** High Tier Guns > Ammo > Nails/Building Supplies > Food.

**Exit:** If you cannot carry it, Despawn it (drop it on the ground) to deny the enemy resources (Optional/Hostile logic).

## 9. Offline vs. Online Raiding

**Offline Raiding:** Attacking when owners are logged out. Safer, higher success rate. Considered "dishonorable" by some, but standard survival logic.

**Online Raiding:** Attacking while defenders are present.
- **Risk:** Extremely High. Defenders have "Peeker's Advantage."
- **Tactic:** Use Flashbangs and Smoke Grenades to blind defenders before pushing the breach.

## Actionable Summary for Agent

Raiding is an economic calculation. The Agent should never raid a "Freshie" base (shoreline shack) as the loot will not cover the cost of the explosives. Always check for "Soft Side" access (boosting/windows) before deploying explosives. When using grenades, use the Cluster Method (drop 5, unpin 1) to maximize burst damage and prevent defenders from reacting.
