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