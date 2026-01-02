# DayZ Vanilla Server Environment: Technical Overview

## 1. Root Directory Structure (Server_Root)

The root directory serves as the execution entry point.

- **DayZServer_x64.exe:** Main server executable.
- **serverDZ.cfg:** Primary configuration file (hostname, password, max players, persistence). Note: The name `serverDZ.cfg` is a convention; the actual file used is defined by the `-config` launch parameter.
- **BattlEye/:** Contains `BEServer_x64.cfg` (RCON password, banlist).
- **Keys/:** Stores `.bikey` files. The server compares these against client keys to validate signed mods.
- **mpmissions/:** Contains mission folders (e.g., `dayzOffline.chernarusplus`).
- **@ModName/:** Typical structure for a mod. The `@` prefix is a convention for readability/sorting but not strictly required by the engine, though widely used.
- **start.bat (User Created):** The standard batch script used to launch the server with parameters (e.g., `-config`, `-profiles`, `-mod`).

## 2. Profile & Logic Structure

The `-profiles=NameOfFolder` launch parameter is critical. It redirects dynamic data away from the root to keep the server clean.

### The Profile Folder (/profiles/)

**Purpose:** Stores logs, persistence saves, and mod configurations.

**Key Contents:**
- ***.RPT files:** The main server debug logs.
- ***.ADM files:** Admin logs (connections, chats, building).
- **Users/:** Stores survivor states if not using a database wrapper.
- **Mod Configs:** Most modern mods (e.g., Expansion, CF, VPP) generate their config folders here, not in the mod folder itself.

## 3. Mission File Structure (/mpmissions/dayzOffline.chernarusplus/)

This folder dictates the "World" logic.

### A. The Entry Point: init.c

- **Role:** The constructor for the mission.
- **Key Function:** `void main()` is the entry point.

**Responsibilities:**
- Creating the hive (economy connection).
- Creating the player character object upon connection (`CreateCharacter`).
- Equipping the player with starting gear (`itemEnt.GetInventory().CreateInInventory`).
- Defining weather initiation.

### B. Economy & Spawn Control (/db/ and XMLs)

DayZ uses a Central Economy (CLE) controlled by XML files.

- **types.xml:** The master list of items. Defines `nominal` (target count), `min` (respawn trigger), `lifetime` (despawn timer), and `tiers` (map location).
- **events.xml:** Spawns dynamic events (Helicrashes, dynamic convoys, animal herds).
- **cfgspawnabletypes.xml:** Defines attachments/cargo for items (e.g., ensuring a gun spawns with a mag, or a car spawns with wheels).
- **globals.xml:** Server-wide variables (e.g., loot respawn timers, zombie counts).

### C. Environment (/env/)

- **territories.xml:** Defines spatial zones for AI (wolves, bears, infected) to roam.

### D. Configuration (/cfg/)

- **cfgGameplay.json:** (Newer addition) Controls stamina, hitboxes, map markers, and building placement rules without needing modded scripts.

## 4. Enforce Script (EnScript) Language Oddities

DayZ uses Enforce Script, a C-like language with strict object-oriented enforcement and unique memory management quirks.

### Syntax & Behavior

**Strict Typing:**
- Variables must be explicitly typed (`int`, `string`, `PlayerBase`).

**Memory Management (ref vs autoptr):**
- **ref:** Strong reference. The object persists as long as this reference exists.
- **autoptr:** Automatic pointer. The object is deleted when the variable goes out of scope (end of function/block). Crucial for preventing memory leaks.

**Null Checks:**
- Accessing a null object crashes the entire server instance instantly. `if (!object) return;` is mandatory before manipulation.

**Casting:**
- Heavily relies on `CastTo`.
- Example: `Class.CastTo(myPlayer, game_entity);`

**Modules:**
- Code is divided into modules:
  - **1_Core:** Base engine functions.
  - **3_Game:** Global game logic.
  - **4_World:** Entities, items, player logic.
  - **5_Mission:** UI, Camera, and the `init.c` script.
- **Rule:** Higher modules can access lower ones, but lower ones cannot access higher ones directly.

### Common Oddities

- **GetGame():** The singleton access point for the game instance. Nearly all logic starts here.
- **String Formatting:** Concatenation uses `+` but complex formatting often requires `%1`, `%2` variable substitution syntax in localized strings.
- **Arrays:** Static arrays exist, but `ref array<type>` is preferred for dynamic resizing.
- **RPC (Remote Procedure Calls):** Communication between Client and Server is manual. You must define an RPC ID, register it, send it, and catch it in `OnRPC`.

## 5. Mod Structure & Loading

### Folder Hierarchy (@ModName)

- **Addons/:** Contains `.pbo` files (Packed Bohemia Objects). These are the compiled mod assets and scripts.
- **Keys/:** Contains the public `.bikey`. Must be copied to the server root `Keys` folder to allow clients to join.
- **mod.cpp or meta.cpp:** Metadata for the launcher (logo, description).

### The PBO Structure

Inside a `.pbo` (viewable with tools like PBOManager), the logic follows the module structure (World, Mission, etc.).

- **config.cpp:** The definition file. It inherits from base classes (e.g., `class CfgVehicles`) to override properties without writing scripts.

## 6. Dependencies & Requirements

- **DirectX:** DirectX End-User Runtimes (June 2010).
- **Visual C++:** Redistributables 2013, 2015-2019 (x86 and x64).
- **SteamCMD:** Required for downloading and updating the server files via command line.

**Network:**
- **UDP 2302:** Game Port (Default).
- **UDP 27016:** Steam Query Port (Default).
- **UDP 47200 (optional):** Often used by specific mod tools like DOM or Omega Manager.

## 7. Operational Workflow

1. **Startup:** `start.bat` invokes `DayZServer_x64.exe`.
2. **Config Load:** Reads `serverDZ.cfg` -> Defines Mission Path.
3. **Mission Load:** Loads `mpmissions/init.c`.
4. **Hive Connect:** Server connects to local storage (or external DB).
5. **Loot Spawn:** CLE reads `types.xml` and populates the world based on `lifetime` and `nominal` values.
6. **Loop:** Server enters main tick loop (simulation).