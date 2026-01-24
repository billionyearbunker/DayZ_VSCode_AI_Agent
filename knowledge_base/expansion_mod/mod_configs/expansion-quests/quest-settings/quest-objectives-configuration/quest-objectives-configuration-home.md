# Quest Objectives Configuration

---

## File Information

You can name an objective configuration file to whatever you want as long as it has the `.json` file extension and is placed in the related objective configurations folder.

---

## Main Objective Configuration Parameters

### **`ConfigVersion`**
- **Type**: Integer
- **Description**: Current config file version. NEVER CHANGE THIS!

---

### **`ID`**
- **Type**: Integer
- **Description**: Unique objective ID. Make sure this ID is different for every single objective in this objective category! You can use the same ID for a different objective configuration in a different objective category but never use the same ID in the same category twice!

---

### **`ObjectiveType`**
- **Type**: Integer
- **Description**: Objective Type of this objective configuration. As every objective type uses and handles different parameters and values we need to tell the system what kind of objective this is. It always needs to be the category where the config file is located

**Objective Types**:
- `TARGET = 2`
- `TRAVEL = 3`
- `COLLECT = 4`
- `DELIVERY = 5`
- `TREASUREHUNT = 6`
- `AIPATROL = 7`
- `AICAMP = 8`
- `AIVIP = 9`
- `ACTION = 10`
- `CRAFTING = 11`

---

## Objective Type Descriptions

There are different objective types that all do something different when added to a quest and every objective has a different configuration depending on the objective type:

- **TARGET**: Quest player/s will need to kill a certain amount of mobs/players. (Optional: With a special weapon)
- **TRAVEL**: Quest player/s will need to go to location XY
- **COLLECT**: Quest player/s will need to collect/find a certain amount of items
- **DELIVERY**: The Quest player/s will need to deliver given items to a certain position and NPC
- **TREASUREHUNT**: Quest player/s will need to find a location containing a stashed treasure
- **AIPATROL**: Quest player/s will need to clear an AI patrol. (Optional: With a special weapon)
- **AICAMP**: Quest player/s will need to clear an AI Camp. (Optional: With a special weapon)
- **AIVIP**: Quest player/s will need to protect and escort an AI to a certain location
- **ACTION**: Quest player/s will need to execute a certain Action
- **CRAFTING**: Quest player/s will need to craft certain items

---

### **`ObjectiveText`**
- **Type**: String
- **Description**: The objective text will be displayed in the quest log and quest hud when the objective is active and displayed

---

### **`TimeLimit`**
- **Type**: Integer
- **Description**: The time limit in seconds the quest player/s has to complete this objective. This should be set and added in the quest configuration file containing this objective in its objectives array as it allows you to reuse it in other quests with different time limit values or without one

---

### **`Active`**
- **Type**: Boolean
- **Description**: Enable/disable this objective configuration file from being loaded by the quest system

---

## Specific Objective Configuration Pages

- **Action Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Action-Objective-Configuration
- **AI Camp Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/AI-Camp-Objective-Configuration
- **AI Patrol Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/AI-Patrol-Objective-Configuration
- **AI VIP Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/AI-VIP-Objective-Configuration
- **Collection Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Collection-Objective-Configuration
- **Crafting Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Crafting-Objective-Configuration
- **Delivery Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Delivery-Objective-Configuration
- **Target Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Target-Objective-Configuration
- **Travel Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Travel-Objective-Configuration
- **Treasure Hunt Objective Configuration**: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/Treasure-Hunt-Objective-Configuration
