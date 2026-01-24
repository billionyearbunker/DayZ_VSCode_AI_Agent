# Quest Settings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Current setting file version. **NEVER CHANGE THIS!**

---

### **`EnableQuests`**
- **Type**: Boolean
- **Description**: Enable\disable the quest system

---

### **`EnableQuestLogTab`**
- **Type**: Boolean
- **Requirements**: Only used if the Expansion-Book mod is loaded next to the quest mod
- **Description**: Enable\disable the book quest log tab

---

### **`CreateQuestNPCMarkers`**
- **Type**: Boolean
- **Requirements**: Only used if the Expansion-Navigation mod is loaded next to the quest mod
- **Description**: Set server map markers on the quest NPC spawn locations
- **Status**: NOT WORKING AT THIS POINT. SUBJECT TO CHANGE!

---

### **`QuestAcceptedTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest is accepted

---

### **`QuestAcceptedText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest is accepted

---

### **`QuestCompletedTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest is completed

---

### **`QuestCompletedText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest is completed

---

### **`QuestFailedTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest is failed

---

### **`QuestFailedText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest is failed

---

### **`QuestCanceledTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest is canceled

---

### **`QuestCanceledTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest is canceled

---

### **`QuestTurnInTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest is turned-in

---

### **`QuestTurnInText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest is turned-in

---

### **`QuestObjectiveCompletedTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest objective is completed

---

### **`QuestObjectiveCompletedText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest objective is completed

---

### **`AchivementCompletedTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a achivement quest is completed

---

### **`AchivementCompletedText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a achivement quest is completed

---

### **`WeeklyQuestResetDay`**
- **Type**: String
- **Description**: Day name in english when the weekly quest reset should happend

---

### **`WeeklyQuestResetHour`**
- **Type**: Integer
- **Description**: Hour at when the quest reset will happend for all weekly quests

---

### **`WeeklyQuestResteMinute`**
- **Type**: Integer
- **Description**: Minute at when the quest reset will happend for all weekly quests

---

### **`DailyQuestResetHour`**
- **Type**: Integer
- **Description**: Hour at when the quest reset will happend for all daily quests

---

### **`DailyQuestResetMinute`**
- **Type**: Integer
- **Description**: Minute at when the quest reset will happend for all daily quests

---

### **`UseUTCTime`**
- **Type**: Boolean
- **Description**: Use UTC server time or not for all quest cooldown and reset times

---

### **`QuestCooldownTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a quest is on cooldown

---

### **`QuestCooldownText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a quest is on cooldown

---

### **`QuestNotInGroupTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a group quest is accepted without beeing in a group

---

### **`QuestNotInGroupText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a group quest is accepted without beeing in a group

---

### **`QuestNotGroupOwnerTitle`**
- **Type**: String
- **Description**: Text that will displayed in the notification title field when a group quest is accepted/turned-in and the player is not the group owner

---

### **`QuestNotGroupOwnerText`**
- **Type**: String
- **Description**: Text that will displayed in the notification text field when a group quest is accepted/turned-in and the player is not the group owner

---

### **`GroupQuestMode`**
- **Type**: Integer
- **Description**: Controls how group quests can be accepted and turned in

**Valid Values:**
- `0` - Only group owners can accept and turn-in group quests
- `1` - Only group owner can turn-in group quest but all group members can accept them
- `2` - All group members can accept and turn-in group quests

---

## Example Configuration

```json
{json
{
    "m_Version": 10,
    "EnableQuests": 1,
    "EnableQuestLogTab": 1,
    "CreateQuestNPCMarkers": 1,
    "QuestAcceptedTitle": "Quest Accepted",
    "QuestAcceptedText": "The quest %1 has been accepted!",
    "QuestCompletedTitle": "Quest Completed",
    "QuestCompletedText": "All objectives of the quest %1 have been completed",
    "QuestFailedTitle": "Quest Failed",
    "QuestFailedText": "The quest %1 failed!",
    "QuestCanceledTitle": "Quest Canceled",
    "QuestCanceledText": "The quest %1 has been canceled!",
    "QuestTurnInTitle": "Quest Turn-In",
    "QuestTurnInText": "The quest %1 has been completed!",
    "QuestObjectiveCompletedTitle": "Objective Completed",
    "QuestObjectiveCompletedText": "You have completed the objective %1 of the quest %2.",
    "QuestCooldownTitle": "Quest Cooldown",
    "QuestCooldownText": "This quest is still on cooldown! Come back in %1",
    "QuestNotInGroupTitle": "Group Quest",
    "QuestNotInGroupText": "Group quests can only be accepted while in a group!",
    "QuestNotGroupOwnerTitle": "Group Quest",
    "QuestNotGroupOwnerText": "Only a group owner can accept and turn-in a group quest!",
    "GroupQuestMode": 0,
    "AchievementCompletedTitle": "Achievement \"%1\" completed!",
    "AchievementCompletedText": "%1",
    "WeeklyResetDay": "Wednesday",
    "WeeklyResetMinute": 0,
    "WeeklyResetHour": 8,
    "DailyResetHour": 8,
    "DailyResetMinute": 0,
    "UseUTCTime": 0,
    "UseQuestNPCIndicators": 1,
    "MaxActiveQuests": 5
}
```
