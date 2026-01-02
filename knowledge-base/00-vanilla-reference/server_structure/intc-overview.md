# DayZ Vanilla Mission Script: init.c Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 (Stable)  
**Purpose:** Technical documentation of the init.c mission script architecture, class structure, and implementation patterns

---

## 1. File Definition & Scope

**Path:** `/mpmissions/dayzOffline.chernarusplus/init.c` (Path varies by map).

**Language:** Enforce Script (C-like syntax).

**Role:** The Constructor of the mission instance. It is the first script executed when the mission loads.

**Execution Context:** Server-Side (mostly). Some elements broadcast to Client.

**Compilation:** Compiled once at server startup. Changes require a server restart to take effect.


The file typically contains a global main function and a class that extends `MissionServer`.

```cpp
void main()
{
    // The entry point function for the world environment
}

class CustomMission: MissionServer
{
    // Overrides for specific game events (Player creation, login, etc.)
}
```

---

## 3. The main() Functionpecific game events (Player creation, login, etc.)

3. The main() Function
This is the procedural entry point that sets up the world before players exist.

A. Hive Initialization
Hive ce = CreateHive();: Initializes the Central Economy (CE). Without this, no loot spawns.

if ( ce ) ce.InitOffline();: Starts the economy logic.

B. Weather Configuration
Weather weather = g_Game.GetWeather();: Fetches the weather singleton.

weather.MissionWeather(false);: Disables "Mission" preset weather logic to allow dynamic flow.

weather.GetOvercast().SetLimits( 0.0 , 1.0 );: Defines the min/max range for clouds.

weather.GetOvercast().SetForecastChangeLimits( 0.0, 0.2 );: Defines how drastically weather can change in one cycle.

C. Date & Time
GetGame().GetWorld().SetDate( 2026, 1, 1, 9, 0 );: Sets the in-game date/time (Year, Month, Day, Hour, Minute).

- **Logic:** This is the time the server starts at. Persistence (saving time) usually overrides this if configured in `serverDZ.cfg`.

---

## 4. The CustomMission Class

This class overrides engine events to customize player behavior.

### A. Player Creation (CreateCharacter)

**Signature:** `override PlayerBase CreateCharacter(PlayerIdentity identity, vector pos, ParamsReadContext ctx, string characterName)`

**Purpose:** Determines the physical avatar of the player.

**Default Logic:**
- If the player has a saved character in the hive, it loads that.
- If new, it creates a random survivor.

**Customization:**
- You can force specific skins here: `characterName = "SurvivorM_Mirek";`

### B. Starting Gear (StartingEquipSetup)

**Signature:** `override void StartingEquipSetup(PlayerBase player, bool clothesChosen)`

**Purpose:** Defines what a fresh spawn carries.

**Mechanism:**
- **Clear Inventory:** `player.RemoveAllItems();`
- **Add Items:** `player.GetInventory().CreateInInventory("ItemClassname");`
- **Add to Hands:** `player.GetHumanInventory().CreateInHands("ItemClassname");`
- **Shortcuts:** `itemEnt.SetQuickBarEntityShortcut(itemEnt, 0);` (Assigns to hotbar slot 1).

**Code Snippet Example (Loadout):**

```cpp
override void StartingEquipSetup(PlayerBase player, bool clothesChosen)
{
    player.RemoveAllItems();

    // Clothing
    player.GetInventory().CreateInInventory("TShirt_Black");
    player.GetInventory().CreateInInventory("Jeans_Blue");
    player.GetInventory().CreateInInventory("AthleticShoes_Black");

    // Gear
    player.GetInventory().CreateInInventory("Rag");
    ItemBase lights = player.GetInventory().CreateInInventory("Chemlight_White");
    lights.SetQuickBarEntityShortcut(lights, 0); // Hotbar slot 1

    // Food
    player.GetInventory().CreateInInventory("Apple");
}
```

---

## 5. Advanced Functions & Hooks

### A. OnPreloadFinished

**Trigger:** Runs when the client finishes loading mission assets.

**Usage:** Best place to send RPCs (Remote Procedure Calls) to the client or initialize complex mod data that requires the world to be fully built.

### B. PlayerEventListener

**Usage:** Can monitor when a player connects, disconnects, or respawns.


**Include Statements:** `#include "$CurrentDir:\\mpmissions\\DayZSurvival.chernarusplus\\Script\\custom_file.c"`
- You can split your code into multiple files and include them in `init.c`.

**Variable Scope:** Variables defined inside `StartingEquipSetup` (like `ItemBase rags`) are local. You cannot access them in `main()`.

**Null Checks:**
- **CRITICAL:** When creating items, always check if the item was actually created before modifying it.
- **Bad:** `player.GetInventory().CreateInInventory("M4A1").SetHealth("","Health", 0);` (Crashes if M4 fails to spawn).
- **Good:**

```cpp
EntityAI gun = player.GetInventory().CreateInInventory("M4A1");
if (gun) { gun.SetHealth("","Health", 0); }
```

---

## 7. Operational Workflow
Good:
EntityAI gun = player.GetInventory().CreateInInventory("M4A1");
if (gun) { gun.SetHealth("","Health", 0); }

1. **Server Start:** Engine loads `serverDZ.cfg`.
2. **Mission Select:** Engine mounts `mpmissions/dayzOffline.chernarusplus`.
3. **Compilation:** `init.c` is read and compiled into bytecode.
4. **Execution:** `void main()` is run. Economy and Weather start.
5. **Connection:** When a player joins, `CreateCharacter` fires → then `StartingEquipSetup` fires (if fresh spawn).

---

## 8. Modding Implicationser joins, CreateCharacter fires -> then StartingEquipSetup fires (if fresh spawn).

8. Modding Implications
Conflict: If a mod wants to change the starting loadout, it usually overrides StartingEquipSetup via a modded class in its own PBO.

**Conflict:** If a mod wants to change the starting loadout, it usually overrides `StartingEquipSetup` via a modded class in its own PBO.

**Priority:** `init.c` overrides are "Mission level." They often take precedence over basic mod defaults unless the mod uses strong modded class overrides.

**Vanilla Overwrite:** Every time the DayZ game updates via Steam, the `mpmissions` folder might be verified/reset if you are not careful.

**Best Practice:** Rename your mission folder (e.g., `dayzOffline.custom_chernarus`) and update `serverDZ.cfg` to point to it. This prevents Steam from overwriting your custom `init.c` during an update.