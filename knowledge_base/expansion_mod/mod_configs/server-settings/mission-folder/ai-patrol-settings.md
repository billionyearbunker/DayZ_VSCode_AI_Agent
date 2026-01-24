# AIPatrolSettings

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`Enabled`**
- **Type**: Boolean
- **Values**:
  - `0` = OFF | Disabled
  - `1` = ON | Enabled

---

### **`FormationScale`**
- **Type**: Float
- **Description**: How far apart the individual formation positions are
- **Details**:
  - For formations that are on a grid (like Vee, InvVee, Wall, Column and InvColumn), the value determines the side length of the grid in meters
  - For formations that are not on a grid (like Star, StarDot, Circle and CircleDot), the value roughly determines the distance between the positions (in case of star-based formations, the inner positions, with distances between outer positions scaled accordingly)
- **Default**: -1.0 (uses AISettings.json value, which defaults to 1.0)

---

### **`DespawnTime`**
- **Type**: Float
- **Description**: How long in seconds will it take for the patrol to despawn if no players are in DespawnRadius
- **Values**: `-1` = Use the value from AISettings.json

---

### **`RespawnTime`**
- **Type**: Float
- **Description**: How long in seconds until this patrol can respawn if no players are in MinDistRadius?
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`MinDistRadius`**
- **Type**: Float
- **Description**: The required minimum distance from a player to spawn. If a player is closer than MinDistRadius meters, then the patrol won't spawn
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`MaxDistRadius`**
- **Type**: Float
- **Description**: The required maxium distance from a player to spawn. If a player is further away than MaxDistRadius meters, then the patrol won't spawn
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`DespawnRadius`**
- **Type**: Float
- **Description**: The required distance from a player to despawn. If a player is closer than DespawnRadius meters, then the patrol won't despawn

---

### **`AccuracyMin`**
- **Type**: Float
- **Description**: Minimum accuracy of the AI (0.0-1.0)
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`AccuracyMax`**
- **Type**: Float
- **Description**: Maximum accuracy of the AI (0.0-1.0)
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`ThreatDistanceLimit`**
- **Type**: Float
- **Description**: Distance in meters when the target will start be considered a potential threat. AI will not see enemies past this distance, so use with care
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`NoiseInvestigationDistanceLimit`**
- **Type**: Float
- **Description**: Max distance in meters that AI will search for noise sources
- **Values**: -1 = use value from AISettings.json

---

### **`MaxFlankingDistance`**
- **Type**: Float
- **Description**: Max distance to enemy in meters that AI will try to flank the enemy (default 200)
- **Values**: -1 = use value from AISettings.json

---

### **`EnableFlankingOutsideCombat`**
- **Type**: Int
- **Description**: Enable flanking outside combat. Note that this will give AI a sort of "sixth sense" about enemies, but not necessarily their exact position when there is no line of sight
- **Values**:
  - `0` = disabled
  - `1` = enabled
  - `-1` = use value from AISettings.json

---

### **`DamageMultiplier`**
- **Type**: Float
- **Description**: Damage multiplier from the AI (default 1.0 = no change). Base damage they will deal multiplied by this value
- **Values**: If set to -1 will use the value from AISettings.json

---

### **`DamageReceivedMultiplier`**
- **Type**: Float
- **Description**: Damage multiplier for damage the AI receive (default 1.0 = no change). Base damage they receive will be multiplied by this value
- **Values**: If set to -1 will use the value from AISettings.json

---

## Additional Resources

- **LoadBalancingCategories**: AI Load Balancing
- **Patrols**: How to create AI Patrols
