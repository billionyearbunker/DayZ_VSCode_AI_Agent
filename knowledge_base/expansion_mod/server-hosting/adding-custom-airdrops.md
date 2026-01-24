# Adding custom airdrops

---

## Creating the file

Go to `mpmissions\dayzOffline.<mapname>\expansion\missions` in your server directory and create a file named `Airdrop_<yourcustomname>.json` e.g.

`Airdrop_MyCustomDrop.json`

**Important**: It is important that the file name starts with `Airdrop_`!

---

## Configuring the file

You can configure your file in two different ways:

**A) Random airdrops** will take a random container (airdrop type) from the airdropsettings.json (from your server profile/expansionmod/settings/) and will use this file as a new potential location to spawn one of the configured crate from the airdropsettings.json. This solution is very useful if you want to have one place with all the loot configured and one place for all the airdrop locations instead of configuring all your new airdrops with the same loot all over again.

**B) Unique Airdrop** will have everything configured inside your new file: loot, amount of zombies, crate skin and so on. If you want to do a "unique" airdrop at a specific location, this method is more likely the one you are looking for.

---

## A) Random Airdrop

Inside your `Airdrop_Random_MyLocation.json` file you just created, copy and paste the following lines:

```json
{
    "Enabled": 1,
    "Weight": 294.0,
    "MissionMaxTime": 1200,
    "MissionName": "Random_MyLocation",
    "Difficulty": 0,
    "Objective": 0,
    "Reward": "",
    "ShowNotification": 1,
    "Height": 450.0,
    "Speed": 25.0,
    "Container": "Random",
    "DropLocation": {
        "x": 5043.0,
        "z": 2505.0,
        "Name": "My Location Name I will display on the notification",
        "Radius": 100.0
    },
    "Loot": [],
    "Infected": [],
    "ItemCount": -1,
    "InfectedCount": -1
}
```

---

## B) Unique Airdrop

Inside your `Airdrop_MyCustomDrop.json` file you just created, copy and paste the following lines:

```json
{
    "Enabled": 1,
    "Weight": 294.0,
    "MissionMaxTime": 1200,
    "MissionName": "MyCustomDrop",
    "Difficulty": 0,
    "Objective": 0,
    "Reward": "",
    "ShowNotification": 1,
    "Height": 450.0,
    "Speed": 25.0,
    "Container": "ExpansionAirdropContainer",
    "DropLocation": {
        "x": 5043.0,
        "z": 2505.0,
        "Name": "My Location Name I will display on the notification",
        "Radius": 100.0
    },
    "Loot": [
        {
            "Name": "AKS74U",
            "Attachments": [
                "AKS74U_Bttstck"
            ],
            "Chance": 0.07999999821186066,
            "QuantityPercent": -1,
            "Max": -1,
            "Variants": []
        },
        {
            "Name": "FirstAidKit",
            "Attachments": [
                "BandageDressing",
                "BandageDressing",
                "BandageDressing",
                "BandageDressing",
                "BandageDressing",
                "BandageDressing"
            ],
            "Chance": 0.3799999952316284,
            "QuantityPercent": -1,
            "Max": -1,
            "Variants": [
                {
                    "Name": "FirstAidKit",
                    "Attachments": {
                        "BandageDressing": 0.5,
                        "SalineBagIV": 1.0
                    },
                    "Chance": 0.13157899677753449
                },
                {
                    "Name": "FirstAidKit",
                    "Attachments": [],
                    "Chance": 0.13157899677753449
                }
            ]
        },
        {
            "Name": "Bear_Pink",
            "Attachments": [],
            "Chance": 0.70,
            "QuantityPercent": -1,
            "Max": 2,
            "Variants": []
        }
    ],
    "Infected": [
        "ZmbM_HermitSkinny_Beige",
        "ZmbM_HermitSkinny_Black",
        "ZmbM_HermitSkinny_Green",
        "ZmbM_HermitSkinny_Red"
    ],
    "ItemCount": 30,
    "InfectedCount": 25
}
```

---

## Configuration Parameters

### **`Weight`**

- **Type**: Float
- **Description**: How important is this airdrop. The bigger the number is, the more likely it will be picked. If you want this airdrop to be rare, take a smaller number compared to the other airdrops!

### **`MissionMaxTime`**

- **Type**: Integer
- **Description**: How long this airdrop could stay on the map until it despawns. It's in seconds

### **`MissionName`**

- **Type**: String
- **Description**: Currently useless since missions are only used for airdrops but will be used in the future to create multiple categories for missions

### **`Difficulty`**

- **Type**: Integer
- **Description**: Unused at the moment. Keep it at 0

### **`Objective`**

- **Type**: Integer
- **Description**: Unused at the moment. Keep it at 0

### **`Reward`**

- **Type**: String
- **Description**: Unused at the moment. Keep it empty

### **`ShowNotification`**

- **Type**: Bool
- **Description**: If set to 1, this specific airdrop will notify players with a notification if notifications are not disabled in NotificationSettings.json!

### **`Height`**

- **Type**: Float
- **Description**: The altitude the plane will fly at

### **`Speed`**

- **Type**: Float
- **Description**: The speed of the plane

### **`Container`**

- **Type**: String
- **Description**: What container will be used for the airdrop
- **Values**: By default you can choose between:
  - `ExpansionAirdropContainer_Military`
  - `ExpansionAirdropContainer_Basebuilding`
  - `ExpansionAirdropContainer_Medical`
  - `ExpansionAirdropContainer`

**Note**: If Loot (below) is empty and the name is "Random", it will ignore all the parameters and will use randomly one of the presets configured in your airdropsettings.json

### **`DropLocation`**

- **Type**: Array
- **Description**: Where the airdrop will be dropped, what name will be displayed in the notification "Airdrop have been dropped at MyNameHere" and the radius is where the airdrop should land around the coordinates given

### **`Loot`**

- **Type**: Array
- **Description**: What loot could spawn inside the airdrop. You have to give the Name of the Classname, his chance of spawning (1.00 = 100%) and his attachments if you want it to spawn with items attached to it

**Note**: Please make sure the last `}` of the loot list doesn't have the `,` in `},` like in the example!

**Simple Example:**

```json
{
    "Name": "My_ClassName",
    "Attachments": [],
    "Chance": 0.5,
    "QuantityPercent": -1,
    "Max": 10,
    "Variants": []
}
```

### **`Loot`** => **`QuantityPercent`**

- **Type**: Integer
- **Values**:
  - `-2` = will use the quantmin and quantmax of this item from your types.xml
  - `-1` = will default to 100% quantity of that item (full mag, full water bottle, 99 nails, etc)
  - `0 to 100` = how full the item is in percentage. `(Desired Quantity / Max Quantity) * 100 = QuantityPercent`

**Complex Example with Attachments and Variants:**

```json
{
    "Name": "My_ClassName",
    "Attachments": [
        "classname_withaCommaAtTheEnd",
        "classname_withaCommaAtTheEnd",
        "classname_withoutCommaAtTheEndBecauseItsTheLastOne"
    ],
    "Chance": 0.07,
    "QuantityPercent": -1,
    "Max": -1,
    "Variants": [
        {
            "Name": "My_ClassName",
            "Attachments": {
                "classname_withaCommaAtTheEnd": MyChance,
                "classname_withoutCommaAtTheEndBecauseItsTheLastOne": MyChance
            },
            "Chance": 0.13157899677753449
        },
        {
            "Name": "My_ClassName",
            "Attachments": {
                "classname_withaCommaAtTheEnd": 1.0,
                "classname_withoutCommaAtTheEndBecauseItsTheLastOne": 0.5
            },
            "Chance": 0.13157899677753449
        }
    ]
}
```

### **`Infected`**

- **Type**: Array [String]
- **Description**: A list of AI that will spawn around the airdrop once landed. Zombies or Animals for example

**AI Bot Example**: To spawn AI bots when using the DayZ-Expansion-AI mod, specify each string like this:

`"eAI_SurvivorM_Mirek|faction:Mercenaries,loadout:BanditLoadout,canbelooted:false"`

### **`ItemCount`**

- **Type**: Integer
- **Description**: The amount of items the airdrop will have in it

### **`InfectedCount`**

- **Type**: Integer
- **Description**: The amount of Zombies around the airdrop
