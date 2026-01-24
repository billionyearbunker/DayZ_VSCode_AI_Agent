# Deer Isle Map Mechanics

**Subject:** GameWorld.Mod.DeerIsle  
**Version Context:** Deer Isle (Current Community Release / v5.x+)  
**Purpose:** Comprehensive logic guide for AI agent decision-making regarding navigation, lore-specific questlines (The Temple), unique environmental hazards, and archipelago survival strategies.

## 1. Core Concept & Geography Overview

Deer Isle is a 16km x 16km community map created by JohnMcLane. Unlike Chernarus (a continental landmass), Deer Isle is a massive Archipelago.

### Topography Logic:

- **Southern Coast (Spawns):** Stonington, Paris Island, Westbrook. Urban, high population, low-tier loot.
- **The Main Landmass:** Dense forests, rolling hills, mimicking Maine/New England terrain.
- **The North (The Arctic):** A separate biome in the far north. Requires high insulation.
- **The Swamp:** Massive wetland in the Southwest. Difficult navigation.
- **The Volcano:** Active geothermal zone.
- **Offshore Assets:** Oil Rigs and the Aircraft Carrier (Vityaz).

### Navigation Directive:

**Boats are Critical:** Unlike Chernarus, swimming is often fatal due to distance and water temperature. The Agent must prioritize acquiring a boat (if vehicle mods are active) or planning strict island-hopping routes to manage stamina.

## 2. The Quest System (The Temple & KMUC)

Deer Isle contains a scripted "End Game" dungeon crawl that is built into the map geometry. This is unique to Deer Isle and not found in Vanilla DayZ.

### 2.1. The Loot Keys (Security Cards)

Access to high-tier loot and the final zones requires physical keycards found in the world.

| Key Card | Location Logic | Access Target | Note |
|----------|---------------|---------------|------|
| Orange Card | Low Tier Police/Prison areas. | Security Doors in Police Stations. | Basic loot. |
| Yellow Card | Mid Tier Military/Industrial. | Security Doors in Military Outposts. | Better weapons/ammo. |
| Green Card | High Tier Military (Aircraft Carrier). | Area 42 (Volcano Base). | Required for progression. |
| Blue Card | Area 42 (Inside Green Room). | KMUC (Secret Underground). | The "End Game" key. |
| Red Card | Rare spawn (Helis/Toxic Zones). | High Value Armory. | Often server-dependent. |

### 2.2. The "Temple" (The Tikis)

There is a massive Mayan-style temple hidden on the map.

- **Mechanic:** The player must collect "Tikis" (Idols) scattered around the map.
- **The Altar:** Bringing the correct Tikis to the Altar trigger events (teleportation, loot drops, or opening the "Crypt").
- **Nighttime Requirement:** Many temple scripts only activate at Night (in-game time).

### 2.3. KMUC (Katahdin Military Underground Complex)

- **Location:** Buried deep beneath the mountains (Mount Katahdin).
- **Entry:** Requires the Blue Keycard and navigating a complex tunnel system.
- **Threat:** Usually populated with "Dark" areas requiring NVGs (Night Vision) and high-tier Infected.
- **Loot:** The best loot on the map spawns here.

## 3. Unique Biomes & Hazards

The Agent must recognize that Deer Isle has distinct biomes that require different loadouts.

### 3.1. The Swamp (Southwest)

- **Navigation:** Extremely difficult. Shallow water slows movement (high calorie burn).
- **Threat:** Leaches (if modded) or simply rapid hypothermia from being wet.
- **Flora:** Dense overhangs block sunlight and visibility.
- **Logic:** Avoid unless equipped with Waders or Waterproof Backpack (Drybag).

### 3.2. The Arctic (North)

- **Mechanic:** Ambient temperature drops drastically.
- **Requirement:** High Insulation clothing (Hunting Gear, Winter coats).
- **Loot:** High-tier military spawns are hidden in the ice caves and research outposts.

### 3.3. Area 42 (The Volcano)

- **Environment:** Ash particles in the air (visual obstruction).
- **Terrain:** Steep, rocky cliffs.
- **Hazards:** Lava zones (instant death/fire damage).
- **Lore:** This is a bio-weapon research facility. Expect heavy military presence (AI or Players).

## 4. Loot Progression Route

The standard "Chernarus Loop" (Northwest Airfield run) does not apply here.

### Deer Isle Progression Logic:

1. **Spawn (Stonington/Paris):** Gather food and Waterproof Bag.
2. **Island Hop:** Move to Old Arnold or Eastbrook.
3. **Military Gear:** Raid the Prison Island (Alcatraz) or small military checkpoints.
4. **The Swim (High Risk):** Swim or Boat to the Aircraft Carrier (Vityaz) in the Southeast.
   - **Reward:** Mid-to-High tier military gear.
   - **Risk:** No fresh water source on the carrier.
5. **The End Game:** Move North to Area 42 or the Temple once equipped with Keycards.

## 5. Custom Modded Entities (Common Pairings)

While Deer Isle is a map, it is almost always hosted with specific creature mods that the Agent must expect.

- **Blood Suckers:** Invisible/Camouflaged mutants often scripted to spawn in the Swamp or Underground.
  - **Counter:** Listen for the "Heavy Breathing" audio cue. They are visible in Thermal/NVG.
- **Wendigos/Yeti:** Often found in the Northern Arctic biome.

## 6. Survival Logistics Specific to Deer Isle

### 6.1. Water Scarcity

- **Islands:** Small islands often lack Water Pumps (Wells).
- **Solution:** The Agent must prioritize finding a Cooking Pot or Chlorine Tablets immediately. Pond water is the only option in 60% of the map.

### 6.2. Caves & Underground

Deer Isle has a massive, non-instanced cave system.

- **Agent Logic:** Never enter a cave without a light source (Glowstick/Headtorch) AND a backup battery. It is pitch black, and getting lost leads to starvation.

## 7. Agent Logic: Troubleshooting

**Problem:** "I am swimming to an oil rig and my health is dropping."

- **Cause:** You are cold (Wet + Windy Ocean).
- **Fix:** You cannot fix this while swimming. You must turn back or use Epinephrine to stamina-boost the rest of the way. Prevention: Use a Drybag to keep clothes dry, change immediately upon landing.

**Problem:** "I found a 'Tiki' idol. What do I do with it?"

- **Logic:** Do not drop it. It is a quest item. It takes up heavy inventory space (usually 10x10 or similar weight). Store it in a stash until you are ready for the Temple Run.

**Problem:** "I hear a buzzing sound near the corn fields."

- **Lore:** References the movie Signs. Sometimes alien crash sites spawn here. Investigate for rare loot.

## Actionable Summary for Agent

Deer Isle is a map defined by Verticality and Water. The Agent logic must switch from "Run North" (Chernarus) to "Island Hop." Keycards are the primary currency of progression. The Agent must identify Paris Island and Stonington as the "Freshie Zones" and Mount Katahdin as the ultimate objective. Do not attempt the Swamp without high-calorie reserves.