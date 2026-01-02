# 📚 Knowledge Base

### What is this?
This directory acts as the **"Source of Truth"** for the DayZ AI Developer Agent. It contains all the documentation, statistics, and rules the AI needs to write accurate, context-aware code for your specific server.

### Why is it important?
* **Prioritization:** It ensures the AI prioritizes your local documentation over general internet knowledge, which may be outdated or incorrect.
* **Context:** It gives the agent "eyes" to see your specific server changes, preventing it from hallucinating features that don't exist.
* **Safety:** It helps the agent write safer, more accurate Enforce Script (`.c`) by understanding the specific boundaries of your project.

### How is it set up?
The Knowledge Base is split into two distinct tiers to establish a strict "Hierarchy of Truth":

* **`00-vanilla-reference/` (Tier 2):** Contains the baseline game information and vanilla statistics. This serves as the unchangeable foundation of DayZ.
* **`01-custom-server/` (Tier 1):** Contains your specific server changes, such as modified loot tables or custom scripts. **This folder overrides everything else.**

### How does it work?
The AI is instructed to follow a strict hierarchy when answering questions:
1.  **Check Tier 1 (`01-custom-server`) first.** If a file exists here, it is treated as the "Supreme Truth."
2.  **Check Tier 2 (`00-vanilla-reference`) second.** This is used only for comparison or if a custom value does not exist.
3.  **Conflict Resolution:** If data exists in both folders, the AI is explicitly instructed to report the Tier 1 value and note that it overrides the vanilla baseline.

### How were these files generated?
These files were not handwritten; they were developed using **Gemini 3** to act as training prompts for an AI agent.
* **Creation Process:** The author requested detailed overviews of file structures, mechanics (like fishing), and weapon statistics, formatted specifically for AI consumption.
* **Cloning:** The set was originally created as a baseline and then "cloned" to create the two tiers. The `01-custom-server` folder started as a copy of the vanilla files, intended to be updated as you modify your specific server.
