# How to configure the Expansion NoBuildZone

---

## Where to find the BaseBuildingSettings

Go to `mpmissions\dayzOffline.<mapname>\expansion\settings` in your server directory and open the file [basebuildingsettings.json](basebuildingsettings.json)

---

## Adding a BaseBuilding Zone

**Example Configuration:**

```json
{
    "Name": "My Location Name",
    "Center": [
        11882.0,
        143.0,
        12466.0
    ],
    "Radius": 1000.0,
    "Items": [
        "MyClassName",
        "MyOtherClassName",
        "MyLastClassName_WithoutACommaAtTheEnd"
    ],
    "IsWhitelist": 1,
    "CustomMessage": "If you want a custom message to display to the player"
}
```

---

## How does it work?

**Configuration Structure:**

```json
{
    "Name": "My Location Name",
    "Center": [
        X,  // West/East
        Y,  // Elevation/Altitude
        Z   // South/North
    ],
    "Radius": 1000.0,
    "Items": [
        "MyClassName",
        "MyOtherClassName",
        "MyLastClassName_WithoutACommaAtTheEnd"  // Without a comma if it's the last item
    ],
    "IsWhitelist": 1,
    "CustomMessage": "If you want a custom message to display to the player"
}  // Without a comma if it's the last zone
```

---

## Parameters

### **`Name`**

- **Type**: String
- **Description**: The name of your zone. It will be displayed as a notification title if the player tries to build with an item not allowed to be used in this area

### **`Center`**

- **Type**: Vector
- **Description**: The position of your zone
- **Format**: `[X, Y, Z]`
  - **X**: West/East coordinate
  - **Y**: Elevation/Altitude
  - **Z**: South/North coordinate

### **`Radius`**

- **Type**: Float
- **Description**: The size of your zone

### **`Items`**

- **Type**: Array [String]
- **Description**: A list of classnames (items)

### **`IsWhitelist`**

- **Type**: Integer
- **Description**: Controls whether the Items list is a whitelist or blacklist
- **Values**:
  - `1` = Only the Items will be allowed to be used in this zone (Whitelist)
  - `0` = All the Items will be disallowed in this area (Blacklist)

### **`CustomMessage`**

- **Type**: String
- **Description**: Similar to "Name", this message will be displayed below the title

---

## Recommendations

The easiest method we recommend you to do is to go at the location you want to add your safezone and open your admin tool to get these coordinates.

**Important**: Remember to remove the `,` in `},` at the last bracket.

---

## Other Settings

As you have noticed, this file also contains various settings. If you are curious about any of them, we recommend you to read the server settings documentation of this file:

https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-SafeZoneSettings