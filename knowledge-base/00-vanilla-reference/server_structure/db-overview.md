# DayZ Vanilla Database Directory: /db/ Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 Stable  
**Purpose:** Comprehensive breakdown of the `/db/` directory architecture, XML manifest system, and Central Loot Economy configuration files.

---

## 1. Directory Overview

**Path:** `/mpmissions/dayzOffline.chernarusplus/db/`

**Role:** The brain of the Central Loot Economy (CLE). It contains all XML datasets that control the spawning, persistence, and categorization of items and events.

**Loading Mechanism:** Unlike other folders, the engine does not "scan" this folder. It loads specifically what is defined in the manifest file: `cfgeconomycore.xml`.

---

## 2. The Manifest: cfgeconomycore.xml

This is the root loader. If a file is in the `/db/` folder but not listed here, it is ignored.

### A. Core Function

It defines which XML files are active and assigns them a "type" (role).

```xml
<ce folder="db">
    <file name="types.xml" type="types" />
    <file name="globals.xml" type="globals" />
    <file name="cfgspawnabletypes.xml" type="spawnabletypes" />
    <file name="my_mod_types.xml" type="types" /> 
</ce>
```

### B. Key Attributes

**`folder`:** Tells the engine which directory to look in (relative to mission root).

**`type`:** The internal engine handler for the file.
- **`types`:** Item spawn tables.
- **`globals`:** Server-wide variables.
- **`spawnabletypes`:** Attachments/Cargo logic.
- **`events`:** Dynamic event logic.
- **`defaults`:** Reset logic for wipes.

---

Controls the "Physics" of the economy. It contains Key-Value pairs that adjust server-wide behavior.

### Critical Variables

**`LootProxyPlacement` (0/1):**
- **`1`:** Items spawn inside container proxies (e.g., inside the visual model of a shelf or under a bed).
- **`0`:** Items spawn on the center point of the floor (Old school / Performance mode).

**`RestartSpawn` (Integer):**
- How many items to spawn immediately upon server restart to top up the economy.
- **Value 0:** Economy does not panic-spawn on restart; it waits for natural ticks.

**`TimeHoarding` (Integer):**
- A multiplier for the lifetime of stored items (Tents/Barrels).
- **Default 72:** Usually results in 45 days (using the base lifetime).

**`AnimalMaxCount` / `ZombieMaxCount`:**
- Hard caps for AI entities to preserve server FPS.

**`IdleModeCountdown`:**
- Time (in seconds) the server waits after the last player disconnects before freezing the economy simulation to save CPU.

---

## 4. Taxonomy & Definitions: cfglimitsdefinition.xml

This file defines the Tags used in `types.xml`. It creates the "Language" of the economy.

### Structure

**`<categories>`:** Defines valid categories (e.g., weapons, clothes).

**`<usage>`:** Defines usage flags (e.g., Military, Police, Town).

**`<value>`:** Defines Tier flags (e.g., Tier1, Tier2).

### Agent Logic

- If you want to create a new custom tag, e.g., `<usage name="SecretLab"/>`, you must define it here first.
- If you use a tag in `types.xml` that is not defined in `cfglimitsdefinition.xml`, the item will likely not spawn or default to a fallback.

---

## 5. Randomization Presets: cfgrandompresets.xml

Acts as a "Variable Store" for groups of items, referenced by `cfgspawnabletypes.xml`.

### Use Case: "Food in Zombies"

Instead of listing every food item in every zombie definition, you define a preset:

```xml
<cargo name="foodCommon">
    <item name="Apple" chance="0.20" />
    <item name="Banana" chance="0.20" />
    <item name="Plum" chance="0.20" />
</cargo>
```

**Integration:** In `cfgspawnabletypes.xml`, you simply write `<cargo preset="foodCommon" />`.

**Architecture:** Allows for changing the "Global Loot Table" for zombies/backpacks in one single file rather than editing thousands of lines.

---

## 6. Server Messaging: messages.xml

Controls the automated text broadcast to players during a shutdown sequence.

### Structure

```xml
<message>
    <delay>60</delay>
    <text>Server is restarting in 60 minutes.</text>
    <onconnect>0</onconnect>
</message>
```

**`delay`:** Time in minutes (relative to the shutdown timer).

**`onconnect`:** If `1`, this message is sent to a player immediately when they join.

---

## 7. The Ignore List: cfgignorelist.xml

**Role:** A blacklist for the economy.

**Function:** Tells the CLE, "If you see this item on the ground, do not interact with it."

**Usage:**
- Used for items that have their own internal physics/persistence scripts (e.g., `Land_Radio_PanelPas`).
- Prevents the economy from deleting specific static map objects that might technically be "items."

---

## 8. Economy Save Data: economy.xml

**Role:** Defines which parts of the economy are saved to the binary storage (`storage_1/data/types.bin`) and which are dynamic.

### Dynamic Attribute

**`init="1"`:** Wipes the data on restart (Fresh spawns).

**`load="1"`:** Loads the data from the binary save (Persistence).

**Wipe Logic:** To wipe just vehicles but keep tents, admins edit this file to toggle `load="0"` for vehicles before a restart.

---

## 9. Operational Oddities

**Syntax Fragility:** The `/db/` folder is the most fragile part of the server. One XML error (e.g., `<nominal>10<nominal>` - missing slash) in any file loaded by `cfgeconomycore.xml` can cause the entire loot system to abort.

**Validation:** The server log (`.RPT`) will output `[CE][Error]` lines indicating specifically which file and line failed to parse.

**Hot-Swapping:** You cannot edit these files while the server is running. The CLE loads them into RAM at boot. Changes require a full server restart.

**Folder Name:** While convention is `db`, you can rename it, provided you update the `economy.xml` or `cfgeconomycore.xml` paths (though highly discouraged).
