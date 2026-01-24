# Adding Custom Airdrops

## Creating the File

Go to `mpmissions\dayzOffline.<mapname>\expansion\missions` in your server directory and create a file named `Airdrop_<yourcustomname>.json` e.g.

```
Airdrop_MyCustomDrop.json
```

**Important:** The file name must start with `Airdrop_`!

---

## Configuring the File

You can configure your file in two different ways:

### A) Random Airdrops

Random airdrops will take a random container (airdrop type) from the `airdropsettings.json` (from your server `profile/expansionmod/settings/`) and will use this file as a new potential location to spawn one of the configured crates from the `airdropsettings.json`. This solution is very useful if you want to have one place with all the loot configured and one place for all the airdrop locations instead of configuring all your new airdrops with the same loot all over again.

### B) Unique Airdrop

Unique Airdrop will have everything configured inside your new file: loot, amount of zombies, crate skin and so on. If you want to do a "unique" airdrop at a specific location, this method is more likely the one you are looking for.

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
                    "Attachments": [
                        "BandageDressing": 0.5,
                        "SalineBagIV": 1.0
                    ],
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
"Weight"
How important is this airdrop, the bigger the number is, the more likely it will be picked. If you want this airdrop to be rare take a smaller number compared to the other airdrops !

"MissionMaxTime"
How long this airdrop could stay on the map until it despawn? It's in seconds.

"MissionName"
String. Currentlty useless since missions are only used for airdrops but will be used in the futur to create multiple categories for missions.

"Difficulty"
Unused at the moment. Keep it at 0

"Objective"
Unused at the moment. Keep it at 0

"Reward"
String. Unused at the moment. Keep it empty

"ShowNotification"
Bool. If set to 1, this specific airdrop will notify players with a notification if notifications are not disabled in NotificationSettings.json !

"Height"
Float. The altitude the plane will fly at.

"Speed"
Float. The speed of the plane.

"Container"
String. What container will be used for the airdrop. By default you can choose between :

ExpansionAirdropContainer_Military
ExpansionAirdropContainer_Basebuilding
ExpansionAirdropContainer_Medical
ExpansionAirdropContainer
Please note, if Loot (below) is empty and the name is "Random", it will ignore all the parameters and will use randomly one of the presets configured in your airdropsettings.json

"DropLocation"
Array. Where the airdrop will be dropped, what name will be displayed in the notification "Airdrop have been dropped at MyNameHere" and the radius is where the airdrop should land around the coordinates given.

"Loot"
What loot could spawn inside the airdrop. You have to give the Name of the Classname, his chance of spawning (1.00 = 100%) and his attachements if you want it to spawn with items attached to it. Please make sure the last } of the loot list doesn't have the , in }, like in the example !

In a quick glance, this is how it can look like.

{
    "Name": "My_ClassName",
    "Attachments": [],
    "Chance": 0.5,
    "QuantityPercent": -1,
    "Max": 10,
    "Variants": []
}
"Loot" => "QuantityPercent"
-2 => will use the quantmin and quantmax of this item from your types.xml
-1 => will default to 100% quantity of that item (full mag, full water bottle, 99 nails, etc)
0 to 100 => how full the item is in percentage. ( Desired Quantity / Max Quantity ) * 100 = QuantityPercent
But if we want to go more complex with attachments on the items and variants (so we don't write the same config for the same item but with different colors for example)

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
            "Attachments": [
                "classname_withaCommaAtTheEnd": MyChance,
                "classname_withoutCommaAtTheEndBecauseItsTheLastOne": MyChance
            ],
            "Chance": 0.13157899677753449
        },
        {
            "Name": "My_ClassName",
            "Attachments": [
                "classname_withaCommaAtTheEnd": 1.0,
                "classname_withoutCommaAtTheEndBecauseItsTheLastOne": 0.5
            ],
            "Chance": 0.13157899677753449
        }
    ]
}
"Infected"
A list of AI that will spawn around the airdrop once landed. Zombies or Animals for example.

To spawn AI bots when using the DayZ-Expansion-AI mod, specify each string like this (example):

"eAI_SurvivorM_Mirek|faction:Mercenaries,loadout:BanditLoadout,canbelooted:false"

"ItemCount"
The amount of items the airdrop will have in it

"InfectedCount"
The amount of Zombies around the airdrop
