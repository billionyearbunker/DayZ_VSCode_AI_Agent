# DayZ Cherno AI Developer Agent for Visual Studio Code

This repository contains the configuration files needed to turn Visual Studio Code's GitHub Copilot into a specialized, context-aware AI developer for DayZ servers, specifically focused on the Chernarus map.

By setting up this agent, you get an AI assistant that:

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
  ├── .github/                 <-- Hidden folder for Copilot configs
  │   └── agents/              <-- Folder specifically for agent definitions
  │
  └── knowledge-base/          <-- Your "Source of Truth" documentation
      ├── 00-vanilla-reference/ <-- Baseline game info (optional but recommended)
      └── 01-custom-server/     <-- YOUR custom changes (Highest Priority)
```

**Tip:** On Windows, the `.github` folder might be hidden by default. Ensure you can see hidden files if you need to navigate manually.

### Step 2: Populate the Knowledge Base

The AI is only as smart as the data you give it.

- **Gather Data:** Collect your server rules, loot tables in Markdown tables, custom scripts explanations, and general notes.
- **Organize:**
  - Put baseline DayZ information (e.g., vanilla weapon stats) into `knowledge-base/00-vanilla-reference/`.
  - Put your server's specific changes (e.g., custom trader zones, modded item lists, rule changes) into `knowledge-base/01-custom-server/`.
- **Format:** Ensure your files are readable text or Markdown (.md). Markdown tables are highly recommended for loot stats.

### Step 3: Configure Global Copilot Instructions

This file guides the general @workspace chat to respect your knowledge base hierarchy.

Create a new file: .github/copilot-instructions.md

(Note: This goes directly inside .github/, NOT inside the agents/ subfolder).

Paste the following content exactly:
# KNOWLEDGE BASE HIERARCHY (CRITICAL)
You have access to a local `knowledge-base/` directory which contains distinct types of data. You must respect this hierarchy when answering questions about this project:

1.  **TIER 1 (Supreme Truth):** Files in `knowledge-base/01-custom-server/`.
    * These are OUR specific server changes. They override EVERYTHING.
    * If the user asks "How does X work on *my* server?", look here first.

2.  **TIER 2 (Baseline Reference):** Files in `knowledge-base/00-vanilla-reference/`.
    * These represent the standard game files.
    * Use these ONLY if the specific feature is NOT defined in Tier 1, or for comparison.

3.  **TIER 3 (General Knowledge):** Your training data/Internet.
    * Use this only if the answer is not found in Tier 1 or Tier 2.
  
Step 4: Create the "DayZ-Dev" Specialist Agent

This file defines the specific persona, model (Claude), and specialized skills of your agent.

Create a new file: .github/agents/dayz-dev.agent.md

Paste the following content exactly:
---
name: dayz-dev
description: Expert DayZ Server Developer (Chernarus Focus)
model: claude-4.5-sonnet
---

# Identity
You are **DayZ-Dev**, an expert DayZ Server Administrator and Enforce Script developer.
- You are terse, technical, and precise.
- You prioritize Enforce Script (`.c`) over XML edits when possible for dynamic features.

# CRITICAL: Knowledge Base Hierarchy
When provided access to the codebase, you strictly follow this "Source of Truth" hierarchy:

1.  **TIER 1 (The Truth):** `knowledge-base/01-custom-server/`
    * These are the custom settings for THIS server.
    * **Always check here first.** If a file here exists, it overrides everything else.

2.  **TIER 2 (The Baseline):** `knowledge-base/00-vanilla-reference/`
    * These are the vanilla DayZ statistics.
    * Use these only for comparison or if a custom value does not exist.

3.  **TIER 3 (The Web):** General Training Data
    * Use this only as a last resort for syntax or general coding concepts.

# Capabilities & Constraints
- **Map:** Chernarus (Map Size: approx 15360 x 15360). Do not assume other maps.
- **Locations:** You know the coordinates for major Chernarus landmarks (NWAF, Tisy, Green Mountain, etc.).
- **Conflict Resolution:** If a user asks for data found in both Tier 1 and Tier 2, report the Tier 1 value and explicitly mention it is a custom change overriding vanilla.

# Response Style
- Do not lecture on safety unless the requested code will cause an immediate server crash.
- When referencing local data, cite the specific filename (e.g., "According to `custom-economy.md`...").

Step 5: Activate the Configuration

For VS Code to recognize the new agent and folder structures, you must reload the window.

Press Ctrl + Shift + P (Windows/Linux) or Cmd + Shift + P (Mac).

Type "Reload Window".

Select Developer: Reload Window.

Wait 10-15 seconds for the Copilot icon in the bottom right to finish initializing.

Usage Workflow
You now have two distinct ways to interact with Copilot.

1. The Librarian: @workspace

Use this for general navigation and finding files. It knows where things are but isn't the deep Cherno expert.

"Where is the file containing M4 stats?"

"Summarize the contents of the 01-custom-server folder."

2. The Specialist: @dayz-dev

Use this for coding, specific DayZ logic, and getting answers based on your "Hierarchy of Truth."

⚠️ THE GOLDEN RULE ⚠️

By default, agent participants are "blind" to your files for security reasons. To give @dayz-dev eyes to read your knowledge base, you must append #codebase to your prompt.

Incorrect Usage:

@dayz-dev How much damage does the M4 do on my server? (Result: It will guess based on internet data because it can't see your files.)

Correct Usage:

@dayz-dev How much damage does the M4 do on my server? #codebase (Result: It searches your knowledge base, finds the custom file, prioritizes it, and gives the exact answer.)

Other Examples:

@dayz-dev Write an Enforce Script function to spawn a trader crate at Green Mountain. #codebase

@dayz-dev Compare the M4 stats between #file:vanilla-m4.md and #file:custom-m4.md

Troubleshooting
Problem: I type @ in chat but don't see dayz-dev in the list. Solution: Ensure the file path is exactly .github/agents/dayz-dev.agent.md. Perform the "Developer: Reload Window" step again.

Problem: The agent says "I don't have access to your files" or gives generic internet answers. Solution: You forgot the Golden Rule. Add #codebase to the end of your prompt so it knows to search your local files.

Problem: The agent isn't finding files I just added to the knowledge base. Solution 1: Check your .gitignore file. Ensure it is not ignoring knowledge-base/ or *.md files. Copilot will not read ignored files by default. Solution 2: Run the command palette command: GitHub Copilot: Index Workspace.
