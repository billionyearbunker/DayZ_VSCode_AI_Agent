# AI Settings

## Configuration Parameters

### **`m_Version`**
- **Type:** `Integer`
- **Description:** Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

### **`AccuracyMin`**
- **Type:** `Float`
- **Range:** `0.0-1.0`
- **Description:** Minimum accuracy of the AI.
- **Note:** This setting can be overridden in each patrols themselves.

### **`AccuracyMax`**
- **Type:** `Float`
- **Range:** `0.0-1.0`
- **Description:** Maximum accuracy of the AI.
- **Note:** This setting can be overridden in each patrols themselves.

### **`ThreatDistanceLimit`**
- **Type:** `Float`
- **Description:** Maximum distance the AI is allowed to calculate a potential target as a threat.
- **Note:** This setting can be overridden in each patrols themselves.

### **`NoiseInvestigationDistanceLimit`**
- **Type:** `Float`
- **Description:** How far away a noise can be for AI to consider checking it out.
- **Note:** This setting can be overridden in each patrols themselves.

### **`DamageMultiplier`**
- **Type:** `Float`
- **Description:** How much damage AI is doing. `1.0 = 100%`
- **Note:** This setting can be overridden in each patrols themselves.

### **`DamageReceivedMultiplier`**
- **Type:** `Float`
- **Description:** How much damage AI is receiving when attacked. `1.0 = 100%`
- **Note:** This setting can be overridden in each patrols themselves.

### **`Admins`**
- **Type:** `TStringArray`
- **Description:** A list of steam ids in quotes to allow access to a debug menu for AI.
- **More Info:** For more information Click here

### **`Vaulting`**
- **Type:** `Boolean`
- **Values:**
  - `0` = AI won't vault
  - `1` = AI can vault over objects

### **`SniperProneDistanceThreshold`**
- **Type:** `Float`
- **Description:** How close a target can be for AI to go prone when using a bolt action rifle. If the target is closer than this value, AI won't go prone.

### **`Manners`**
- **Type:** `Boolean`
- **Values:**
  - `0` = AI won't taunt or emote
  - `1` = AI will taunt after killing a target, or emote, randomly

### **`MemeLevel`**
- **Type:** `Integer`
- **Description:** Make the AI behave in goofy ways.
- **Values:**
  - `0` = Turned off
  - `???` = Do something

### **`CanRecruitFriendly`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Friendly AI cannot be recruited
  - `1` = Players can recruit Friendly AIs (Based on Faction relations)

### **`CanRecruitGuards`**
- **Type:** `Boolean`
- **Values:**
  - `0` = Guards cannot be recruited
  - `1` = Players can recruit Guards

### **`PreventClimb`**
- **Type:** `TStringArray`
- **Description:** A list of objects classnames the AI shouldn't be able to climb.
- **Example:** `"Land_Mil_Airfield_HQ"` (this one is hardcoded)

### **`PlayerFactions`**
- **Type:** `TStringArray`
- **Description:** A list of Factions in quotes. One of these listed factions will be randomly assigned to new players.
- **More Info:** For more information Click here

### **`LogAIHitBy`**
- **Type:** `Bool`
- **Description:** Log AI getting hit to admin log.

### **`LogAIKilled`**
- **Type:** `Bool`
- **Description:** Log AI getting killed to admin log.

### **`EnableZombieVehicleAttackHandler`**
- **Type:** `Bool`
- **Description:** Zombies will attack vehicles if a player sits in them.

### **`EnableZombieVehicleAttackPhysics`**
- **Type:** `Bool`
- **Description:** Zombies will shake up the vehicle while attacking it.

### **`LightingConfigMinNightVisibilityMeters`**
- **Description:** Sets how far AI can see at night without flashlight/NVG depending on `lightingConfig` value in `CfgGameplay.json`.

**Default for Chernarus:**

```json
"LightingConfigMinNightVisibilityMeters": {
    "0": 100.0,
    "1": 10.0
}
```
    