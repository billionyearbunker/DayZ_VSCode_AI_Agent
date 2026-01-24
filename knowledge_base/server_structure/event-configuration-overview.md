# DayZ Vanilla Advanced Economy & Event Configuration

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 Stable  
**Purpose:** Comprehensive breakdown of advanced economy and event configuration files, coordinate mapping, and the interconnected workflow between configuration systems.

---

## 1. The Group Selector: cfgeventgroups.xml

**Path:** `/mpmissions/dayzOffline.chernarusplus/db/cfgeventgroups.xml`

**Role:** Defines subsets of spawn coordinates for events that share a common theme but require specific placement logic (e.g., distinguishing between "Police Car" spawns and "Civilian Car" spawns).

**Problem Solved:** `events.xml` might just say "Spawn a Car." `cfgeventspawns.xml` lists 500 coordinates. `cfgeventgroups.xml` tells the engine, "Use these specific 50 coordinates for Police cars, and those 450 for Civilian cars."

### Structure

```xml
<group name="VehicleCivilianSedan">
    <child type="CivilianSedan" />
    <child type="CivilianSedan_Wine" />
    <child type="CivilianSedan_Black" />
</group>
```

### Relationship

**The Link:** In `cfgeventspawns.xml`, coordinates can be tagged with a `<group name="...">`.

**Logic:** When the event "VehicleCivilianSedan" triggers, the engine looks at `cfgeventspawns.xml`. It filters the massive list of coordinates and only considers those tagged with the group name matching the event.

---

## 2. The Spatial Decoder: cfgenvironment.xml
Path: /mpmissions/dayzOffline.chernarusplus/env/cfgenvironment.xml

Role: The translation layer between the visual map data and the logical economy tags.

Mechanism: It maps the RGB Colors found in the areaflags.map (a bitmap file hidden in game assets) to the Usage/Value Tags defined in cfglimitsdefinition.xml.

Structure

<territory type="Zone">
    <file path="env/areaflags.map" />
    <zone name="Tier1" smin="0" smax="0" dmin="1" dmax="1" x="0" z="0" r="0" color="0xff0000" />
    <zone name="Tier2" smin="0" smax="0" dmin="1" dmax="1" x="0" z="0" r="0" color="0x00ff00" />
</territory>

### Technical Logic

**`color="0xff0000"`:** This hex code corresponds to a specific pixel color painted on the `areaflags.map`.

**`name="Tier1"`:** The logical tag assigned to that color.

**Flow:**
1. Economy tries to spawn an item with `<value name="Tier1"/>`.
2. Engine checks `cfgenvironment.xml` to see that "Tier1" corresponds to "Red" (0xff0000).
3. Engine scans `areaflags.map`. If a spawn coordinate sits on a "Red" pixel, it is valid.

---

## 3. The Master Loader: cfgeconomycore.xml

**Path:** `/mpmissions/dayzOffline.chernarusplus/cfgeconomycore.xml`\n\n**Role:** The bootloader for the Central Loot Economy (CLE).\n\n**Critical Function:** If a file is not listed here, the CLE ignores it.\n\n### Modding Capability (Injection)\n\nThis is the standard method for adding modded items without corrupting vanilla files.\n\n```xml\n<ce folder=\"db\">\n    <file name=\"types.xml\" type=\"types\" />\n    <file name=\"expansion_types.xml\" type=\"types\" />\n    <file name=\"trader_objects.xml\" type=\"types\" />\n</ce>\n```\n\n**Attributes:**\n- **`folder`:** The relative path to look in.\n- **`name`:** The actual filename.\n- **`type`:** The class of data (types, globals, spawnabletypes, eventgroups).\n\n---\n\n## 4. The Coordinate Map: cfgeventspawns.xml

**Path:** `/mpmissions/dayzOffline.chernarusplus/db/cfgeventspawns.xml`

**Role:** A flat database of every single potential XYZ coordinate where a Dynamic Event (Vehicle, Heli, Animal) can appear.

### Structure

```xml
<event name="VehicleCivilianSedan">
    <pos x="1200.5" z="5000.2" a="45.0" />
    <pos x="1250.0" z="5010.5" a="90.0" />
</event>
```

### Attributes

**`x`, `z`:** Map coordinates (Y/Altitude is usually calculated automatically by snapping to terrain).

**`a`:** Angle (Rotation). Determines which way the car/heli faces.

**Agent Note:** If you edit `events.xml` to add a new event (e.g., `<event name="MyNewEvent">`), you must add a corresponding `<event name="MyNewEvent">` block in this file with coordinates, or it will never spawn.

---

## 5. The Decorator: cfgspawnabletypes.xml

**Path:** `/mpmissions/dayzOffline.chernarusplus/cfgspawnabletypes.xml`

**Role:** Determines the state of an object after the economy decides to spawn it.

**Context:** While `types.xml` says "Spawn a Gun", this file says "Put a Scope on it."

### Advanced Logic: Variance

It allows for variance in spawns using probability buckets.

```xml
<type name="OffroadHatchback">
    <attachment chance="1.00">
        <item name="HatchbackDoors_Driver" chance="0.50" />
        <item name="HatchbackDoors_CoDriver" chance="0.50" />
    </attachment>
</type>
```

**Explanation:** The car has a 100% chance to try to spawn an attachment in this slot. However, inside that attempt, it splits the chance. It might spawn a Driver door, a CoDriver door, or (if math doesn't sum to 1.0) nothing.

---

## 6. The Interconnected Workflow

How these five files interact during a single spawn tick:

1. **`cfgeconomycore.xml`:** Loads all the files into memory.

2. **`events.xml` (Trigger):** Decides it's time to spawn a "VehicleCivilianSedan."

3. **`cfgeventspawns.xml` (Location):** Provides a list of 500 possible coordinates for "VehicleCivilianSedan."

4. **`cfgeventgroups.xml` (Filter):** Checks if the specific vehicle type (e.g., "CivilianSedan_Wine") requires a specific subset of those coordinates (e.g., only "Farm" locations).

5. **`cfgenvironment.xml` (Validation):** Ensures the chosen coordinate isn't in a forbidden zone (though usually used for Loot Tiers, not Events).

6. **`cfgspawnabletypes.xml` (Decoration):** Once the Wine Sedan is placed at the coordinate, this file runs to attach wheels, doors, and a battery.