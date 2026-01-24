# DayZ Vehicle Mechanics

**Subject:** GameMechanics.Transportation.Vehicles  
**Version Context:** DayZ Standalone (Vanilla 1.26+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding vehicle repair, maintenance, fluid logic, and physics handling.

## 1. Core Concept Overview

Vehicles in DayZ are server-authoritative physics objects. This means the server dictates the car's position, not the client. **Critical Warning:** High speeds (>80 km/h) in populated servers can cause "Desync," leading to the vehicle flying, flipping, or crashing into invisible obstacles.

### Vehicle Classes

- **Hatchback:** Gunter 2 (FWD, Fast).
- **Sedan:** Olga 24 (RWD, Tank-like).
- **4x4:** Ada 4x4 (AWD, Best off-road).
- **Rear-Engine Sedan:** Sarka 120 (RWD, Engine is in the back).
- **Heavy Truck:** M3S (6x6, Slow, massive cargo).
- **Military:** M1025 (Humvee - Automatic transmission, armored).

## 2. Assembly & Parts Hierarchy

A chassis found in the world is rarely functional. The Agent must source and install specific parts.

### 2.1. The "Ignition Trinity" (Required to Start)

Without these three items, the engine will not turn over.

**Spark Plug:**
- **Civilian Cars:** Standard Spark Plug.
- **Trucks (M3S):** Glow Plug.
- **Status:** If Ruined, the car makes no sound when turning the key.

**Battery:**
- **Civilian/Humvee:** Car Battery.
- **Trucks:** Truck Battery.
- **Logic:** Must have charge. If dead, must be charged with Battery Charger + Generator.

**Fuel:**
- **Civilian:** Gasoline.
- **Truck/Humvee:** Gasoline (Vanilla engines are unified on Gas currently, though M3S is visually a diesel truck, it takes Gas from pumps).

### 2.2. The Cooling System (Required to Move)

**Radiator:**
- **Installation:** Must be slot-locked into the engine bay.
- **Fluid:** Water.
- **Capacity:** Variable (approx 5.0L - 10.0L).
- **Critical Logic:** If you drive a car with an empty or un-filled radiator, the engine will start smoking in ~15 seconds and become Ruined (permanent death) in ~60 seconds.
- **Sarka 120 Exception:** The Radiator is in the rear engine bay, not the front.

### 2.3. Traction (Wheels)

Each vehicle requires 4 wheels (M3S needs 6 for full traction, but can move with fewer).

**Logic:** Ruined tires cause the vehicle to pull heavily to one side and significantly reduce max speed. Driving on a ruined tire eventually destroys the wheel rim.

## 3. Dashboard & Feedback Loop

The Agent must monitor the dashboard instrument cluster continuously.

### Indicators (Left to Right)

**RPM Gauge:**
- Keep the needle out of the Red Zone. Redlining damages the engine.

**Engine Light (Check Engine):**
- **Solid Yellow:** Engine is Damaged. Performance reduced.
- **Flashing Red:** Engine is failing. Stop immediately.
- **Solid Red:** Engine is Ruined. Vehicle is dead.

**Fuel Light:**
- **White:** Fuel > 10%.
- **Yellow/Red:** Low fuel.
- **Empty:** Engine cuts out.

## 4. Driving Physics & Gearbox Logic

### 4.1. Manual Transmission (Standard)

Most cars in DayZ are manual.

- **Gears:** Reverse (R), Neutral (N), 1, 2, 3, 4.
- **Upshifting:** Listen to engine pitch. Shift up when RPM is high.
- **Downshifting:** Shift down when climbing hills (Torque management).
- **Stalling:** If you stop the car while in Gear 1-4, the engine stalls. You must shift to Neutral to brake to a full stop without stalling.

### 4.2. Automatic Transmission (M1025 Humvee)

- **Gears:** R, N, D (Drive).
- **Logic:** Shift to D and hold acceleration. The gearbox handles the rest.

### 4.3. Terrain Interaction

- **Roads (Asphalt):** High traction, max speed.
- **Dirt/Grass:** Medium traction. Rear-Wheel Drive (RWD) cars like the Olga and Sarka will "fishtail" (spin out) if accelerated too hard while turning.
- **Mud:** Low traction. Requires low gear (1st or 2nd) to maintain momentum.

## 5. Maintenance & Repair Mechanics

Cars degrade from crashes and bullet fire.

### 5.1. Engine Repair

- **Tool:** Blowtorch (Note: Requires Gas Canister attached).
- **Target:** Look at the Engine block (open hood).
- **Action:** "Repair Engine".
- **Limit:** Can repair up to "Worn". Cannot fix "Ruined".
- **Pipe Wrench:** Used to repair the Engine in older patches, but now largely replaced by the Blowtorch/Epoxy for specific parts.

### 5.2. Body & Fuel Tank Repair

- **Tool:** Epoxy Putty.
- **Target:** Panels, Doors, and the Fuel Tank.
- **Leak Logic:** A damaged fuel tank leaks gas. Patching it with Epoxy stops the leak.

### 5.3. Tire Repair

- **Tool:** Tire Repair Kit.
- **Target:** Damaged (but not Ruined) tires.
- **Note:** A "Ruined" tire (shredded) cannot be repaired. It must be replaced.

## 6. Fluid Management

**Filling Fuel:**
- Look at Fuel Cap -> Action "Refill" (Requires Jerry Can / Bottle with Gas).
- Or stop at Gas Station pump -> Action "Fill Tank".

**Filling Radiator:**
- Must be done manually with a Bottle/Canister/Jerry Can containing Water.
- **Warning:** Do not pour Gasoline into the Radiator. This ruins the car.

## 7. The "Space Program" (Physics Glitches)

The Agent must be aware of "Game-Ending" physics anomalies.

**The Cause:** Server FPS drops or Network Lag. The client predicts the car is moving forward; the server disagrees; the physics engine resolves this by launching the car into the orbit.

### Prevention Logic

- If the car starts "bouncing" or "shaking" violently -> SLAM BRAKES. Turn off engine. Exit vehicle.
- Do not drive through "open" gates immediately. Wait 1 second for the server to register the gate is open.
- Avoid driving excessively fast (100km/h+) through major cities (Chernogorsk/Elektro) where rendering load is high.

## 8. Agent Logic: Troubleshooting

**Problem:** "I turn the key, the engine cranks (chug-chug-chug), but won't start."
- **Cause A:** No Fuel.
- **Cause B:** Spark Plug is Ruined.
- **Cause C:** Ruined Fuel Tank (Fuel leaked out immediately).

**Problem:** "I turn the key and hear a 'Click' sound only."
- **Cause:** Dead Battery.
- **Fix:** Find a new battery or charge the current one.

**Problem:** "White smoke is coming from the hood."
- **Cause:** Radiator water is low/empty.
- **Action:** STOP IMMEDIATELY. Turn off engine. If you continue, the engine will die in seconds. Refill radiator.

**Problem:** "The car is sliding on grass like it is on ice."
- **Cause:** You are driving a RWD car (Sarka/Olga) and accelerating too hard on a turn.
- **Fix:** Tap the W key (feather the throttle). Do not hold W while turning on grass.

## Actionable Summary for Agent

A vehicle is a liability until it is fully maintained. The Agent must prioritize finding a Radiator and Water before even attempting to start a found chassis. Blowtorches are high-value loot for vehicle owners as they are the only way to repair engine damage. When driving, the Agent should treat 50 km/h as the safe limit in towns to avoid lag-induced crashes.