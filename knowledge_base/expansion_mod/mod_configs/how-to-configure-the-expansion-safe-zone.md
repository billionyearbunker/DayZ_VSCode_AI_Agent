# How to Configure the Expansion Safezone

---

## File Location

Go to `mpmissions\dayzOffline.<mapname>\expansion\settings` in your server directory and open the file **safezonesettings.json**

---

## Adding a Circle Safezone

## Adding a Circle Safezone

Add the following lines:

```json
{
    "Center": [
        3728.27001953125,
        403.0,
        6003.60009765625
    ],
    "Radius": 500
}
```

**Parameters**:
- **Center**: An array where you will need to specify the X Y Z coordinates of your safezone
- **Radius**: The size of your safezone (meters)

**Tip**: The easiest method we recommend is to go to the location where you want to add your safezone and open your admin tool to get these coordinates.

**Note**: Think to remove the `,` in `},` at the last bracket.

---

## Adding a Cylinder Safezone

Add the following lines:

```json
{
    "Center": [
        3728.27001953125,
        403.0,
        6003.60009765625
    ],
    "Radius": 500,
    "Height": 120.0
}
```

**Parameters**:
- **Center**: An array where you will need to specify the X Y Z coordinates of your safezone
- **Radius**: The size of your safezone (meters)
- **Height**: The Height of your safezone (meters)

**Tip**: The easiest method we recommend is to go to the location where you want to add your safezone and open your admin tool to get these coordinates.

**Note**: Think to remove the `,` in `},` at the last bracket.

---

## Adding a Polygon Safezone

Add the following lines (you have a picture to show how it should be done):

```json
{
    "Positions": [
        [
            6345,
            140.0,
            2181
        ],
        [
            6198,
            140.0,
            2433
        ],
        [
            6565,
            140.0,
            2945
        ],
        [
            7000,
            140.0,
            2521
        ]
    ]
}
```

**Parameters**:
- **Positions**: An array where you will need to specify the X Y Z coordinates of your safezone. Since this is a polygon, you need to add multiple positions like in this example to create a polygon shape safezone

**Tips**:
- The easiest method we recommend is to go to the location where you want to add your safezone and open your admin tool to get these coordinates
- You can also use the DayZ Editor mod if it's easier for you

**Note**: Think to remove the `,` in `},` at the last bracket.

---

## Other Settings

As you have noticed, this file also contains various settings. If you are curious about any of them, we recommend you to read the server settings documentation of this file: https://github.com/salutesh/DayZ-Expansion-Scripts/wiki/%5BServer-Hosting%5D-SafeZoneSettings
