# DayZ Custom Profiles Directory: Technical Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 (Stable)  
**Purpose:** Technical documentation of the profiles directory structure, logging systems, and configuration management

---

## 1. Directory Definition & Role

**Launch Parameter:** Defined by `-profiles=Foldername` (e.g., `-profiles=Profiles` or `-profiles=SC`).

**Role:** The write-access directory for dynamic server operations excluding the world hive. It separates static executable data from mutable runtime data.

**Permissions:** The server executable (`DayZServer_x64.exe`) requires explicit Read/Write/Modify access to this folder.

---

## 2. The Logging Infrastructure

The profiles folder is the primary destination for all diagnostic output.

### A. The RPT File (*.RPT)

**Format:** `DayZServer_x64_<timestamp>.RPT`

**Content:** The standard output (stdout) and standard error (stderr) equivalent for the Arma/Enfusion engine.

**Critical Markers:**
- `init.c`: syntax errors in the mission file will appear here.
- `script`: Stack traces for mod errors (Null Pointer Exceptions).
- `[CE]`: Central Economy debug messages (e.g., "Failed to spawn entity").

**Oddity:** RPT files are not auto-rotated or deleted by the engine. They will accumulate indefinitely until the disk is full, requiring external batch scripts or tools (like OmegaManager/CFTools) to manage cleanup.

### B. The ADM Logs (*.ADM)

**Format:** `DayZServer_x64_<timestamp>.ADM`

**Trigger:** Enabled via `serverDZ.cfg` parameter `adminLog = 1;`.

**Content:**
- **Connections:** Player Connect/Disconnect with Steam64IDs and IP addresses.
- **Chat:** Global, Direct, and Vehicle chat logs.
- **Placement:** Logs whenever a player places a base building object (Fence, Tent).
- **Damage:** (If enabled) Logs who hit whom and with what projectile.

### C. BattlEye Logs (/BattlEye/)

**Location:** Often generated inside `profiles/BattlEye` if the profiles path is set.

**Files:** `scripts.log`, `createvehicle.log`, `publicvariable.log`.

**Function:** These logs show when the Anti-Cheat kicks a player.

**Agent Note:** These are vital for debugging "Kick" errors. A player getting kicked for "Script Restriction #45" requires checking `scripts.log` line #45 to adjust filters.

---

## 3. Mod Configuration Hub

In modern DayZ (post-2019), the profiles folder has become the standard repository for Mod Settings. Mods use this folder to generate JSON or TXT config files so admins don't have to repack PBOs to change settings.

### A. Community Framework (/CF/ or permissions/)

**Role:** Many mods depend on Community Framework (CF). It stores server-side permissions here.

**Structure:** Uses JSON serialization.

### B. Common Mod Folders

**`/VPPAdminTools/`:**
- `Permissions/SuperAdmins.txt`: Stores Steam64IDs of server admins.
- `UserGroups/`: Defines what specific tools (Esp, Teleport, Godmode) each admin rank can use.

**`/ExpansionMod/`:**
- **Complexity:** Extremely high. Contains subfolders for Settings, Quests, Market, Traders.
- **Format:** JSON files.
- **Behavior:** Expansion will auto-generate default files here on the first run. Admins edit the JSONs, and the mod reads them on the next restart.

**`/Trader/` (Dr. Jones):**
- `TraderConfig.txt`: Defines currency, prices, and stock for safezone traders.
- **Oddity:** Uses a custom tab-delimited or space-delimited syntax, not JSON. Very sensitive to whitespace errors.

---

## 4. User Persistence (/Users/)

**Path:** `profiles/Users/Survivor/`

**File:** `Server.vars.DayZProfile`

**Role:** Stores server-specific variable persistence, but not the character hive (inventory/health).

**Usage:** Rarely edited manually. Stores things like view distance settings if forced by the server, or specific variable states that aren't strictly "Gameplay" mechanics.

---

## 5. Crash Dumps (*.mdmp)

**Format:** Minidumps generated when the server executable crashes (CTD).

**Utility:** Binary files readable only by debugging tools (Windbg) or Bohemia Interactive developers.

**Agent Action:** If these exist, the server is unstable. They cannot be "fixed" via text editing; they indicate a binary conflict or memory corruption.

---

## 6. Operational Oddities

**File Locking:** The server places a write lock on the active `.RPT` and `.ADM` files. You cannot move or delete them while the server is running. You can read them (tail) in real-time.

**Sanitization:** Deleting the profiles folder is generally safe. The server will regenerate a fresh one on startup (creating new logs and default mod configs). This is a common troubleshooting step for "Corrupted Mod Configs."

**JSON Syntax Sensitivity:** The majority of mod configs in this folder are JSON. A single missing comma in a Trader file or Expansion setting will often cause the entire mod to revert to default settings or crash the server silently.