# Book Settings

## Configuration Parameters

### **`m_Version`**
- **Type:** `Integer`
- **Description:** Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`EnableStatusTab`**
- **Type:** `Bool`
- **Values:**
  - `0` = This page won't be displayed in the book
  - `1` = The status tab will be available. The status tab contains character info like health, hunger/thirst values, etc.

---

### **`EnablePartyTab`**
- **Type:** `Bool`
- **Values:**
  - `0` = This page won't be displayed in the book
  - `1` = The party tab will be available allowing players to manage and creating parties and invite players. You can tweak parties in the `PartySettings.json`

---

### **`EnableServerInfoTab`**
- **Type:** `Bool`
- **Values:**
  - `0` = This page won't be displayed in the book
  - `1` = A server info page will be available allowing you to provide a description of your server, buttons to redirect the player to your discord, forum or other places

---

### **`EnableServerRulesTab`**
- **Type:** `Bool`
- **Values:**
  - `0` = This page won't be displayed in the book
  - `1` = The server rules tab will be available. This page allows servers to display their rules

---

### **`EnableTerritoryTab`**
- **Type:** `Bool`
- **Values:**
  - `0` = This page won't be displayed in the book
  - `1` = The territory tab will be available allowing players to manage their territories and invite players. You can tweak territories in the `TerritorySettings.json`

---

### **`EnableBookMenu`**
- **Type:** `Bool`
- **Values:**
  - `0` = The Book will be disabled
  - `1` = Players can press B to open the Book

---

### **`CreateBookmarks`**
- **Type:** `Bool`
- **Values:**
  - `0` = Bookmarks won't be displayed for each book categories (pages)
  - `1` = Bookmarks will be displayed on the top of the book for quick navigation between the categories

---

### **`ShowHaBStats`**
- **Type:** `Bool`
- **Note:** If the mod Heroes and Bandits is loaded, this setting will be added
- **Values:**
  - `0` = Do not show any stats related to Heroes and Bandits
  - `1` = Display stats related to Heroes and Bandits

---

### **`RuleCategories`**
- **Type:** `Array`
- **Description:** Contains all the rules categories.

---

#### **`CategoryName`**
- **Type:** `String`
- **Description:** Title of the category.

---

#### **`Rules`**
- **Type:** `Array`
- **Description:** A list of rules.

---

#### **`RuleParagraph`**
- **Type:** `String`
- **Description:** Usually servers like to enumerate their rules. This setting allows you to do this and the way you want it.

---

#### **`RuleText`**
- **Type:** `String`
- **Description:** The text of your rule.

**Example:**

```json
"RuleCategories": 
[
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
				"RuleParagraph": "A)",
				"RuleText": "No step on snek"
			},
			{
				"RuleParagraph": "B)",
				"RuleText": "Kiwis are forbidden"
			}
		]
	}
]
```

---

### **`DisplayServerSettingsInServerInfoTab`**
- **Type:** `Bool`
- **Values:**
  - `0` = The server settings won't be displayed in the server info page
  - `1` = Will display the server settings in the server info tab on the right page

---

### **`SettingCategories`**
- **Type:** `Array`
- **Description:** Contain all the settings categories.

---

#### **`CategoryName`**
- **Type:** `String`
- **Description:** The title of this setting category name.

---

#### **`Settings`**
- **Type:** `Array`
- **Description:** Contain all the settings of this category.

---

#### **`SettingTitle`**
- **Type:** `String`
- **Description:** The path of the setting.

**Format:** `"Expansion.Settings.Category.SettingName"`

**Example:** `"Expansion.Settings.BaseBuilding.CanCraftVanillaBasebuilding"`

---

#### **`SettingText`**
- **Type:** `String`
- **Description:** You can write a custom description or leave it empty.

---

#### **`SettingValue`**
- **Type:** `String`
- **Description:** You can also use this setting to display a custom secondary information about this setting. If it's enabled or disabled for example.

**Example:**

```json
"SettingCategories": [
    {
        "CategoryName": "Base-Building Settings",
        "Settings": [
            {
                "SettingTitle": "Expansion.Settings.BaseBuilding.CanCraftVanillaBasebuilding",
                "SettingText": "",
                "SettingValue": ""
            },
            {
                "SettingTitle": "Expansion.Settings.BaseBuilding.CanCraftExpansionBasebuilding",
                "SettingText": "",
                "SettingValue": ""
            }
        ]
    },
    {
        "CategoryName": "Raid Settings",
        "Settings": [
            {
                "SettingTitle": "Expansion.Settings.Raid.CanRaidSafes",
                "SettingText": "",
                "SettingValue": ""
            }
        ]
    }
]
```

---

### **`Links`**
- **Type:** `Array`
- **Description:** Contain a list of social links.

---

#### **`Name`**
- **Type:** `String`
- **Description:** The name to display.

---

#### **`URL`**
- **Type:** `String`
- **Description:** The URL used for this link.

---

#### **`IconName`**
- **Type:** `String`
- **Description:** The icon to display. A list will be provided later.

---

#### **`IconColor`**
- **Type:** `Integer`
- **Description:** The color of the icon.

**Note:** Use this website to generate the color you want to apply on your Icon: https://www.shodor.org/~efarrow/trunk/html/rgbint.html

Enter the RGBA values and then click on the button "ARGB → int" to generate the color code you will need.

- **R:** Red
- **G:** Green
- **B:** Blue
- **A:** Opacity from 0 (can't be seen) to 255 (very visible, opaque)

**Note:** You can use this website to generate the RGBA color, however watch out this website generate the A value from 0 to 1 instead of 255!

**Example:**

```json
{
    "Name": "Feedback",
    "URL": "https://exp.thurston.pw/",
    "IconName": "Forums",
    "IconColor": -14473430
}
```

---

### **`Descriptions`**
- **Type:** `Array`
- **Description:** A list of description categories.

---

#### **`CategoryName`**
- **Type:** `String`
- **Description:** The title of this category.

---

#### **`Descriptions`**
- **Type:** `Array`
- **Description:** A list of descriptions for this category.

---

#### **`DescriptionText`**
- **Type:** `String`
- **Description:** A paragraph.

**Example:**

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

---

### **`CraftingCategories`**
- **Type:** `Array`
- **Description:** A list of crafting categories.

---

#### **`CategoryName`**
- **Type:** `String`
- **Description:** The title of this category.

---

#### **`Results`**
- **Type:** `Array`
- **Description:** A list of craftable items for this category.

**Example:**

```json
"CraftingCategories": [
    {
        "CategoryName": "The three must know crafts",
        "Results": [
            "fireplace",
            "splint",
            "improvisedsuppressor"
        ]
    },
    {
        "CategoryName": "Fishing",
        "Results": [
            "bait",
            "bonebait",
            "bonehook",
            "improvisedfishingrod"
        ]
    }
]
```
```
