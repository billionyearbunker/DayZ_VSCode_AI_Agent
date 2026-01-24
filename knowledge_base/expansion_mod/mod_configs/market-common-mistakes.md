# Market Common Mistakes

---

## "Item listed doesn't have a preview and translated name"

![unknown item preview](unknown-item-preview.png)

**Issue**: This items doesn't exist.

**Solution**: Make sure you are loading the mod adding these items and make sure you provided the correct classname!

---

## "Not Enough Spawn Positions within x meters of this trader!"

![Not Enough Spawn Positions within x meters of this trader](spawn-position-error.png)

**Issue**: The vehicle you are trying to buy was unable to be spawned as the Trader couldn't find a valid spawn position nearby.

**Possible Causes**:

### 1. No Configured Spawn Position Nearby

Go inside your `mpmission/dayzoffline.mapname/expansion/settings/marketsettings.json` and add a new Spawn Position.

**Example**:
```json
"LandSpawnPositions": [
    {
        "Position": [
            11903.400390625,
            140.0,
            12455.099609375
        ],
        "Orientation": [
            24.0,
            0.0,
            0.0
        ]
    },
    {
        "Position": [
            11898.400390625,
            140.0,
            12481.599609375
        ],
        "Orientation": [
            24.0,
            0.0,
            0.0
        ]
    }
]
```

**Configuration Structure**:
```json
{
    "Position": [
        X,
        Y,      // Altitude
        Z
    ],
    "Orientation": [
        24.0,   // Orientation
        0.0,
        0.0
    ]
}   // Remove the comma if it's the last spawn position of your list!
```

### 2. Invalid Spawn Position

The other possibility is an invalid spawn position which is not safe to spawn a vehicle. It could be because of objects too close to the configured spawn position for example.

---

## "Stuck at Loading Trader..."

![Trader not loading](trader-not-loading.png)

**Possible Causes**:

1. **Your trader .json is broken** - validate your file!
2. **Your trader is not inside a traderzone**
