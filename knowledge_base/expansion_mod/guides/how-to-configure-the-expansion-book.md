# How to configure the Expansion Book

---

## Table of Contents

- Server Informations Tab
  - Side Buttons
  - Server Description
  - Server Settings
- Server Rules Tab
  - How to create your own rules
- Crafting Recipes Tab
  - How to add new recipes (crafts)
- Other tabs

---

## Tab Configuration

### **`EnableStatusTab`**

- **Type**: Boolean
- **Description**: This setting allows you to enable or disable the "Player Profile" tab
- **Values**:
  - `0` = Disabled
  - `1` = Enabled

### **`EnablePartyTab`**

- **Type**: Boolean
- **Description**: This setting allows you to enable or disable the "Party Manager" tab
- **Values**:
  - `0` = Disabled
  - `1` = Enabled

**Caution**: Disabling it will prevent players to create parties (groups)!

### **`EnableTerritoryTab`**

- **Type**: Boolean
- **Description**: This setting allows you to enable or disable the "Territory Manager" tab
- **Values**:
  - `0` = Disabled
  - `1` = Enabled

**Caution**: Disabling it will prevent players to invite/kick/manage players into their territory!

### **`EnableBookMenu`**

- **Type**: Boolean
- **Description**: This setting allows you to enable or disable the book
- **Values**:
  - `0` = Disabled
  - `1` = Enabled

### **`CreateBookmarks`**

- **Type**: Boolean
- **Description**: Currently doesn't work, in the old version of the book tabs were shown on the top of the book like bookmarks. This feature has yet to be re-introduced

---

## Setting up the Server Book Tab [Buttons]

### Where do you need to go?

Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Settings` and open the [BookSettings.json](BookSettings.json)

### How does it work?

**Example Configuration:**

```json
{
    "Name": "Feedback",
    "URL": "https://exp.thurston.pw/",
    "IconName": "Forums",
    "IconColor": -14473430
},
{
    "Name": "My Name To Display",
    "URL": "My Link here",
    "IconName": "MyIconHere",
    "IconColor": -14473430
}
```

**Note**: REMOVE the `,` from `},` on the last server button config entry.

---

## Links Configuration

### **`Links`**

- **Type**: Array
- **Description**: Contain a list of social links

### **`Links`** -> **`Name`**

- **Type**: String
- **Description**: The name to display

### **`Links`** -> **`URL`**

- **Type**: String
- **Description**: The URL used for this link

### **`Links`** -> **`IconName`**

- **Type**: String
- **Description**: The icon to display. A list will be provided later

### **`Links`** -> **`IconColor`**

- **Type**: Integer
- **Description**: The color of the icon

**Color Generation**: Use this website to generate the color you want to apply on your Icon!

Enter the RGBA values and then click on the button "ARGB → int" to generate the color code you will need.

- **R**: Red
- **G**: Green
- **B**: Blue
- **A**: Opacity from 0 (can't be seen) to 255 (very visible, opaque)

You can use this website to generate the RGBA color, however watch out this website generates the A value from 0 to 1 instead of 255!

---

## Example Configuration

```json
"Links": [
    {
        "Name": "Homepage",
        "URL": "https://www.google.com/",
        "IconName": "Homepage",
        "IconColor": -14473430
    },
    {
        "Name": "Feedback",
        "URL": "https://exp.thurston.pw/",
        "IconName": "Forums",
        "IconColor": -14473430
    },
    {
        "Name": "Discord",
        "URL": "https://www.google.com/",
        "IconName": "Discord",
        "IconColor": -9270822
    },
    {
        "Name": "Patreon",
        "URL": "https://www.patreon.com/dayzexpansion",
        "IconName": "Patreon",
        "IconColor": -432044
    },
    {
        "Name": "Steam",
        "URL": "https://steamcommunity.com/sharedfiles/filedetails/?id=2116151222",
        "IconName": "Steam",
        "IconColor": -14006434
    },
    {
        "Name": "Reddit",
        "URL": "https://www.reddit.com/r/ExpansionProject/",
        "IconName": "Reddit",
        "IconColor": -12386303
    },
    {
        "Name": "GitHub",
        "URL": "https://github.com/salutesh/DayZ-Expansion-Scripts/wiki",
        "IconName": "GitHub",
        "IconColor": -16777216
    },
    {
        "Name": "YouTube",
        "URL": "https://www.youtube.com/channel/UCZNgSvIEWfru963tQZOAVJg",
        "IconName": "YouTube",
        "IconColor": -65536
    },
    {
        "Name": "Twitter",
        "URL": "https://twitter.com/DayZExpansion",
        "IconName": "Twitter",
        "IconColor": -14835214
    }
]
```

---

## Setting up the Server Book Tab [Description]

### Where do you need to go?

Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Settings` and open the [BookSettings.json](BookSettings.json)

### How does it work?

**Example Configuration:**

```json
"Descriptions": [
    {
        "CategoryName": "My First Category",
        "Descriptions": [
            {
                "DescriptionText": "My first paragraph !"
            },
            {
                "DescriptionText": "And my second paragraph :)"
            }
        ]
    },
    {
        "CategoryName": "My Second Category",
        "Descriptions": [
            {
                "DescriptionText": "And this paragraph is in a new category"
            }
        ]
    }
]
```

**Note**: REMOVE the `,` from `},` at the last DescriptionText and Descriptions entry.

### **`Descriptions`**

- **Type**: Array
- **Description**: A list of description categories

### **`Descriptions`** -> **`CategoryName`**

- **Type**: String
- **Description**: The title of this category

### **`Descriptions`** -> **`Descriptions`**

- **Type**: Array
- **Description**: A list of description for this category

### **`Descriptions`** -> **`Descriptions`** -> **`DescriptionText`**

- **Type**: String
- **Description**: This is where you will write your paragraph

---

## Setting up the Server Settings Tab

### Where do you need to go?

Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Settings` and open the [BookSettings.json](BookSettings.json)

### How does it work?

**Example Configuration:**

```json
"SettingCategories": [
    {
        "CategoryName": "Base-Building Settings",
        "Settings": [
            {
                "SettingTitle": "Expansion.Settings.BaseBuilding.CanCraftVanillaBasebuilding",
                "SettingText": "Fence and Watchtower",
                "SettingValue": "Disabled"
            },
            {
                "SettingTitle": "Expansion.Settings.BaseBuilding.CanCraftExpansionBasebuilding",
                "SettingText": "My Custom Text to display",
                "SettingValue": "My Custom Value to display"
            }
        ]
    },
    {
        "CategoryName": "Party Settings",
        "Settings": [
            {
                "SettingTitle": "Expansion.Settings.Party.MaxMembersInParty",
                "SettingText": "",
                "SettingValue": ""
            },
            {
                "SettingTitle": "Expansion.Settings.Party.UseWholeMapForInviteList",
                "SettingText": "",
                "SettingValue": ""
            }
        ]
    }
]
```

**Note**: REMOVE the `,` from `},`

### **`CategoryName`**

- **Type**: String
- **Description**: The name title of a list of settings

### **`Settings`**

- **Type**: Array
- **Description**: A list of settings

### **`Settings`** -> **`SettingTitle`**

- **Type**: String
- **Description**: The path of this setting
- **Format**: `Expansion.Settings.Category.SettingName`

**Example**: `Expansion.Settings.BaseBuilding.CanCraftVanillaBasebuilding`

### **`Settings`** -> **`SettingText`**

- **Type**: String
- **Description**: You can write a custom description or leave it empty

### **`Settings`** -> **`SettingValue`**

- **Type**: String
- **Description**: You can also use this setting to display a custom secondary information about this setting. If it's enabled or disabled for example

---

## Setting up the Rule Book Tab

### Where do you need to go?

Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Settings` and open the [BookSettings.json](BookSettings.json)

### How does it work?

**Example Configuration:**

```json
"RuleCategories": [
    {
        "CategoryName": "General",
        "Rules": [
            {
                "RuleParagraph": "1.1.",
                "RuleText": "Insults, discrimination, extremist and racist statements or texts are taboo."
            },
            {
                "RuleParagraph": "1.2.",
                "RuleText": "We reserve the right to exclude people from the server who share extremist or racist ideas or who clearly disturb the server harmony."
            }
        ]
    },
    {
        "CategoryName": "Memes",
        "Rules": [
            {
                "RuleParagraph": "One",
                "RuleText": "No step on snek"
            },
            {
                "RuleParagraph": "Two",
                "RuleText": "We are waiting for you, in the test chamberrr"
            }
        ]
    }
]
```

**Note**: REMOVE the `,` from `},`

### **`RuleCategories`**

- **Type**: Array
- **Description**: A list of rule categories

### **`RuleCategories`** -> **`CategoryName`**

- **Type**: String
- **Description**: The name title of this rule category

### **`RuleCategories`** -> **`Rules`**

- **Type**: Array
- **Description**: A list of rules for this category

### **`Rules`** -> **`RuleParagraph`**

- **Type**: String
- **Description**: The rule number or identifier

### **`Rules`** -> **`RuleText`**

- **Type**: String
- **Description**: The rule text content

---

## Adding Crafting Recipes Tab

### Where do you need to go?

Go to `DayZServer\ServerProfile` (or config)`\ExpansionMod\Settings` and open the [BookSettings.json](BookSettings.json)

### How does it work?

**Example Configuration:**

```json
"CraftingCategories": [
    {
        "CategoryName": "BaseBuilding Kits",
        "Results": [
            "fencekit",
            "watchtowerkit",
            "territorykit"
        ]
    }
]
```

**Note**: REMOVE the `,` if it's the last entry of your results or your last category.

### **`CraftingCategories`**

- **Type**: Array
- **Description**: A list of crafting categories

### **`CraftingCategories`** -> **`CategoryName`**

- **Type**: String
- **Description**: The name to display of this category

### **`CraftingCategories`** -> **`Results`**

- **Type**: Array
- **Description**: Contain a list of crafted items. The system will automatically find what items need to be combined to craft this item

**Note**: Yes, this can be used with any items from any mods as long as they are from a crafting 'recipe' (item A + Item B = result).
