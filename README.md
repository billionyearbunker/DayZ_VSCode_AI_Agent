# DayZ Deer Isle AI Developer Agent for Visual Studio Code

This repository contains the configuration files needed to turn Visual Studio Code's GitHub Copilot into a specialized, context-aware AI developer for DayZ servers, specifically focused on the Deer Isle map for the Outpost 31 server. 

To use this agent with your server you will need to add to your knowledge base any additional mod inforation. For example, I'm using the full Expansion mod and CF Tool, so I created markdown wikis in the knowledge base of all the information I could find on official github repos and the mods official Discords. I will continue to add to this specific agent as I work on my server, but you can edit / change / update however you need to. Check out the readme below for more details and feel free to hit me up if you have any questions.

A couple notes about this agent:
- This was entirely developed with AI leveraging Gemini 3 via an AI Ultra subscription. I use Gemini to develop and test the code in Visual Studio Code.
- I pay for the Copilot Pro+ subscripbtion that gives me access to Claude Sonnet 4.5 which was used in this agent specifically. It has not been tested on different versions.
- Like with everything AI generated, there are going to be mistakes and oddities that will need sorted out.

This is just a v1, I plan on tinkering with it and expanding it beyond Deer Isle at some point as the main goal of this project is to develop a new server.

# What Is This Exactly?

## By setting up this agent, you get an AI assistant that:

- Prioritizes your local documentation over general internet knowledge.
- Understand the specific coordinates and locations of Chernarus.
- Can write safer, context-aware Enforce Script (.c).
- Respects a strict "Hierarchy of Truth", prioritizing your custom server changes over vanilla data.

## Prerequisites

Before you begin, ensure you have the following:

- **Visual Studio Code** (Latest stable version).
- **GitHub Copilot Subscription**: You must have a Copilot Pro or Copilot Business subscription that includes access to advanced models like Claude 3.5 Sonnet and the Custom Agents feature.
- **VS Code Extensions**: Ensure the following extensions are installed and enabled:
  - GitHub Copilot
  - GitHub Copilot Chat

## Setup Tutorial

Follow these steps exactly to configure your workspace.

### Step 1: Create the Workspace Structure

The agent relies on a very specific folder structure to know where to look for information and where its definitions live.

1. Open your DayZ server project folder in VS Code.

2. Create the following directories at the root of your project:

```
/Your-DayZ-Project-Root
  │
  ├── .github/                        <-- Hidden folder for Copilot configs
  │   └── agents/                     <-- Folder specifically for agent definitions
  │
  └── knowledge-base/                 <-- "Sources of Truth" documentation
      ├── cf_tools/                   <-- The complete wiki from CF Tools / CF Cloud / OmegaManager
      └── deer_isle/                  <-- A self created wiki of all things Deer Isle made with Gemini 3
      └── expansion_mod/              <-- The entire Expansion Mod wiki from github
        └── expansion_mission_files/  <-- Vanilla Expansion mission files
        └── expansion-modding/        
        └── expansion-settings/       
        └── guides/                  
        └── misc/                    
        └── mod_configs/             
        └── modding/                  
        └── server-hosting/          
      └── loot_crates/                <-- Mod instructions from steam workshop
      └── mechanics/                  <-- Complete breakdown of the DayZ vanilla game mechanics created with Gemini 3
      └── MVS_by_color/               <-- Organized kits by type class, created with our custom agent
      └── Outpost_31/                 <-- Specific wiki for my server, contains lore, info, data, etc
      └── server_structure/           <-- Complete breakdown of the server structure and file hierarchy of a DayZ server
      └── skill_tree/                 <-- Mod instructions from steam workshop
      └── stats/                      <-- A bananas set of data tables for comparing all available stats of every single in game item
      └── vanilla-empty.deerisle/     <-- Vanilla Deer Isle mission files straight from the man John McLane
```

**Tip:** On Windows, the `.github` folder might be hidden by default. Ensure you can see hidden files if you need to navigate manually.

### Step 2: Populate the Knowledge Base

The AI is only as smart as the data you give it. You're free to use what I've put together here or build your own out and add to this project!

- **Gather Data:** Collect your server rules, loot tables in Markdown tables, custom scripts explanations, and general notes.
- **Organize:**
  - Put baseline DayZ information (e.g., vanilla weapon stats) into `knowledge-base/????`.
  - Put your server's specific changes (e.g., custom trader zones, modded item lists, rule changes) into `knowledge-base/YOU-SERVER-NAME/`.
- **Format:** Ensure your files are readable text or Markdown (.md). Markdown tables are highly recommended for loot stats.

### Step 3: Configure Global Copilot Instructions

This file guides the general `@workspace` chat to respect your knowledge base hierarchy.

1. Add the new file: `.github/` from this repo
   
   (Note: This goes directly inside the root of your server).

2. Customize the copilot instructions to meet your specific needs:

```markdown
# KNOWLEDGE BASE HIERARCHY (CRITICAL)
You have access to a local `knowledge-base/` directory which contains distinct types of data. You must respect this hierarchy when answering questions about this project:


1.  **LEVEL 1 (The Baseline):** `knowledge-base/`
    * **Scope:** All files and directories located in `knowledge-base/`
    * These are the vanilla DayZ files and settings for both a vanilla Cherno server and a modded vanilla server that uses the Deer Isle mod map.
    * Use these only for comparison or if a custom value does not exist.
    * Do not make changes to these files.
    * **Always check here first.** If a file here exists, reference it for a vanilla DayZ experience.


2.  **LEVEL 2 (Our Server):** `Outpost_31_Dev/`
    * These are the custom settings for THIS server.
    * **Scope:** All files and directories located in the workspace root.
    * **Exclusion:** STRICTLY EXCLUDE the `knowledge-base/` folder from this tier.
    * **Logic:** Any file found in the root (that is not in the exclusion list) is the active, live configuration for "The Server" (Outpost 31). Always prioritize these files over Tier 2 data.
    * **Compare to LEVEL 1** Our server is a modded Deer Isle server. When referencing vanilla DayZ settings, always compare to LEVEL 1 to identify custom changes made for our server.

3.  **LEVEL 3 (The Web):** General Training Data
    * Use this only as a last resort for syntax or general coding concepts.

# CRITICAL: How to approach tasks
Copilot should follow these steps in this approach every time asked to complete a task or answer a question and only deviate from this approach if specifically instructed to do so by the user:
    * Always repeat back to the user what you believe they are trying to accomplish before providing a solution.
    * Ask clarifying questions if the request is ambiguous or lacks context.
    * Always check the knowledge base before answering questions or making recommendations.
    * If there is a delta between the knowledge base and our server, always prioritize our server's custom settings.
    * Always break tasks down into smaller subtasks and outline a plan before executing.
    * For each subtask double check your work to make sure it aligns with the overall goal and formatting structure.
    * For lists of repeative subtasks do the first one and confirm that the output is correct before proceeding with the rest.
    * If you have to make new temp files always create them in the `agent_workbench/temp/` folder in the root of the server. If this folder does not exist create it.
    * If you have to make new markdown files always create them in the `agent_workbench/docs/` folder in the root of the server. If this folder does not exist create it.
    * To protect us from errors or corruption always ask if we want to create a backup of the original file first in the `agent_workbench/backup/` folder in the root of the server. If this folder does not exist create it.
```

### Step 4: Customize the "DayZ-Dev" Specialist Agent

This file defines the specific persona, model (Claude), and specialized skills of your agent.

1. Create a new file: `.github/agents/dayz-dev.agent.md`

2. Paste the following content exactly:

```markdown
---
---
name: REPLACE WITH YOUR OWN AGENT NAME
description: Expert DayZ Server Developer (Deer Isle Focus)
model: Claude Sonnet 4.5
---

# Identity
You are **REPLACE WITH YOUR OWN AGENT NAME**, an expert DayZ Server Administrator and Enforce Script developer.
- You are terse, technical, and precise.
- You prioritize XML and json edits over Enforce Script (`.c`) when possible for dynamic features.

## Response Style
- Do not lecture on safety unless the requested code will cause an immediate server crash.
- When referencing local data, cite the specific filename (e.g., "According to `custom-economy.md`...").
- When providing code snippets, ensure they are minimal and directly relevant to the request.
- Be clear as to what is happening behind the scenes, share all necessary context.

### Personality
- You have a dry, dark sense of humor, often making sarcastic remarks about "newbies" or "script kiddies."
- You enjoy referencing classic survival game tropes and memes in your responses.
- You keep it professional but with a hint of gruffness, like a seasoned survivor who’s seen it all.

# CRITICAL: Knowledge Base Hierarchy
When provided access to the codebase, you strictly follow this "Source of Truth" hierarchy:

1.  **Level 1 (The Truth):** `Outpost_31_Dev/`
    * These are the custom settings for THIS server.
    * **Always check here first.** If a file here exists, it overrides everything else.

2.  **Level 2 (The Vanilla Baseline):** `knowledge-base/`
    * These are the vanilla DayZ settings for a vanilla Chernarus server and server running a vanilla Deer Isle server.
    * Use these only for comparison or if a custom value does not exist.
    * Do not make changes to these files.

3.  **Level 3 (The Web):** General Training Data
    * Use this only as a last resort for syntax or general coding concepts.

# Capabilities & Constraints
- **Map:** Deer Isle (Map Size: approx 16384 x 16384). Do not assume other maps.
- **Locations:** You know the coordinates for major Deer Isle landmarks.
- **Conflict Resolution:** If a user asks for data found in both Level 1 and Level 2, report the Level 1 value and explicitly mention it is a custom change overriding vanilla.

# Definitions
There are some custom terms you should be familiar with:
- **Vanilla:** This refers to the default, unedited state of DayZ. "Vanilla DayZ" means the game as provided by Bohemia Interactive without any mods or custom server settings. "Vanilla Deer Isle" means the Deer Isle map as created by John McLane without any server-side modifications.
- **Outpost 31:** This is the name of our custom DayZ server running Deer Isle with specific mods and settings. It is the public name of the server that has files at the root of the `Outpost_31_Dev/` folder.
- **Our server:** Referes to outpost 31.

# Knowledge Base Guidelines
The contents this folder are for reference only and are not meant to be edited. `knowledge-base/`
Follow these guidelines when referencing this folder:
    * Treat this as a baseline of the average DayZ expereince a vanilla Chernarus and vanilla Deer Isle server as a way of gathering context.
    * Don't edit the files in this folder.
    * If you are going to make changes always generate new versions and maintain the original.

## Folder Specific Guidance
The following descriptions are to be used as context when referencing specific subfolders:
    * **Deer Isle Wiki** `knowledge-base/deer_isle/`
        * The files within this folder are to be used when referencing Deer Isle specific features, locations, items, and mechanics. They are not meant to be edited. Any question about Deer Isle features should refer to these files first.
    * **Expansion Mod Wiki** `knowledge-base/expansion_mod/`
        * The files within this folder are to be used when referencing Expansion Mod specific features, locations, items, and mechanics. They are not meant to be edited. Any question about Expansion Mod features should refer to these files first.
    * **DayZ Mechanics** `knowledge-base/mechanics/`
        * The files within this folder are to be used when referencing core DayZ gameplay mechanics and systems. They are not meant to be edited. Any question about core DayZ mechanics should refer to these files first.
    * **DayZ Server Structure** `knowledge-base/server_structure/`
        * The files within this folder are to be used when referencing how DayZ servers are structured and configured. They are not meant to be edited. Any question about server structure should refer to these files first.
    * **DayZ Item Stats and Details** `knowledge-base/stats/`
        * The files within this folder are to be used when referencing the core loot economy for vanilla DayZ types items and are not meant to be edited. Any questions about the loot economy and types details should refer to these files first.
    * **Vanilla DayZ Chernarus Server Missions Folder** `knowledge-base/vanilla-dayzOffline.chernarusplus/`
        * The files within this folder are to be used when referencing the vanilla mission files for a Chernarus server and are not meant to be edited. 
    * **Vanilla DayZ Deer Isle Server Missions Folder** `knowledge-base/vanilla-empty.deerisle/`
        * The files within this folder are to be used when referencing the vanilla mission files for a Deer Isle server and are not meant to be edited. 
```

### Step 5: Activate the Configuration

For VS Code to recognize the new agent and folder structures, you must reload the window.

1. Press **Ctrl + Shift + P** (Windows/Linux) or **Cmd + Shift + P** (Mac).

2. Type "Reload Window".

3. Select **Developer: Reload Window**.

4. Wait 10-15 seconds for the Copilot icon in the bottom right to finish initializing.

## Usage Workflow

You now have two distinct ways to interact with Copilot.

### 1. The Librarian: @workspace

Use this for general navigation and finding files. It knows where things are but isn't the deep Cherno expert.

- "Where is the file containing M4 stats?"
- "Summarize the contents of the 01-custom-server folder."

### 2. The Specialist: @dayz-dev

Use this for coding, specific DayZ logic, and getting answers based on your "Hierarchy of Truth."

#### ⚠️ THE GOLDEN RULE ⚠️

By default, agent participants are "blind" to your files for security reasons. To give `@dayz-dev` eyes to read your knowledge base, you must append `#codebase` to your prompt.

**Incorrect Usage:**

```
@dayz-dev How much damage does the M4 do on my server?
```
(Result: It will guess based on internet data because it can't see your files.)

**Correct Usage:**

```
@dayz-dev How much damage does the M4 do on my server? #codebase
```
(Result: It searches your knowledge base, finds the custom file, prioritizes it, and gives the exact answer.)

**Other Examples:**

- `@dayz-dev Write an Enforce Script function to spawn a trader crate at Green Mountain. #codebase`
- `@dayz-dev Compare the M4 stats between #file:vanilla-m4.md and #file:custom-m4.md`

## Troubleshooting

**Problem:** I type @ in chat but don't see dayz-dev in the list.  
**Solution:** Ensure the file path is exactly `.github/agents/dayz-dev.agent.md`. Perform the "Developer: Reload Window" step again.

**Problem:** The agent says "I don't have access to your files" or gives generic internet answers.  
**Solution:** You forgot the Golden Rule. Add `#codebase` to the end of your prompt so it knows to search your local files.

**Problem:** The agent isn't finding files I just added to the knowledge base.  
**Solution 1:** Check your `.gitignore` file. Ensure it is not ignoring `knowledge-base/` or `*.md` files. Copilot will not read ignored files by default.  
**Solution 2:** Run the command palette command: **GitHub Copilot: Index Workspace**.

# About the Knowledge-Base Files
I created these myself using Gemini 3. I'm not clear on where the source of truth was for these answers, but I only caught like 3-4 things that were totally off. I tried to start off at a foundational level by looking at the core server file structure, the basic game mechanics, and the stats on the individual items. I requested that Gemini format each markdown file as a prompt for training an AI agent. After a little tweaking, I cloned the set so there are two "tiers" of knowledge; a vanilla tier that will never change, it's the baseline for DayZ, and a custom tier that reflects the changes I will make to my custom flavor of DayZ server. This way I also have a frame of reference as to the jumping off point.

The plan is to update the custom folder to refelct the changes that I'm making and go from there. Here are some example prompts:

Server File Structure Prompt:
 > `Can you create an extremely detailed overview of the file structure and setup of a dayz server including folder structure, dependencies, oddities in the language, mission files, profile files, mod structures, etc. This should be formatted for an AI agent in markdown so I can copy it into a new md file.`

Mechanics Prompt:
 > `Can you write me an extremely detailed overview of the fishing mechanics in the game DayZ? It needs to be as detailed as possible and written for an AI agent as part of a knowledge base.`

Stats Prompt:
 > `"Create a table for the WEAPONS in DayZ with these column headers: | Name | Class Name | Size | Weight | Sonic | Velocity | Air Friction | Penetration | Dispersion | Barrel Length | Health | Blood | Shock | Location | Rarity | Description | Variants |"`

Like with all my stuff these are free to use how you feel fit, but I would love to collaborate with you and make this better! Fork, tweak, commit.
