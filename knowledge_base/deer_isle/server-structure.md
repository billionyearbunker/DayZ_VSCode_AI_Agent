# DayZ Mod Map: Deer Isle Technical Architecture

## 1. Map Identity & Installation

- **Mod Name:** Deer Isle
- **Author:** JohnMcLane
- **Mission Folder:** Usually provided as `empty.deerisle` or `dayzOffline.deerisle` in the server download.
- **Server Config:** `template="dayzOffline.deerisle";` (in serverDZ.cfg).
- **Map Name:** `deerisle` (for cfgweather, etc).

## 2. The Tier System (The "11-Tier" Anomaly)

Unlike Vanilla Chernarus (4 Tiers) or Livonia (3 Tiers), Deer Isle utilizes a highly complex, expanded tier system.

### The "Zone" Logic

- **Tier 1 (Spawn):** The Southern main island (Stonington).
- **Tier 2-5:** Progressive difficulty moving North and West.
- **Tier 6-9:** High-value military islands (e.g., Aircraft Carrier, Swamp Military).
- **Tier 10:** The "Arctic" / North. Extreme cold survival.
- **Tier 11 (Endgame):** The Temple / Crypt.

**Agent Note:** Standard types.xml files usually only account for Tiers 1-4. To spawn loot correctly on Deer Isle, the map_grouppos.xml and areaflags.map must be correctly calibrated to support custom values, or you simply map Tier 11 areas to Vanilla "Tier 4" logic in your types.

## 3. Unique Mechanics & Event Logic

### A. The Tide System

Deer Isle features a dynamic tide system that actually raises and lowers the water level.

- **Mechanism:** Scripted event inherent to the map mod.

**Impact on Spawns:**

- **Loot:** Items spawned on the shoreline at Low Tide may be submerged at High Tide.
- **Bases:** Base building below the high-tide mark can result in flooded bases.
- **Pathfinding:** AI (Zombies/Wolves) generally do not navigate the tidal flats well and may walk underwater.

### B. The Crypt & Temple (Quest Logic)

- **Static Triggers:** The map contains hard-coded triggers for teleports and "The Temple" event.
- **Persistence:** These areas are part of the terrain .pbo but often rely on specific init.c logic provided in the official mission files to function (e.g., the smoke/sounds of the temple).
- **Loot:** "KMUC" (Keycard) rooms require specific loot definitions in types.xml to spawn the keycards (often BJ_Keycard_Red, etc., if using the specific sub-mod).

## 4. Environment & Economy Configuration

### A. areaflags.map (The Custom Palette)

- **Complexity:** The bitmap for Deer Isle is significantly more colorful than Chernarus to account for the 10+ distinct zones.
- **Mapping:** cfgenvironment.xml must map these extra colors. If you use a vanilla cfgenvironment.xml, loot will only spawn in the red/green/blue zones, leaving 60% of the map (the custom Deer Isle zones) empty of loot.

### B. map_grouppos.xml

- **Size:** Massive. Deer Isle has a very high building density compared to Chernarus.
- **Usage Tagging:** The map creator has meticulously tagged custom structures.
- **Example:** Land_JMC_Temple might be tagged strictly as Military or Historic.
- **Warning:** Overwriting this file with a vanilla Chernarus one (a common mistake during server updates) will result in Zero Loot spawning map-wide.

### C. Weather & Survival

- **Fog:** The map script enforces heavy fog in specific zones (The Swamp, The North). This is often hard-coded in the map's climatic settings and resists standard cfgweather.xml overrides unless using admin tools.
- **Temperature:** The Northern islands act as a "Winter Map" zone within a temperate map. Code in the map's world config lowers the ambient temperature based on the Z-coordinate (North).

## 5. Known Oddities & Troubleshooting

### A. The "Water" Spawn Issue

- **Scenario:** Heli Crashes or Cars spawning in the ocean.
- **Cause:** Deer Isle has vast water expanses. If cfgeventspawns.xml contains coordinates that were valid on land in an older version but are now water (due to map updates), the event spawns underwater.
- **Fix:** Always use the cfgeventspawns.xml provided with the current version of the mod. Do not carry over old coordinate files.

### B. Sound Controllers

- **Ambience:** Deer Isle uses custom soundsets (Bird noises, Temple rumbles).
- **Conflict:** Some audio mods (e.g., "MoreGunSounds") can conflict with the map's ambient sound handlers if priority is not set correctly in the mod load order.

### C. AI Mesh (Navmesh)

- **Complex Terrain:** The verticality of Deer Isle (cliffs, oil rigs) strains the AI Navmesh.
- **Behavior:** Zombies on the Oil Rigs or Aircraft Carrier often phase through floors or refuse to aggro because they cannot calculate a path to the player. This is a geometry limitation, not a server config error.

## 6. Mission Files vs. Map Updates

- **The "Empty" Mission:** The mod author releases a mission folder called `empty.deerisle`.
- **Critical Step:** When the mod updates on Steam, you must check if the db/ files (specifically types.xml and map_grouppos.xml) were updated.

**Workflow:**

1. Download new Mission files.
2. Copy map_grouppos.xml (Coordinates) -> overwrite old.
3. Copy zombie_territories.xml (AI Zones) -> overwrite old.
4. Merge types.xml (New Items) -> Do not simply overwrite if you have custom edits; use a diff tool.

## 7. Recommended Mod Associations

While not strictly "technical architecture," Deer Isle is structurally built to interface with:

- **Boats:** The geography forces boat usage. Standard events.xml usually includes spawn points for Vanilla boats, but modded boats (RedFalcon, Expansion) require custom events.xml entries.
- **Helicopters:** The map size (16km x 16km) is significantly larger than Chernarus (15km x 15km) in terms of traversal time due to water gaps.