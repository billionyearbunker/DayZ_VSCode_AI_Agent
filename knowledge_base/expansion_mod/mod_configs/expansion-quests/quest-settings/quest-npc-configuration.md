# Quest NPC Configuration

---

## File Information

You can name a quest npc configuration file to whatever you want as long as it has the `.json` file extension and is placed in the quest npc configurations folder it will get loaded by the quest system.

---

## Main Objective Configuration Parameters

### **`ConfigVersion`**
- **Type**: Integer
- **Description**: Current config file version. **NEVER CHANGE THIS!**

---

### **`ID`**
- **Type**: Integer
- **Description**: Unique NPC ID. Make sure this ID is different for every single NPC configuration!

---

### **`ClassName`**
- **Type**: String
- **Description**: NPC Class name to use for this NPC. There are several different default types provided by the quest mod

**Default NPC types**:
- ExpansionQuestNPCMirek
- ExpansionQuestNPCDenis
- ExpansionQuestNPCBoris
- ExpansionQuestNPCCyril
- ExpansionQuestNPCElias
- ExpansionQuestNPCFrancis
- ExpansionQuestNPCGuo
- ExpansionQuestNPCHassan
- ExpansionQuestNPCIndar
- ExpansionQuestNPCJose
- ExpansionQuestNPCKaito
- ExpansionQuestNPCLewis
- ExpansionQuestNPCManua
- ExpansionQuestNPCNiki
- ExpansionQuestNPCOliver
- ExpansionQuestNPCPeter
- ExpansionQuestNPCQuinn
- ExpansionQuestNPCRolf
- ExpansionQuestNPCSeth
- ExpansionQuestNPCTaiki
- ExpansionQuestNPCLinda
- ExpansionQuestNPCMaria
- ExpansionQuestNPCFrida
- ExpansionQuestNPCGabi
- ExpansionQuestNPCHelga
- ExpansionQuestNPCIrena
- ExpansionQuestNPCJudy
- ExpansionQuestNPCKeiko
- ExpansionQuestNPCEva
- ExpansionQuestNPCNaomi
- ExpansionQuestNPCBaty

**Default AI NPC types** (Only usable if the Expansion-AI mod is loaded):
- ExpansionQuestNPCAIMirek
- ExpansionQuestNPCAIDenis
- ExpansionQuestNPCAIBoris
- ExpansionQuestNPCAICyril
- ExpansionQuestNPCAIElias
- ExpansionQuestNPCAIFrancis
- ExpansionQuestNPCAIGuo
- ExpansionQuestNPCAIHassan
- ExpansionQuestNPCAIIndar
- ExpansionQuestNPCAIJose
- ExpansionQuestNPCAIKaito
- ExpansionQuestNPCAILewis
- ExpansionQuestNPCAIManua
- ExpansionQuestNPCAINiki
- ExpansionQuestNPCAIOliver
- ExpansionQuestNPCAIPeter
- ExpansionQuestNPCAIQuinn
- ExpansionQuestNPCAIRolf
- ExpansionQuestNPCAISeth
- ExpansionQuestNPCAITaiki
- ExpansionQuestNPCAILinda
- ExpansionQuestNPCAIMaria
- ExpansionQuestNPCAIFrida
- ExpansionQuestNPCAIGabi
- ExpansionQuestNPCAIHelga
- ExpansionQuestNPCAIIrena
- ExpansionQuestNPCAIJudy
- ExpansionQuestNPCAIKeiko
- ExpansionQuestNPCAIEva
- ExpansionQuestNPCAINaomi
- ExpansionQuestNPCAIBaty

**Default static object types**:
- ExpansionQuestObjectBoard
- ExpansionQuestBoardSmall
- ExpansionQuestBoardLarge
- ExpansionQuestObjectLocker

---

### **`Position`**
- **Type**: Vector
- **Description**: Position of the NPC to be spawned in the world after the server starts

---

### **`Orientation`**
- **Type**: Vector
- **Description**: The orientation of the NPC is to be set when he gets spawned after the server starts

---

### **`NPCName`**
- **Type**: String
- **Description**: NPC name that gets displayed on the action

---

### **`DefaultNPCText`**
- **Type**: String
- **Description**: Default text that is displayed in the quest menu when interacting with this NPC and there are no quests available for the player

---

### **`Waypoints`**
- **Type**: Array
- **Requirements**: Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure `IsAI` is set to 1!
- **Description**: Should contain the NPCs position as the first waypoint entry! NPC will follow the waypoint path if there is more than one waypoint configured

---

### **`NPCEmoteID`**
- **Type**: Integer
- **Requirements**: Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure `IsAI` is set to 1!
- **Description**: NPC Emote ID the NPC will play randomly sometimes

**Available Emote IDs**:
- `ID_EMOTE_GREETING = 1`
- `ID_EMOTE_SOS = 2`
- `ID_EMOTE_HEART = 3`
- `ID_EMOTE_TAUNT = 4`
- `ID_EMOTE_LYINGDOWN = 5`
- `ID_EMOTE_TAUNTKISS = 6`
- `ID_EMOTE_FACEPALM = 7`
- `ID_EMOTE_TAUNTELBOW = 8`
- `ID_EMOTE_THUMB = 9`
- `ID_EMOTE_THROAT = 10`
- `ID_EMOTE_SUICIDE = 11`
- `ID_EMOTE_DANCE = 12`
- `ID_EMOTE_CAMPFIRE = 13`
- `ID_EMOTE_SITA = 14`
- `ID_EMOTE_SITB = 15`
- `ID_EMOTE_THUMBDOWN = 16`
- `ID_EMOTE_DABBING = 32`
- `ID_EMOTE_TIMEOUT = 35`
- `ID_EMOTE_CLAP = 39`
- `ID_EMOTE_POINT = 40`
- `ID_EMOTE_SILENT = 43`
- `ID_EMOTE_SALUTE = 44`
- `ID_EMOTE_RPS = 45`
- `ID_EMOTE_WATCHING = 46`
- `ID_EMOTE_HOLD = 47`
- `ID_EMOTE_LISTENING = 48`
- `ID_EMOTE_POINTSELF = 49`
- `ID_EMOTE_LOOKATME = 50`
- `ID_EMOTE_TAUNTTHINK = 51`
- `ID_EMOTE_MOVE = 52`
- `ID_EMOTE_DOWN = 53`
- `ID_EMOTE_COME = 54`
- `ID_EMOTE_RPS_R = 55`
- `ID_EMOTE_RPS_P = 56`
- `ID_EMOTE_RPS_S = 57`
- `ID_EMOTE_NOD = 58`
- `ID_EMOTE_SHAKE = 59`
- `ID_EMOTE_SHRUG = 60`
- `ID_EMOTE_SURRENDER = 61`
- `ID_EMOTE_VOMIT = 62`
- `ID_EMOTE_DEBUG = 1000`

---

### **`NPCEmoteIsStatic`**
- **Type**: Boolean
- **Requirements**: Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure `IsAI` is set to 1!
- **Description**: NPC Emote ID the NPC will play. Forces the NPC into this animation and he will never change it

---

### **`NPCLoadoutFile`**
- **Type**: String
- **Description**: Loadout file name from the expansion loadout's folder that should get applied to the NPC if it is a normal or AI NPC. NPC will spawn with the configured geat from the given loadout file

---

### **`NPCInteractionEmoteID`**
- **Type**: Integer
- **Requirements**: Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure `IsAI` is set to 1!
- **Description**: NPC Emote ID the NPC will play when interacting with him

---

### **`NPCQuestCancelEmoteID`**
- **Type**: Integer
- **Requirements**: Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure `IsAI` is set to 1!
- **Description**: NPC Emote ID the NPC will play when a quest is canceled

"NPCQuestStartEmoteID"
Integer.

Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure "IsAI" is set to 1! NPC Emote ID the NPC will play when a quest is started/accepted.

"NPCQuestCompleteEmoteID"
Integer.

Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure "IsAI" is set to 1! NPC Emote ID the NPC will play when a quest is completed.

---

### **`NPCFaction`**
- **Type**: String
- **Requirements**: Only used if the NPC is an AI type and the Expansion-AI mod is loaded next to the quest mod. Make sure `IsAI` is set to 1!
- **Description**: Controls the faction of the NPC. Need to be the faction name

---

### **`NPCType`**
- **Type**: Integer
- **Description**: NPC type to set the right spawn event for the NPC. Need to be set correctly depending on the entity class type used for the NPC set in the `ClassName` parameter

**Valid Values:**
- `NORMAL = 0` - Normal NPC type
- `OBJECT = 1` - Object type
- `AI = 2` - AI NPC type

---

### **`Active`**
- **Type**: Boolean
- **Description**: Enable/disable this configuration file from being loaded by the quest system

---

## Example Configuration

```json
{
    "ConfigVersion": 6,
    "ID": 1,
    "ClassName": "ExpansionQuestNPCAIDenis",
    "Position": [
        3706.27001953125,
        402.0119934082031,
        5987.080078125
    ],
    "Orientation": [
        282.0,
        0.0,
        0.0
    ],
    "NPCName": "Peter",
    "DefaultNPCText": "Hmm?",
    "Waypoints": [
        [
            3706.27001953125,
            402.0119934082031,
            5987.080078125
        ]
    ],
    "NPCEmoteID": 46,
    "NPCEmoteIsStatic": 0,
    "NPCLoadoutFile": "NBCLoadout",
    "NPCInteractionEmoteID": 1,
    "NPCQuestCancelEmoteID": 60,
    "NPCQuestStartEmoteID": 58,
    "NPCQuestCompleteEmoteID": 39,
    "NPCFaction": "InvincibleObservers",
    "NPCType": 2,
    "Active": 1
}
```
