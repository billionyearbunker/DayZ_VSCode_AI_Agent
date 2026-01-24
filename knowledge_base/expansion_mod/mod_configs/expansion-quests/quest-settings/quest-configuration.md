# Quest Configuration

---

## File Information

You can name a quest configuration file to whatever you want as long as it has the `.json` file extension and is placed in the quest configurations folder it will get loaded by the quest system.

---

## Configuration Parameters

### **`ConfigVersion`**
- **Type**: Integer
- **Description**: Current config file version. Please don't change this unless you know what you are doing!

---

### **`ID`**
- **Type**: Integer
- **Description**: Unique quest ID. Make sure this ID is different for every single quest

---

### **`Type`**
- **Type**: Integer
- **Description**: Quest type from ExpansionQuestType enumeration. Only use type 1 for all quests
- **Values**: `NORMAL = 1`

---

### **`Title`**
- **Type**: String
- **Description**: Quest title

---

### **`Descriptions`**
- **Type**: Array
- **Description**: Should have only max. 3 entries in the array! Each index has its own use in the system
- **Array Indexes**:
  - `0` - Description of getting the quest
  - `1` - Description while the quest is active (only visible at the given quest NPCs)
  - `2` - Description when taking in quest (only visible at the given quest turn-in NPC)

---

### **`ObjectiveText`**
- **Type**: String
- **Description**: Short objective description text

---

### **`FollowUpQuest`**
- **Type**: Integer
- **Description**: Follow-up Quest ID. If this quest has a follow quest you need to add the quest ID of the follow-up quest here so it will be automatically shared with the player when he completes the pre-quest

---

### **`Repeatable`**
- **Type**: Boolean
- **Description**: Quest is a repeatable quest

---

### **`IsDailyQuest`**
- **Type**: Boolean
- **Description**: Quest is a daily quest and has a daily reset

---

### **`IsWeeklyQuest`**
- **Type**: Boolean
- **Description**: Quest is a weekly quest and has a weekly cooldown

---

### **`CancelQuestOnPlayerDeath`**
- **Type**: Boolean
- **Description**: The quest will be canceled if the quest player (or one of his group members when it's a group quest) dies

---

### **`Autocomplete`**
- **Type**: Boolean
- **Description**: Quest will be autocompleted when all quest objectives are completed

---

### **`IsGroupQuest`**
- **Type**: Boolean
- **Description**: Quest is a group quest

---

### **`ObjectSetFileName`**
- **Type**: String
- **Description**: Can be used to spawn a set of objects when a quest player starts a certain quest. Add the file name of the `.map` file that will get loaded without the `.map` extension
- **Location**: The `.map` file needs to be located in the mission directory at: `MISSION.MAPNAME/expansion/quests/objects`

---

### **`QuestItems`**
- **Type**: Array<ExpansionQuestItemConfig>
- **Description**: Quest items that the player will receive when starting the quest. These items get deleted from the quest player/s when the quest is canceled/completed or the player logs out/server restarts. If the player reconnects the items get added back to the quest players as long as the quest is not completed

**Example**:
```json
{
    "ClassName": "SledgeHammer",
    "Amount": 1
}
```

**Sub-Parameters**:
- **`ClassName`** (String): The class name of the quest item
- **`Amount`** (Integer): How many units/items should the player get of the item?

---

### **`Rewards`**
- **Type**: Array<ExpansionQuestRewardConfig>
- **Description**: Quest rewards that the player will receive when turning in the quest and all objectives are completed

**Example**:
```json
{
  "ClassName": "TaloonBag_Blue",
  "Amount": 1,
  "Attachments": [],
  "DamagePercent": 0,
  "QuestID": -1,
  "Chance": 1.0
}
```

**Sub-Parameters**:
- **`ClassName`** (String): The class name of the reward item
- **`Amount`** (Integer): How many units/items should the player get of the item?
- **`Attachments`** (Array): Attachments that will be applied to the main reward item given
- **`DamagePercent`** (Integer): The damage percent value of the reward item the player will get. Damage is also applied to the attachments
- **`QuestID`** (Integer): If the item should be usable and turn out a certain quest then add the quest ID of that quest here to make the reward item a quest giver item
- **`Chance`** (Float): Only used if the `RandomReward` parameter is set to 1 (true). Sets the chance of the reward to be selected when the quest is completed and the rewards are selected randomly

---

### **`NeedToSelectReward`**
- **Type**: Boolean
- **Description**: If enabled and there are multiple rewards for the quest in the rewards array the player needs to select one reward when he turns in the quest from the given rewards

---

### **`RandomReward`**
- **Type**: Boolean
- **Description**: If enabled and there are multiple rewards for the quest in the rewards array then random rewards will be selected on quest completion based on the given reward chances and the amount of reward items to spawn set in the `RandomRewardAmount` parameter

---

### **`RandomRewardAmount`**
- **Type**: Integer
- **Description**: Amount of randomly selected reward items each quest player will get on quest completion when the `RandomReward` parameter is enabled and there are multiple rewards for the quest in the rewards array

---

### **`RewardsForGroupOwnerOnly`**
- **Type**: Boolean
- **Description**: If enabled and the quest is a group quest only the group owner (quest owner) will receive the rewards added to the Rewards array

---

### **`QuestGiverIDs`**
- **Type**: Array
- **Description**: Unique quest NPC IDs from the quest NPC configuration of the NPCs that will head out the quest

---

### **`QuestTurnInIDs`**
- **Type**: Array
- **Description**: Unique quest NPC IDs from the quest NPC configuration of the NPCs that will turn in the quest when completed

---

### **`IsAchivement`**
- **Type**: Boolean
- **Description**: Quest is an achievement quest and gets added to new players when they join the server for the first time automatically

---

### **`Objectives`**
- **Type**: Array<ExpansionQuestObjectiveConfigBase>

Quest objectives that the player needs to complete to complete the whole quest and to get the quest rewards if there is a reward defined. Take a look at the objectives configuration page for further information.

{
    "ConfigVersion": 21,
    "ID": 3,
    "ObjectiveType": 3
}
"ConfigVersion" Integer. The same configuration version is used in the quest objective configuration files.
"ID" Integer. Objective ID from the objective configuration.
"ObjectiveType" Integer. Objective Type from the objective configuration.
TARGET = 2
TRAVEL = 3
COLLECT = 4
DELIVERY = 5
TREASUREHUNT = 6
AIPATROL = 7
AICAMP = 8
AIESCORT = 9
ACTION = 10
CRAFTING = 11
"QuestColor"
Integer. The main color of the quest will be used to display it in the menus and quest HUD.

"ReputationReward"
Integer.

Only used if the Hardline mod is loaded and the "UseReputation" setting in the HardlineSettings.JSON is enabled. Reputation reward the quest players will receive on quest completion.

"ReputationRequirement"
Integer.

Only used if the Hardline mod is loaded and the "UseReputation" setting in the HardlineSettings.JSON is enabled. Reputation points are needed to see and accept the quest next to other requirements like completed pre-quests.

"PreQuestIDs"
Array.

Pre-Quest Quest IDs. If this quest requires other quests to be completed before it can be displayed/accepted add the quest IDs of the quests that have to be completed first here.

"RequiredFaction"
String.

Only used if the AI mod is loaded. Name of the Expansion-AI faction the player needs to be in to see/accept/complete this quest.

"FactionReward"
String.

Only used if the AI mod is loaded. Name of the Expansion-AI faction the player will join as a reward for completing this quest.

"PlayerNeedQuestItems"
Boolean.

Controls if the quest will be canceled if the quest players are missing one of the quest items on relog/reconnection.

"DeleteQuestItems"
Boolean.

Controls if the quest items will be deleted when the quest is completed or not. They still always get deleted when the quest is canceled!

"SequentialObjectives"
Boolean.

Controls if the configured quest objectives need to be completed in sequential order or if they are all active and can be completed all the time when the quest is active.

"FactionReputationRequirements"
Map<String, integer>.

This map controls how many reputation points are needed for certain factions to see and start the quest.

"FactionReputationRequirements": {
        "Survivors": 500
    },
"FactionReputationRewards"
Map<String, integer>.

This map controls how many reputation points the player gets for certain factions on quest completion as a reward.

"FactionReputationRewards": {
        "Survivors": 500
    }
"SuppressQuestLogOnCompetion"
Boolean.

Suppressed display of the quest log on quest completion when the quest configuration has no "QuestGiverIDs" set.

"Active"
Boolean.

Enable/disable this configuration file from being loaded my the quest system.

Example configuration JSON file:

{
    "ConfigVersion": 21,
    "ID": 2,
    "Type": 1,
    "Title": "A favor for Steve...",
    "Descriptions": [
        "So, Peter sends you, hmm? Well I have what he wants, although he still owes me something... But I'm also not a bad guy. Let's say if you do me a favor, too, I'll give you what Peter wants and even more. I gotta keep watch and make sure no shit happens around here. I want you to take this sledgehammer and clean up the village with it. There are a few Infected that have to be eliminated before they start moving into the camp.",
        "You are not done yet? How hard can it be to smash some heads with that hammer... Come back when the job is done!",
        "Oh there you are! I thought the Infected got your ass and killed you... Well, here is your reward."
    ],
    "ObjectiveText": "Kill 10 civilian Infected with Steve's sledgehammer.",
    "FollowUpQuest": 3,
    "Repeatable": 0,
    "IsDailyQuest": 0,
    "IsWeeklyQuest": 0,
    "CancelQuestOnPlayerDeath": 0,
    "Autocomplete": 0,
    "IsGroupQuest": 0,
    "ObjectSetFileName": "",
    "QuestItems": [
        {
            "ClassName": "SledgeHammer",
            "Amount": 1
        }
    ],
    "Rewards": [
        {
            "ClassName": "WaterBottle",
            "Amount": 1,
            "Attachments": [],
            "DamagePercent": 0,
            "HealthPercent": 0,
            "QuestID": -1,
            "Chance": 1.0
        },
        {
            "ClassName": "TunaCan",
            "Amount": 1,
            "Attachments": [],
            "DamagePercent": 0,
            "HealthPercent": 0,
            "QuestID": -1,
            "Chance": 1.0
        }
    ],
    "NeedToSelectReward": 0,
    "RandomReward": 0,
    "RandomRewardAmount": 0,
    "RewardsForGroupOwnerOnly": 1,
    "QuestGiverIDs": [
        2
    ],
    "QuestTurnInIDs": [
        2
    ],
    "IsAchievement": 0,
    "Objectives": [
        {
            "ConfigVersion": 26,
            "ID": 2,
            "ObjectiveType": 3
        },
        {
            "ConfigVersion": 26,
            "ID": 1,
            "ObjectiveType": 2
        }
    ],
    "QuestColor": 0,
    "ReputationReward": 0,
    "ReputationRequirement": -1,
    "PreQuestIDs": [
        1
    ],
    "RequiredFaction": "",
    "FactionReward": "",
    "PlayerNeedQuestItems": 1,
    "DeleteQuestItems": 1,
    "SequentialObjectives": 1,
    "FactionReputationRequirements": {},
    "FactionReputationRewards": {},
    "SuppressQuestLogOnCompetion": 0,
    "Active": 1
}
```

---

## Special Quest Configurations

There are certain different quest configurations that change the behavior or handling of the quest with different results.

### Auto-Start Quest

An Auto-start quest will be added to the player on the first server connection.

We need to have the following parameter values to work as intended:

```json
"QuestGiverIDs": [], //! Make sure the quest has no "QuestGiverIDs" in the array!
"IsAchivement": 0, //! Make sure the quest is not flagged as an achievement quest!
"IsGroupQuest": 0, //! Make sure the quest is not flagged as a group quest!
"PreQuestIDs": [] //! Make sure the quest has no "PreQuestIDs" in the array!
```
```

---

### Achievement Quest

An Achievement quest will get added to the player on the first server connection but the difference here is that the player will never be notified about this quest except when he completes the quest (all quest objectives completed).

We need to have the following parameter values to work as intended:

```json
"QuestGiverIDs": [], //! Make sure the quest has no quest giver IDs!
"IsAchivement": 1, //! Make sure the quest is flagged as an achievement quest!
"Autocomplete": 1, //! Make sure the quest is auto-completed when all quest objectives are completed!
"IsGroupQuest": 0, //! Make sure the quest is not flagged as a group quest!
"PreQuestIDs": [] //! Make sure the quest has no "PreQuestIDs" in the array!
```
```

---

### Daily Quest

Daily quests can be completed once per day and then set on a cooldown until the server's daily quest reset happens the next day. The server's daily reset time is controlled by the quest settings [LINK TO SETTING].

We need to have the following parameter values to work as intended:

```json
"Repeatable": 1, //! Make sure the quest is repeatable!
"IsDailyQuest": 1,
"IsWeeklyQuest": 0, //! Make sure it's only a daily or weekly quest!
```
```

---

### Weekly Quest

Weekly quests can be completed once per week and then set on a cooldown until the server's weekly quest reset happens on the next week. The server's weekly reset time and day are controlled by the quest settings [LINK TO SETTING].

We need to have the following parameter values to work as intended:

```json
"Repeatable": 1, //! Make sure the quest is repeatable!
"IsDailyQuest": 0, //! Make sure it's only a daily or weekly quest!
"IsWeeklyQuest": 1,
```
