# What Is This?

This mod adds a simple skill perk tree to the game.

It's inspired by Terje's Syberia and Skills mods. The main difference with my mod is I wanted a lightweight skills mod which doesn't influence PVP as much.

If you want a proper full-on MMO style experience, check out Terje's mods - if you just want a reason for players to invest in their characters over the long-term and feel a sense of progression without changing core gameplay much, check my mod out.

The skill perks in my mod are mainly basic survival perks - such as getting an extra log from trees, having a longer lasting heat buff, being able to track animals etc.

**Key Features:**
- Fully customizable perk rewards via JSON config
- Translated with stringtables (feel free to modify for non-English servers)
- Compatible with most mods (tested with Expansion and Terje's Medicine mod)

---

## Installation Instructions

1. Install this mod like any other mod - copy it into your server folder and add it to your mods list
2. Copy the `.bikey` into your server keys (unless using OmegaManager which does this automatically)

**Important Notes:**
- This mod must be run on both **client and server**
- A wipe is recommended (affects persistent storage of minor items like fruit and predator meat)
- Player data is stored in a separate database
- Backup your storage folder before installation if not wiping
- Optional `types.xml` file included for skill-related items (EXP boost injector, skill books, etc.)

> **NOTE:** This mod is not included in ZenModPack as it's a niche mod. Add it separately if needed.

---

## JSON Files

Configuration files are located in `profiles/Zenarchist/Skills/`

### Core Files

- **`ZenSkillsConfig.json`** - Broad mod config (skill perk rewards, EXP boost injector settings, etc.)
- **`ZenSkillsEXP.json`** - EXP rewards for in-game actions and recipes
- **`ZenSkillsHighscoresDB.json`** - Highscores tracking (optional, can be disabled)

### Additional Files

- **`Analytics/`** - Analytics on average EXP gains per skill across server sessions
- **`PlayerDB/`** - Player database (don't modify unless overriding player skills)
- **`ZenSkillsEXP_ExpansionQuests.json`** - Auto-generated if Expansion Quests mod is detected

Full JSON configuration guides are provided below.

---

## Repack

You can repack this mod if you like, and do anything else you want with it for that matter. Just keep in mind my future updates won't be applied so make sure to check back for new versions if you notice any bugs.

---

## Learn Modding

Want to learn how to make your own mods? Check out my guides on YouTube: https://www.youtube.com/@Zenarchist

---

## Bug Reports

Report any bugs on my GitHub bug tracker: https://github.com/ZenarchistCode/ZenModPack/issues

---

## Buy Me A Coffee

All my mods are free and open source, but it takes an enormous amount of time to put some of these mods together. If I've helped you out, please consider helping me buy my next coffee! I don't expect it, but I very much appreciate it.

https://buymeacoffee.com/zenarchist

---

## Enjoy!

---

# Configuration Guides

## ZenSkillsConfig.json Guide

> Copy & paste into Notepad++ with line wrap enabled and save as `.json` for better readability.

```json
{
    "CONFIG_VERSION": "1",
    "ServerConfig": {
        "DebugJumpEXP": 500, // How much EXP to randomly reward a player when they jump in-game in debug mode
        "AutoSaveTimerSecs": 900, // Timer for saving player DB (player-specific and triggered upon login to stagger file writes)
        "BaseHandDrillKitSuccess": 0.4000000059604645, // Base chance to succeed with hand drill fire kit if no hand drill kit perks active
        "EnableAnalytics": 1, // Turns on/off the analytics dumps
        "EnableDatabaseCache": 1, // Don't touch this - this is for internal testing. Won't break anything but recommended to leave on unless your server has 100+ players coming and going in a session and you run into RAM problems
        "ShareExpRange": 0, // This is how many meters to share EXP amongst nearby players (apprenticeship EXP gain)
        "ShareExpMulti": 0.5, // This is the % multiplier of shared EXP (0.5 = 50% EXP rate shared to nearby players)
        "I_AM_USING_MAPLINK": 0 // Turn this on if you're using ZenMapLink - compatibility PBOs are included in ZenMapLink's folder
    },
    "SharedConfig": {
        "DebugMode": 0, // Turn on/off debug mode: LEAVE OFF ON YOUR LIVE SERVER! This will allow any player to gain EXP etc and print tons of logs
        "ShowExpHudOnLeft": 0, // By default the EXP perks and gained progress bar display on the right of screen - set this to 1 to move it to left
        "AllowHighscores": 1, // Enable/disable highscores feature
        "AllowResetPerks": 1, // Enable/disable allowing players to reset their perks from within the Skill GUI (if disabled, they either can never reset them, or they need a Perk Reset Injector)
        "EXP_InjectorBoostMulti": 2.0, // EXP boost from the EXP boost injector
        "EXP_InjectorBoostTime": 1800.0, // How long the boost lasts in seconds (injectors stack - so if you spawn a lot of them, maybe make this number lower)
        "PercentOfExpLostOnDeath": 0.05000000074505806 // How much % of all EXP is lost when player respawns. Set to 1.0 to wipe all perks and EXP on death
    },
    "SkillDefs": { // List of the default skill configs
        "survival": {
            "DisplayName": "#STR_ZenSkills_Name_Survival",
            "Description": "#STR_ZenSkills_Desc_Survival",
            "StartingEXP": 0, // EXP on a fresh character
            "EXP_Per_Perk": 1000, // EXP required to unlock each perk
            "EXP_Perk_Modifier": 0.009999999776482582, // How much EXP gain is reduced per perk unlocked (to slow progression at higher levels)
            "EXP_Refund_Modifier": 0.5, // How much EXP is refunded when reset from within the skill GUI (0-1 - 0.5 = 50%)
            "MaxAllowedPerks": 20, // Max allowed perks unlocked in any given skill at any given time (20 means the player will have 10 perks they can never unlock and must choose wisely)
            "Perks": {
                "4_1": { // 4_1 means "top row, first perk". 4_2 means "top row, second perk" and so on.
                    "DisplayName": "#STR_ZenSkills_Perk_Survival_Name9",
                    "Description": "#STR_ZenSkills_Perk_Survival_Desc9",
                    "RewardSymbol": "%", // Reward symbol in the text on GUI
                    "MinPerksRequiredFromPrevTier": 1, // Minimum perks required unlocked on lower tier before this tier unlocks - 1 means the player must have at least 1 level 3 perk unlocked before level 4 will be enabled
                    "Rewards": [
                        5.0, // Each unlock tier's reward - every skill perk has 3 tiers. This setting means 5%, 10%, 15% based on tier unlocked.
                        10.0,
                        15.0
                    ]
                }
            }
        }
    },
    "Analytics_AvgTotalExpGainedPerSession": {} // Don't touch this - for internal use of mod.
}
```

---

## ZenSkillsEXP.json Guide

> Copy & paste into Notepad++ with line wrap enabled and save as `.json` for better readability.

```json
{
    "CONFIG_VERSION": "1",
    "ExpNerfConfig": {
        "GlobalExpMultiplier": 1.0, // Global modifier for all EXP gained (eg. 2.0 = 2x EXP gain)
        "EnableExpNerf": 1, // Enable/disable the repeated action nerf
        "NerfBubbleMaxActions": 25, // Max number of the SAME action which can be performed before nerf kicks in
        "NerfBubbleRadiusMeters": 100.0, // Size of the bubble the nerf applies in - player must move 100m+ to reset nerf. Designed to prevent base camping grinding skills
        "NerfActionResetTimeMs": 600000.0, // Miliseconds before nerf resets without leaving the bubble (eg. this is 1 hour)
        "NerfPercentPerActionInBubble": 0.009999999776482582, // How much EXP is lost PER action while camping nerf is activated
        "NerfPercentPerActionRepeat": 0.009999999776482582, // How much EXP is lost PER action while repeating the same action within bubble
        "NerfMaxForBubbleAction": 0.5, // Maximum % nerf for EXP. 0.5 means 50% is the most you can be nerfed
        "NerfMaxForRepeatAction": 0.5 // Ditto
    },
    "ExpDefs": {
        "survival": { // Skill key
            "ExpDefs": {
                "CraftSalineBagIV": { // Action classname, or Recipe classname.
                    "EXP": 25, // How much EXP to award for this action/recipe
                    "AllowModifier": 0, // Some actions can have a boost multiplier to their EXP rewarded - eg. if an action takes longer to perform while this is enabled, the player will gain more EXP, and some special actions are affected too, like hunting EXP for animal kills is boosted based on distance of killshot
                    "ApplyNerf": 1, // Enable/disable the nerf impact on this action
                    "ApplyBoosts": 1 // Enable/disable the EXP booster's impact on this action
                }
			}
		}
	}
}
```

---

## ZenSkillsEXP_ExpansionQuests.json Guide

> Copy & paste into Notepad++ with line wrap enabled and save as `.json` for better readability.

```json
{
    "CONFIG_VERSION": "1",
    "ExpDefs": {
        "survival": { // Skill key
            "ExpDefs": {
                "ExpansionQuest_17": { // Quest ID: Must follow this format (ExpansionQuest_ID)
                    "EXP": 100, // How much EXP to reward
                    "AllowModifier": 0, // Not used
                    "ApplyNerf": 0, // Not used
                    "ApplyBoosts": 0 // Not used
                }
			}
		}
	}
}
```

---

# Repacking / Source Code

All my mods are open-source and published under the **Mozilla Public License Version 2.0**. Any mods based on my code must be open-source - **no obfuscation!**

You can modify/reupload/repack my mods if you like, but please:
- Credit any original authors/3D model/3rd-party asset creators
- Keep in mind any future updates I make will not be automatically applied to repacked mods
- Check back from time to time for bugfixes and improvements

If you find my mods useful, please consider buying me a coffee - it's not expected but very much appreciated:

https://buymeacoffee.com/zenarchist