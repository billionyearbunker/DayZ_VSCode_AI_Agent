# Setting up Trader Entities and NPCs

---

## Overview

All trader entities/NPCs need to be configured using .map files in the following directory:

```
mpmissions/dayzoffline.<MapName>/expansion/traders/MyTrader.map
```

**Important**: If you want to use the DayZ-Expansion-AI for trader NPCs, be aware that AI traders have a higher performance impact than static NPCs.

---

## File Format

The file is a simple text file that needs to follow our .map file format (see below).
- The file name can be whatever you want
- Every trader entity/NPC needs an entry (one line per trader entity) in one or several .map files

### Format Structure

```
<TraderEntityClassName>.<TraderFileName>|<Position>|<Orientation>|<Gear>
```

### Example

```
ExpansionTraderDenis.Weapons|11833.576 140.605 12469.492|110 0 0|Jeans_Blue,TSHirt_Blue
```

---

## Parameter Descriptions

### **`TraderEntityClassName`**
- **Description**: This is the entity/NPC classname (in this example `ExpansionTraderDenis`)
- **Note**: Scroll down to see a list of all the default expansion trader NPC's we provide

---

### **`TraderFileName`**
- **Description**: This is the trader configuration file name (in this example `Weapons`), without the JSON extension, that controls what the trader sells/buys
- **Format**: It is separated from the trader entity class name with a dot (`.`), much like a file extension, but is the trader file's base name instead
- **Requirement**: The TraderFileName parameter here needs to be the same as one of the configured trader JSON files from the trader settings folder (`ExpansionMod\Traders`)
- **Reference**: For further information, please take a look at our Wiki page about the trader settings: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-Trader-Settings

---

### **`Position`**
- **Description**: Either a single position vector or a list of vectors (delimited by commas `,`) aka waypoints
- **Note**: Waypoints will only work if the entity is an AI trader
- **Reminder**: DayZ 3D world uses the Y axis as the height/elevation axis. Use tools such as dayz editor, community online tools, vanilla plus plus admin tools to get these 3D positions

---

### **`Orientation`**
- **Description**: Single vector. The direction the trader entity/NPC will be facing

---

### **`Gear`**
- **Description**: List of items that should be in the trader entity's inventory (i.e. clothes), delimited by comma (`,`)
- **Attachments**: Attachments on items are possible by separating them from the main item with plus signs `+`

**Example**:
```
ExpansionTraderDenis.Weapons|11833.576 140.605 12469.492|110 0 0|Jeans_Blue,TSHirt_Blue,AKM+Mag_AKM_30Rnd+KobraOptic
```

### Special Keywords

You can use special keywords instead of or in addition to gear to influence some properties of a trader.

**Example** - Set trader name to "Mark" and use the loadout "MyTraderLoadout":
```
ExpansionTraderDenis.Weapons|11833.576 140.605 12469.492|110 0 0|name:Mark,loadout:MyTraderLoadout
```

**For AI traders** - You can also assign a different faction:
```
ExpansionTraderAIDenis.Weapons|11833.576 140.605 12469.492|110 0 0|name:Mark,loadout:MyTraderLoadout,faction:Guards
```

---

## List of Default Trader Entities

### Static Trader Entities

- `ExpansionTraderPumpkin`
- `ExpansionTraderZucchini`
- `ExpansionExchangeMachine`
- `ExpansionTraderLockerClosedBlueV1`
- `ExpansionTraderLockerClosedBlueV2`
- `ExpansionTraderLockerClosedBlueV3`
- `ExpansionTraderLockerClosedV1`
- `ExpansionTraderLockerClosedV2`
- `ExpansionTraderLockerClosedV3`

### Static Trader NPCs

- `ExpansionTraderMirek`
- `ExpansionTraderDenis`
- `ExpansionTraderBoris`
- `ExpansionTraderCyril`
- `ExpansionTraderElias`
- `ExpansionTraderFrancis`
- `ExpansionTraderGuo`
- `ExpansionTraderHassan`
- `ExpansionTraderIndar`
- `ExpansionTraderJose`
- `ExpansionTraderKaito`
- `ExpansionTraderLewis`
- `ExpansionTraderManua`
- `ExpansionTraderNiki`
- `ExpansionTraderOliver`
- `ExpansionTraderPeter`
- `ExpansionTraderQuinn`
- `ExpansionTraderRolf`
- `ExpansionTraderSeth`
- `ExpansionTraderTaiki`
- `ExpansionTraderLinda`
- `ExpansionTraderMaria`
- `ExpansionTraderFrida`
- `ExpansionTraderGabi`
- `ExpansionTraderHelga`
- `ExpansionTraderIrena`
- `ExpansionTraderJudy`
- `ExpansionTraderKeiko`
- `ExpansionTraderEva`
- `ExpansionTraderNaomi`
- `ExpansionTraderBaty`

### AI Trader NPCs

- `ExpansionTraderAIMirek`
- `ExpansionTraderAIDenis`
- `ExpansionTraderAIBoris`
- `ExpansionTraderAICyril`
- `ExpansionTraderAIElias`
- `ExpansionTraderAIFrancis`
- `ExpansionTraderAIGuo`
- `ExpansionTraderAIHassan`
- `ExpansionTraderAIIndar`
- `ExpansionTraderAIJose`
- `ExpansionTraderAIKaito`
- `ExpansionTraderAILewis`
- `ExpansionTraderAIManua`
- `ExpansionTraderAINiki`
- `ExpansionTraderAIOliver`
- `ExpansionTraderAIPeter`
- `ExpansionTraderAIQuinn`
- `ExpansionTraderAIRolf`
- `ExpansionTraderAISeth`
- `ExpansionTraderAITaiki`
- `ExpansionTraderAILinda`
- `ExpansionTraderAIMaria`
- `ExpansionTraderAIFrida`
- `ExpansionTraderAIGabi`
- `ExpansionTraderAIHelga`
- `ExpansionTraderAIIrena`
- `ExpansionTraderAIJudy`
- `ExpansionTraderAIKeiko`
- `ExpansionTraderAIEva`
- `ExpansionTraderAINaomi`
- `ExpansionTraderAIBaty`
