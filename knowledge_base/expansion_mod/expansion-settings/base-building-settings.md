# BaseBuildingSettings

**Note**: Unlike most other settings that may not be map-specific, you can find the BaseBuildingSettings.json in your `mpmission\dayzOffline.<mapname>\expansion\settings` folder.

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

## Building Permissions

### **`CanBuildAnywhere`**
- **Type**: Bool
- **Values**:
  - `0` = Deploying an object and building vanilla fence/watchtower will follow the vanilla limitations
  - `1` = You can deploy anywhere and build anywhere without any restrictions from the vanilla limitations

---

### **`AllowBuildingWithoutATerritory`**
- **Type**: Bool
- **Values**:
  - `0` = You are forced to build/deploy inside a territory. However You can add some objects to a whitelist if you still want some deployables usable outside the territory like a campfire or a beartrap
  - `1` = You are not restricted to only build/deploy inside a territory

---

### **`DeployableOutsideATerritory`**
- **Type**: Array of string
- **Description**: Only used if AllowBuildingWithoutATerritory is set to 0. This list of classnames are the items you will be able to deploy outside the territories

**Example**:
```json
"DeployableOutsideATerritory": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withaCommaAtTheEnd",
    "classname03_withoutCommaAtTheEndBecauseItsTheLastOne"
]
```

---

### **`DeployableInsideAEnemyTerritory`**
- **Type**: Array of string
- **Description**: This list is used for raiding purposes. All the classnames listed here will be deployable inside the territory of your ennemies. It's recommended to only allow raiding devices or traps

**Example**:
```json
"DeployableInsideAEnemyTerritory": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withaCommaAtTheEnd",
    "classname03_withoutCommaAtTheEndBecauseItsTheLastOne"
]
```

---

## Crafting Settings

### **`CanCraftVanillaBasebuilding`**
- **Type**: Bool
- **Values**:
  - `0` = The player will not be able to craft the fence and watchtower kit
  - `1` = The player can craft the fence and watchtower kit

---

### **`CanCraftExpansionBasebuilding`**
- **Type**: Bool
- **Values**:
  - `0` = The player will not be able to craft all the expansion kits (wall, floor, ramp, stairs)
  - `1` = The player can craft all the expansion kits (wall, floor, ramp, stairs)

---

## Territory Flag Settings

### **`DestroyFlagOnDismantle`**
- **Type**: Bool
- **Values**:
  - `0` = After dismantling the flag pole, you will get back your kit
  - `1` = You won't get your flag kit back after dismantling

---

### **`DismantleOutsideTerritory`**
- **Type**: Bool
- **Values**:
  - `0` = You cannot dismantle anything outside your own territory
  - `1` = You can dismantle everything unless if it's inside the territory of someone else

---

### **`DismantleInsideTerritory`**
- **Type**: Bool
- **Values**:
  - `0` = You cannot dismantle anything inside the territories you don't own
  - `1` = You can dismantle inside the territory of everyone

---

### **`DismantleAnywhere`**
- **Type**: Bool
- **Values**:
  - `0` = You need to be on the soft side of the object to have the dismantle action
  - `1` = The dismantle action will be available from anywhere. If you are in the territory of someone else, you won't be able to dismantle

---

## Code Lock Settings

### **`CodelockActionsAnywhere`**
- **Type**: Bool
- **Values**:
  - `0` = You need to look at the codelock to have the interactions with the codelock (like in vanilla)
  - `1` = You need to look at the wall, door, gate or the codelock to get the interactions with the codelock (like codelock mod)

---

### **`CodeLockLength`**
- **Type**: Integer
- **Description**: The length of passwords you can put into your code locks. If you want to only allow 6 digits password in the codelocks set it to 6 for example

---

### **`DoDamageWhenEnterWrongCodeLock`**
- **Type**: Bool
- **Values**:
  - `0` = If the user give the wrong password he won't get hurt
  - `1` = If the password is wrong, he will get hurt by the amount defined in `DamageWhenEnterWrongCodeLock`

---

### **`DamageWhenEnterWrongCodeLock`**
- **Type**: Float
- **Description**: The number of damage the player will take when he types a wrong code lock. 0 won't do anything damage and 100 will kill the player

---

## Territory Creation

### **`CanCraftTerritoryFlagKit`**
- **Type**: Bool
- **Values**:
  - `0` = The player can't craft the territory flag
  - `1` = The player can craft the territory flag (3 sticks + 1 rope)

---

### **`SimpleTerritory`**
- **Type**: Bool
- **Values**:
  - `0` = The player will have to build the flag pole like in vanilla
  - `1` = The flag pole will be built automaticly after being deployed

---

### **`AutomaticFlagOnCreation`**
- **Type**: Bool
- **Values**:
  - `0` = The player will need to add by himself the flag
  - `1` = The flag will be automaticly added to the flag pole

---

### **`GetTerritoryFlagKitAfterBuild`**
- **Type**: Bool
- **Values**:
  - `0` = The player will not get his kit after building his territory flag
  - `1` = The player will get his kit back after building the first stage of the territory flag

---

### **`BuildZoneRequiredCustomMessage`**
- **Type**: String
- **Description**: The message that gets displayed to players when the try to build in a non build zone

---

## No-Build Zones

### **`Zones`**
- **Type**: Array of non building zones

**Example**:
```json
"Zones": [
    {
        "Name": "Airstrip Trader",
        "Center": [
            6305.0,
            26.0,
            9521.0
        ],
        "Radius": 4000.0,
        "Items": [],
        "IsWhitelist": 1,
        "CustomMessage": ""
    },
    {
        "Name": "Jalovisko Trader Camp",
        "Center": [
            8583.669921875,
            29.0,
            10515.0
        ],
        "Radius": 2000.0,
        "Items": [],
        "IsWhitelist": 1,
        "CustomMessage": ""
    },
    {
        "Name": "Tara Harbor Boat Trader",
        "Center": [
            8043.4501953125,
            10.0,
            7593.4501953125
        ],
        "Radius": 2000.0,
        "Items": [],
        "IsWhitelist": 1,
        "CustomMessage": ""
    }
]
```

---

### **`ZonesAreNoBuildZones`**
- **Type**: Bool
- **Values**:
  - `0` = If disabled the zones are building zones, witch means players can only build in the configured zones
  - `1` = If enabled the configured non building zones are marking the areas where players cant build

---

## Additional Settings

### **`CodelockAttachMode`**
- **Type**: Integer
- **Values**:
  - `0` = Expansion BaseBuilding only
  - `1` = Expansion BaseBuilding + Fence
  - `2` = Expansion BaseBuilding + Fence + Tents
  - `3` = Expansion BaseBuilding + Tents

---

### **`DismantleFlagMode`**
- **Type**: Integer
- **Values**:
  - `-1` = Only members of the territory can dismantle with their bare hands
  - `0` = Anyone can dismantle with their bare hands
  - `1` = Anyone can dismantle but only with specific tools

---

### **`FlagMenuMode`**
- **Type**: Integer
- **Values**:
  - `0` = The player will not be able to create a territory
  - `1` = The player will be able to create a territory to protect his base
  - `2` = The player will be able to create a territory to protect his base but he won't be able to customize his flag from the flag menu

---

## Virtual Storage

### **`EnableVirtualStorage`**
- **Type**: Bool
- **Description**: Instead of keeping items as attachments or in cargo of containers, they are saved to virtual storage and completely removed from the game world when the container is closed (will be restored when the container is opened). May be good for server performance, but loot that is marked count_in_cargo="1" will be able to respawn. Supports most containers (e.g. barrels, wooden crate, sea chest, Expansion safe) and vanilla tents (only when locking/unlocking). Containers that are not openable/closable or modded items that act as containers will show a "store/restore contents" action

---

### **`VirtualStorageExcludedContainers`**
- **Type**: String array
- **Description**: List classnames that you want to exclude from virtual storage (if enabled, see above) here

**Example**:
```json
"VirtualStorageExcludedContainers": [
    "classname01_withaCommaAtTheEnd",
    "classname02_withaCommaAtTheEnd",
    "classname03_withoutCommaAtTheEndBecauseItsTheLastOne"
]
```
    