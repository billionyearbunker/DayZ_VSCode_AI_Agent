# DayZ Vanilla Central Economy: types.xml Schema & Logic

## 1. File Overview

- **Path:** `/mpmissions/dayzOffline.chernarusplus/db/types.xml`
- **Purpose:** The primary database defining the existence, quantity, location, and persistence of every spawnable item in the game world.
- **Engine:** Controlled by the Central Loot Economy (CLE).
- **Syntax:** Standard XML. Case-sensitive for attribute values (classname matching).

## 2. Root Structure

The file is wrapped in a single root tag.

```xml
<types>
    </types>
```

## 3. Element Definition: <type>

Each item classname defined in `config.cpp` (pbo) must have a corresponding entry here to spawn naturally.

### Attribute: name

- **Syntax:** `<type name="Item_Classname">`
- **Constraint:** Must match the exact classname defined in the game files (modded or vanilla).
- **Behavior:** If a classname is missing from `types.xml`, it will never spawn automatically, though it can still be spawned via admin tools or scripts.

## 4. Child Elements (The Economy Logic)

### A. Quantity Control

**`<nominal>` (Integer):** The target number of this item the server tries to maintain on the map.
- **Logic:** The server spawns items until this number is reached.

**`<min>` (Integer):** The threshold that triggers the respawn queue.
- **Logic:** When the count drops to `min`, the server queues new spawns to reach `nominal` again.

**`<restock>` (Integer, Seconds):** The delay before the respawn queue processes this item after hitting `min`.
- **Set to 0:** Immediate respawn processing.

### B. Persistence Control

**`<lifetime>` (Integer, Seconds):** How long the item persists on the ground without interaction.

**Common Values:**
- **3888000 (45 Days):** Tents, barrels, seachests (Storage).
- **21600 (6 Hours):** Rare weapons.
- **14400 (4 Hours):** Standard loot.
- **3 (3 Seconds):** Used for "cleanup" items or errors.

### C. Spawn Details (Quantity & Priority)

**`<quantmin>` / `<quantmax>` (Percentage or Integer):**
- **For Items:** Represents percentage of durability (approximate). `-1` usually defaults to pristine/full.
- **For Mags/Liquids:** Represents the percentage full (e.g., ammo count or water level).

**`<cost>` (Integer, 100):** The "cost" to the economy to spawn this.
- **Oddity:** Largely vestigial in current builds, usually set to `100`.

### D. Flags (The "Counting" Logic)

These boolean flags (1=True, 0=False) dictate what the server counts when comparing against `nominal`.

```xml
<flags count_in_cargo="0" count_in_hoarder="0" count_in_map="1" count_in_player="0" crafted="0" deloot="0"/>
```

**`count_in_cargo`:**
- **1:** Includes items inside vehicles, backpacks, or other containers in the world count.
- **0:** Only counts items loose on the ground.

**`count_in_hoarder`:**
- **1:** Includes items stored in "Hoarder" containers (Tents, Barrels, Chests, Crates).
- **Critical Logic:** If this is `1` for rare items (e.g., M4A1), and players hoard 10 of them in tents, no new ones will spawn if `nominal` is 10. Set to `0` to ignore player stashes and force map spawns.

**`count_in_map`:**
- **1:** Standard setting. Counts items spawned on the floor of buildings.

**`count_in_player`:**
- **1:** Includes items currently in a player's inventory (logged in).
- **Warning:** Rarely used. Can cause zero spawns if players log out with the items.

**`crafted`:**
- **1:** Marks item as craft-only. Usually prevents spawning.

**`deloot`:**
- **1:** Dynamic Event Loot. Used for Heli Crash or Police Convoy loot. Tells CLE strictly to spawn this via `events.xml` triggers, not static map spawning.

### E. Location Filters (<category>, <usage>, <value>)

These tags cross-reference with the `map_grouppos.xml` (the map's building grid) to determine where an item spawns.

**`<category name="..." />`:** Broad filter.
- **Examples:** `clothes`, `weapons`, `tools`, `food`.

**`<usage name="..." />`:** Specific "Theme" of the location.
- **Examples:** `Military`, `Police`, `Farm`, `Town`, `Village`, `Hunting`.
- **Logic:** An item with `<usage name="Military"/>` will only spawn in buildings tagged as Military in the map files.

**`<value name="..." />`:** The "Tier" system (Geographic bands).
- **Tier1:** Coast/Start area.
- **Tier2:** Just inland.
- **Tier3:** Deep inland / North.
- **Tier4:** High-value military zones (Tisy/NWAF).
- **Logic:** You can combine these. `<value name="Tier3"/>` and `<value name="Tier4"/>` means it spawns in both high-end zones.

## 5. Example Entry: M4A1 (High Value)

```xml
<type name="M4A1">
    <nominal>10</nominal>
    <lifetime>21600</lifetime>
    <restock>1800</restock>
    <min>5</min>
    <quantmin>-1</quantmin>
    <quantmax>-1</quantmax>
    <cost>100</cost>
    <flags count_in_cargo="0" count_in_hoarder="1" count_in_map="1" count_in_player="0" crafted="0" deloot="0"/>
    <category name="weapons"/>
    <usage name="Military"/>
    <value name="Tier3"/>
    <value name="Tier4"/>
</type>
```

**Analysis:** Server wants 10 M4s. It counts those on the ground and in player tents (`count_in_hoarder="1"`). If the total drops below 5 (`min`), it waits 30 mins (`restock`) then spawns more. It only spawns in Tier 3/4 Military zones.

## 6. Syntactical Oddities & Common Errors

**Self-Closing Tags:**
- `<category name="weapons"/>` must adhere to strict XML. Missing the `/` before the closing `>` breaks the file.

**Validation:**
- One syntax error (e.g., a missing `</type>`) will cause the entire loot economy to default or fail (often resulting in zero loot or fallback loot).

**Mod Integration:**
- When adding modded items, you cannot simply paste them at the end. They must be inside the `<types>` root tags.
- Many admins use "include" functionality in `cfgeconomycore.xml` to keep mod files separate (e.g., `custom_types.xml`) rather than editing the massive `types.xml` directly.
