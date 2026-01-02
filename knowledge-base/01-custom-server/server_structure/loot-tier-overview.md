# DayZ Custom Loot Tier System: Technical Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 Stable  
**Purpose:** Comprehensive breakdown of the loot tier system, geographic filtering mechanics, and the configuration handshake between types.xml, map data, and area flags.

---

## 1. Concept & Purpose

**Definition:** A geographic filtering system that governs the progression of loot quality relative to map difficulty.

**Mechanism:** It acts as a "Mask" or "Overlay" on the game world. When the Central Economy (CLE) attempts to spawn an item, it checks if the candidate spawn point lies within the correct Geographic Tier defined in the item's properties.

**Progression:** Generally moves from "Low Risk/Low Reward" (Coast) to "High Risk/High Reward" (Inland/North-West).

---

## 2. The Configuration Handshake

The Tier system functions through the interaction of three specific files/assets.

### A. The Request: types.xml

The specific item requests to be spawned in a specific tier via the `<value>` tag.

```xml
<type name="M4A1">
    ...
    <value name="Tier3"/>
    <value name="Tier4"/>
    ...
</type>
```

**Logic:** This item must spawn on a coordinate that is flagged as Tier 3 OR Tier 4. It will fail to spawn in Tier 1 or 2.

### B. The Coordinate Source: map_grouppos.xml

**Content:** A massive list of XML coordinates defining every loot spawn point (building positions) on the map.

**Role:** Provides the physical $X, Z$ coordinates for potential spawns.

### C. The Filter: areaflags.map (and cfgeconomycore.xml)

**Nature:** A bitmap image file (not human-readable text) located in the server game files (inside missions pbo).

**Role:** It paints the map in different "Colors," where each color represents a Tier.

**Intersection Logic:** The engine looks at a coordinate from `map_grouppos`, checks the `areaflags.map` to see what "Tier Color" that coordinate sits on, and then checks `types.xml` to see if the item allows spawning there.

---

## 3. The Tier Hierarchy (Chernarus Example)

### Tier 1 (Coast / Spawn Zone)

**XML Tag:** `<value name="Tier1"/>`

**Geography:** The immediate coastline (South and East).

**Loot Profile:** Basic survival (Flashlights, Bandages, Ij-70, Civilian clothing).

### Tier 2 (Buffer Zone)

**XML Tag:** `<value name="Tier2"/>`

**Geography:** A band approx. 1-2km inland from the coast.

**Loot Profile:** Mid-range civilian, basic police gear, hunting rifles (BK-18), farming tools.

### Tier 3 (The North / Inland)

**XML Tag:** `<value name="Tier3"/>`

**Geography:** The deep North and West (Stary Sobor, Vybor, Zeleno).

**Loot Profile:** Military grade standard (SK 59/66, KA-74, Combat Gear).

### Tier 4 (High Value / End Game)

**XML Tag:** `<value name="Tier4"/>`

**Geography:** Specific high-danger zones.
- **Chernarus:** Tisy Military Base (Far North West) and Tri Kresta.

**Loot Profile:** End-game military (M4A1, LAR, VSD, Night Vision).

---

## 4. Special Tiers & Flags

### The "Unique" Tier

**XML Tag:** `<value name="Unique"/>`

**Usage:** Rarely used in vanilla types. It implies a specific, manually defined area often used for quest items or static spawns in modded scenarios.

### The Absence of Tiers (Global Spawn)

**Syntax:** If an item in `types.xml` has NO `<value>` tags:

```xml
<type name="Apple">
    <nominal>100</nominal>
</type>
```

**Logic:** The item can spawn in ANY tier (1, 2, 3, or 4), provided the `<usage>` (e.g., Farm) and `<category>` (e.g., Food) match a building.

### Multi-Tier Spawning

**Syntax:**

```xml
<value name="Tier2"/>
<value name="Tier3"/>
```

**Logic:** Allows the item to bridge the gap between zones. Common for items like the Mosin Nagant, which shouldn't be on the coast but shouldn't be exclusive to Tisy.

---

## 5. Map Differences (Livonia vs. Chernarus)

The definition of "North" changes based on the map file loaded.

**Chernarus:** Progression is South-East (Tier 1) to North-West (Tier 4).

**Livonia:** Progression is strictly North (Tier 1) to South (Tier 3/4).

**Note:** Livonia Tier 1 is the spawn river in the North. The "Deep South" is the hardest zone.

---

## 6. Operational Oddities & Customization

### The "Tier 1 + Military" Paradox

**Scenario:** A building is tagged Military but is located in Tier 1 (e.g., Balota Airfield or Kamyshovo Police Station).

**Logic:** If you set an M4A1 to `<usage name="Military"/>` and `<value name="Tier3"/>`, it will NOT spawn at Balota (Tier 1/2), even though Balota is military. It will only spawn at Vybor/NWAF (Tier 3 Military).

**Exploit:** This is how admins force high-tier loot to the coast (PVP servers). They simply add `<value name="Tier1"/>` to the M4A1 entry in `types.xml`.

### "Tier 0" Terminology

**Fact Check:** There is no technical `<value name="Tier0"/>`.

**Community Slang:** Users sometimes refer to the coast as Tier 0, or debug zones as Tier 0, but the XML parser does not recognize this tag.

### Troubleshooting Zero Spawns

If an item has nominal set to 10 but 0 are spawning:

**Check:** Does the intersection exist?

**Example:** An item has `<usage name="Industrial"/>` and `<value name="Tier4"/>`.

**Failure:** If there are no buildings tagged "Industrial" located inside the "Tier 4" zone (which is mostly military tents/barracks), the intersection is Null. The item cannot spawn.

---

## 7. Editing Tiers (Advanced)

You cannot easily change where Tier 3 is on the map without editing the `areaflags.map` (which requires modding tools like DayZ Tools / Workbench).

**Workaround:** You can redefine the item's requirement. You cannot move the mountain to the loot, but you can move the loot to the mountain by changing `<value>` in `types.xml`.
