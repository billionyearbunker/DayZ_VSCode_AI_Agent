# How to Configure the Expansion Map Markers

---

## File Location

Go to `mpmissions\dayzOffline.<mapname>\expansion\settings` and open the **MapSettings.json**

---

## Configuration Structure
{
    "m_UID": "MyUniqueID101",
    "m_Visibility": 6,
    "m_Is3D": 1,
    "m_Text": "My Marker Name !",
    "m_IconName": "IconName",
    "m_Color": -13710223,
    "m_Position": [
        11882.0,
        143.0,
        12466.0
    ],
    "m_Locked": 0,
    "m_Persist": 1
},
**Note**: REMOVE the `,` from `},` for the last marker config (look at the example at the end of the page)

---

## Parameter Descriptions

### **`m_UID`**
- **Type**: String
- **Description**: The UID is the unique identity of a marker, this means it needs to be unique to be valid. This ID can have numbers or letters

---

### **`m_Visibility`**
- **Type**: Integer
- **Description**: We recommend you to keep it to 6 since its behavior is affected by the other settings and might not do what you really expect from this setting
- **Values**:
  - `0` = Not visible
  - `2` = Visible on the World (If `m_Is3D` is set to 1, you should probably put `m_Visibility` to 2)
  - `4` = Visible on the Map only
  - `6` = Visible on the Map and on the World (If `m_Is3D` is set to 1, you should probably put `m_Visibility` to 2)

---

### **`m_Is3D`**
- **Type**: Integer
- **Values**:
  - `0` = Only visible on the 2d map
  - `1` = Visible in 3D while playing and on the 2d map

---

### **`m_Text`**
- **Type**: String
- **Description**: This text will be displayed next to the marker name. You can also keep it empty if you want

---

### **`m_IconName`**
- **Type**: String
- **Description**: What Icon will be used for the marker. See [List of default icon names](list-of-default-icon-names.md)

---

### **`m_Color`**
- **Type**: Integer
- **Description**: The color of the marker, use this website to generate the color you want to apply on your marker!

**Color Generation**:
- Enter the RGBA values and then click on the button "ARGB → int" to generate the color code you will need
- **R**: Red
- **G**: Green
- **B**: Blue
- **A**: Opacity from 0 (can't be seen) to 255 (very visible, opaque)

**Note**: You can use this website to generate the RGBA color, however watch out this website generate the A value from 0 to 1 instead of 255!

---

### **`m_Position`**
- **Type**: Array[Float]
- **Description**: The position of the marker in X Y Z coordinates
- **Note**: Any admin tools and editors should be able to give you these values. You could go where you want your marker to be and check your player position for example

---

### **`m_Locked`**
- **Type**: Integer
- **Description**: Not used for server markers as they are not draggable

---

### **`m_Persist`**
- **Type**: Integer
- **Description**: Also not used for server markers. This setting is meant for modders to create non permanent personal (local) markers

---

## Example Configuration

```json
    "ServerMarkers": [
        {
            "m_UID": "ServerMarker_Trader_Krasno",
            "m_Visibility": 6,
            "m_Is3D": 1,
            "m_Text": "Traders - Krasnostav Airstrip",
            "m_IconName": "Trader",
            "m_Color": -13710223,
            "m_Position": [
                11882.0,
                143.0,
                12466.0
            ],
            "m_Locked": 0,
            "m_Persist": 1
        },
        {
            "m_UID": "ServerMarker_Trader_Kamenka",
            "m_Visibility": 6,
            "m_Is3D": 1,
            "m_Text": "Traders - Kamenka",
            "m_IconName": "Trader",
            "m_Color": -13710223,
            "m_Position": [
                1101.0,
                8.0,
                2382.0
            ],
            "m_Locked": 0,
            "m_Persist": 1
        },
        {
            "m_UID": "ServerMarker_Boats_Kamenka",
            "m_Visibility": 6,
            "m_Is3D": 1,
            "m_Text": "Boats - Kamenka",
            "m_IconName": "Boat",
            "m_Color": -13710223,
            "m_Position": [
                1756.0,
                4.0,
                2027.0
            ],
            "m_Locked": 0,
            "m_Persist": 1
        },
        {
            "m_UID": "ServerMarker_Aircrafts_Balota",
            "m_Visibility": 6,
            "m_Is3D": 1,
            "m_Text": "Aircrafts - Balota",
            "m_IconName": "Helicopter",
            "m_Color": -13710223,
            "m_Position": [
                4973.0,
                12.0,
                2436.0
            ],
            "m_Locked": 0,
            "m_Persist": 1
        },
        {
            "m_UID": "ServerMarker_Boats_Svetloyarsk",
            "m_Visibility": 6,
            "m_Is3D": 1,
            "m_Text": "Boats & Fishing - Svetloyarsk",
            "m_IconName": "Boat",
            "m_Color": -13710223,
            "m_Position": [
                14379.0,
                6.0,
                13256.0
            ],
            "m_Locked": 0,
            "m_Persist": 1
        },
        {
            "m_UID": "ServerMarker_Trader_Green_Montain",
            "m_Visibility": 6,
            "m_Is3D": 1,
            "m_Text": "Trader - Green Montain",
            "m_IconName": "Trader",
            "m_Color": -13710223,
            "m_Position": [
                3698.0,
                405.0,
                5988.0
            ],
            "m_Locked": 0,
            "m_Persist": 1
        }
    ]
}
