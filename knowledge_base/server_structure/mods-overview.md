# DayZ Vanilla Mod Integration: Technical Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 (Stable)  
**Purpose:** Technical documentation of mod integration, installation hierarchy, and security systems

---

## 1. The Source & Transport (Steam Workshop)

**Origin:** Mods are hosted on the Steam Workshop.

**Client Side:** Clients subscribe via Steam. Files are downloaded to `!Workshop` (hidden folder) in the game root.

**Server Side:** The server must possess an identical copy of the mod files to allow connection (unless it is a server-side only mod).

**Naming Convention:** Mods traditionally start with `@` (e.g., `@CF`, `@VPPAdminTools`). This is a sorting convention, not a hard engine requirement, but highly recommended for parsing.


To install a mod, the folder must exist in the `Server_Root`.

### A. The Folder Structure

A valid mod folder (e.g., `@MyMod`) must contain:

- **Addons/:** Contains `.pbo` files (The compiled code/assets).
- **Keys/:** Contains `.bikey` files (The security signature).
- **mod.cpp / meta.cpp:** Metadata (Icon, Description, Version).

### B. The PBO (Packed Bohemia Object)

- **Nature:** Compressed archives containing scripts, models, textures, and configs.
- **Loading:** The engine automatically loads all `.pbo` files found inside the `Addons` folder of any loaded mod.
- **Load Order:** DayZ loads mods sequentially. If Mod B depends on Mod A, Mod A must be loaded first in the launch parameters.

---

## 3. The Security System: Keys (.bikey)
Load Order: DayZ loads mods sequentially. If Mod B depends on Mod A, Mod A must be loaded first in the launch parameters.


This is the most common point of failure for new servers.

**Concept:** Signature Verification.

**The Mechanism:**
1. The Mod Author signs their PBOs with a private key (`.biprivatekey`).
2. They distribute the public key (`.bikey`) inside the mod folder.

**Action Required:** The Server Admin must copy the `.bikey` from `@ModName/Keys/` to the `Server_Root/Keys/` folder.

**The Handshake:** When a client joins, the server checks: "Do I have a `.bikey` in my `Server_Root/Keys` that matches the signature of the PBO the client is trying to load?"
- **Match:** Connection allowed.
- **No Match:** Client kicked ("Verify Signatures Failed").

---

## 4. Execution Logic: Launch Parameters
4. Execution Logic: Launch Parameters
Mods are injected into the engine via command line arguments in `start.bat`.

### A. Standard Mods (-mod)

**Usage:** Mods required by both Client and Server (Items, Vehicles, Map changes).

**Syntax:** `-mod=@ModName;@AnotherMod;@ThirdMod`

**Delimiters:**
- Semicolon `;` separates mods.
- No spaces allowed after semicolons.
- If a mod name contains spaces, the whole string must be quoted: `"-mod=@Mod Name With Spaces;@OtherMod"` (However, it is best practice to rename folders to remove spaces).

### B. Server-Side Mods (-servermod)

**Usage:** Mods required only by the Server (Admin tools, AI managers, mission loggers).

**Behavior:**
- The server loads these PBOs.
- The server does not tell the Client to load them.
- The server does not enforce signature verification for these (usually).

**Benefit:** Clients do not need to download these mods to join.

---

## 5. Economy Integration (The "Loot" Step)

Simply loading a mod does not make its items spawn. You must instruct the Central Economy (CLE).

### A. Classname Extraction

**Goal:** Find the class names of the new items (e.g., `Modded_Rifle_Black`).

**Source:** Usually found in the mod's `types.xml` provided by the author (often in a folder named `extras` or `xml` inside the mod), or by inspecting the `config.cpp` within the PBO.

### B. Integration Methods

**Direct Append (Destructive):** Copy the mod's `<type>` entries and paste them into the main `mpmissions/dayzOffline.chernarusplus/db/types.xml`.
- **Risk:** Hard to maintain. If you remove the mod later, you must manually hunt down the entries.

**CFG Injection (Non-Destructive):**
1. Create a file `custom_types.xml` in the `/db/` folder.
2. Paste the mod's XML entries there.
3. Edit `mpmissions/.../cfgeconomycore.xml` to include the new file:

```xml
<ce folder="db">
  <file name="types.xml" type="types" />
  <file name="custom_types.xml" type="types" />
</ce>
```

---

## 6. Operational Oddities & Constraints

**Symlinks:** Advanced server admins often use Symbolic Links (`mklink`) to point multiple server instances to a single `@Mod` storage folder to save disk space.

**Update Logic:** Steam Workshop mods update frequently.
- **Risk:** If the Client updates a mod but the Server has the old version (or vice versa), the PBO signatures won't match.
- **Solution:** The Server must check for updates, download them, and—critically—copy the new keys to the root `Keys` folder every time a mod updates.

**Dependency Chains:**
- Many mods require `@CF` (Community Framework) or `@Dabs Framework`.
- **Rule:** Dependencies must be listed before the dependent mod in the `-mod` parameter.
- **Example:** `-mod=@CF;@Community-Online-Tools` (Correct) vs `-mod=@Community-Online-Tools;@CF` (Incorrect - may crash).

**Space Sensitivity:**
- Avoid spaces in folder names. Rename `@My Cool Mod` to `@MyCoolMod`.
- If you rename a mod folder, you must update the launch parameter to match exactly.

---

## 7. Troubleshooting "Verify Signatures"

If a player cannot join due to signature errors, the checklist is:

1. Did you copy the `.bikey` from inside the mod to the root `Keys` folder?
2. Is the mod included in the `-mod=` parameter?
3. Does the Client version match the Server version?
4. Does the Mod name in the parameter match the folder name exactly?
