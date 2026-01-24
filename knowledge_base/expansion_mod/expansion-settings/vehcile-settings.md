# VehicleSettings

---

## Settings Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something.

---

### **`VehicleSync`**
- **Type**: Integer
- **Note**: Not used, ignore

---

### **`VehicleRequireKeyToStart`**
- **Type**: Bool
- **Values**:
  - `0` = Even if your car is paired to a key, you don't need to have the key in the vehicle inventory or on yourself
  - `1` = You will need a car key paired to the vehicle in your inventory or in the inventory of the vehicle to start the engine
  - `2` = You need to have the key in your hands to start the engine

---

### **`VehicleRequireAllDoors`**
- **Type**: Bool
- **Values**:
  - `0` = Even if you are missing some doors, you can still lock the vehicle
  - `1` = You will need all the doors of the car to lock your vehicle

---

### **`VehicleLockedAllowInventoryAccess`**
- **Type**: Bool
- **Values**:
  - `0` = Players will need to unlock the vehicle to access the inventory
  - `1` = Allow players to access the inventory of the vehicle even if this vehicle is locked

---

### **`MasterKeyPairingMode`**
- **Type**: Integer
- **Values**:
  - `-1` = infinite master pairing uses
  - `0` = disabled. You can pair any keys to your already paired car
  - `1` = limited uses before becoming a normal car key (MasterKeyUses)
  - `2` = renewable with a electronicalrepairkit or a keygrinder (will also use MasterKeyUses)
  - `3` = renewable with a keygrinder (will also use MasterKeyUses)
- **Note**: Expansion provide his own "KeyGrinder" but we have added compability to the KeyGrinder from the mod MuchCarKeys in case if you want to

---

### **`MasterKeyUses`**
- **Type**: Integer
- **Description**: Amount of times the masterkey can pair unpaired keys

---

### **`CanPickLock`**
- **Type**: Bool
- **Values**:
  - `0` = You can't lock pick vehicles
  - `1` = Allow players to lock pick vehicles

---

### **`PickLockTools`**
- **Type**: Array
- **Description**: A list of classnames (items) allowed to lockpick cars

---

### **`PickLockChancePercent`**
- **Type**: Integer
- **Description**: The Percentage of chance to successfully lock pick a vehicle (from 0 to 100)

---

### **`PickLockTimeSeconds`**
- **Type**: Integer
- **Description**: How many seconds it will take to do the lock pick action

---

### **`PickLockToolDamagePercent`**
- **Type**: Integer
- **Description**: How much damage the tool will take when completing the action. In percentage (from 0 to 100)

---

### **`EnableWindAerodynamics`**
- **Type**: Bool
- **Values**:
  - `0` = The helicopters won't have wind simulation
  - `1` = Enable wind simulation for helicopters

---

### **`EnableTailRotorDamage`**
- **Type**: Bool
- **Values**:
  - `0` = rotors of helicopters can't be damaged
  - `1` = rotors of helicopters can be damaged and will spin if destroy making the helicopters almost unusable

---

### **`Towing`**
- **Type**: Bool
- **Values**:
  - `0` = Towing is disabled
  - `1` = Allow cars to tow other cars. Helicopters can tow any types vehicles

---

### **`EnableHelicopterExplosions`**
- **Type**: Bool
- **Values**:
  - `0` = Helicopters won't explode
  - `1` = Helicopters can explode

---

### **`DisableVehicleDamage`**
- **Type**: Bool
- **Values**:
  - `0` = The Vehicles can take damage from anything (collision damage multipliers apply)
  - `1` = The vehicles can't take damage (collision and bullet proof)

---

### **`VehicleCrewDamageMultiplier`**
- **Type**: Float
- **Description**: Collision damage multiplier for the crew. How fast they will blackout or die. 0 is no damage, 1 is vanilla damage, above 1 is stronger than vanilla

---

### **`VehicleSpeedDamageMultiplier`**
- **Type**: Float
- **Description**: Collision damage multiplier for the speed of the car. 0 is no damage, 1 is vanilla damage, above 1 is stronger than vanilla

---

### **`VehicleRoadKillDamageMultiplier`**
- **Type**: Float
- **Description**: Collision damage multiplier for the pedestrians. How fast they will blackout or die. 0 is no damage, 1 is vanilla damage, above 1 is stronger than vanilla

---

### **`CanChangeLock`**
- **Type**: Bool
- **Values**:
  - `0` = Disabled, you cannot change the lock of a vehicle (key)
  - `1` = You can change the lock of a vehicle (key)

---

### **`ChangeLockTools`**
- **Type**: Array
- **Description**: A list of classnames (items) allowed to change the lock of a vehicle

---

### **`ChangeLockTimeSeconds`**
- **Type**: Integer
- **Description**: Time it will take to change the lock in seconds (s)

---

### **`PickLockToolDamagePercent`**
- **Type**: Float
- **Description**: How much damage the tool will take when executing the action (in percentage, from 0 to 100)

---

### **`PlacePlayerOnGroundOnReconnectInVehicle`**
- **Type**: Integer
- **Description**: If the player crash (or server crash). Should the player be placed on the ground?
- **Values**:
  - `0` = disabled
  - `1` = Always
  - `2` = Only on server restarts

---

### **`RevvingOverMaxRPMRuinsEngineInstantly`**
- **Type**: Bool
- **Values**:
  - `0` = Disabled, the engine won't be damaged
  - `1` = Going beyond the red bar from your RPM gauge will ruin the vehicle engine. (vanilla)

---

### **`VehicleDropsRuinedDoors`**
- **Type**: Bool
- **Values**:
  - `0` = Disabled (vanilla)
  - `1` = If a car door is ruined, this door will detach from the vehicle and fall down

---

### **`ExplodingVehicleDropsAttachments`**
- **Type**: Bool
- **Values**:
  - `0` = Disabled (vanilla)
  - `1` = All the attachments of this vehicle will be detached and will fall

---

### **`DesyncInvulnerabilityTimeoutSeconds`**
- **Type**: Float
- **Description**: How long of an invulnerability window is granted during desync

---

### **`DamagedEngineStartupChancePercent`**
- **Type**: Float
- **Description**: Likelyhood of being able to start a damaged (50% health) engine. Gradually approaches this value when the engine is no longer 100% health, and then gradually approaches zero as engine health gets lower than 50%. The transition is linear if startup chance is equal to 50%, and follows a power curve otherwise

---

## Vehicle Covers

### **`EnableVehicleCovers`**
- **Type**: Bool
- **Description**: Enable covering vehicles with a camonet. Not only conceals the vehicle, but also good for server performance since the covered vehicle has no physics

---

### **`AllowCoveringDEVehicles`**
- **Type**: Bool
- **Description**: Allow covering vehicles spawned by dynamic CE events (e.g. events.xml)
- **Note**: You should set nominal and min to zero in your events.xml files before enabling this, or each covered vehicle can respawn!

---

### **`UseVirtualStorageForCoverCargo`**
- **Type**: Bool
- **Description**: Instead of keeping items in cargo on the covered vehicle, they are saved to virtual storage and completely removed from the game world (will be restored when the vehicle is uncovered). May be good for server performance, but loot that is marked count_in_cargo="1" will be able to respawn

---

### **`VehicleAutoCoverTimeSeconds`**
- **Type**: Float
- **Description**: Time in seconds until a vehicle which engine is not running and without driver or passengers will be automatically covered
- **Note**: Vehicles spawned by events.xml will not be automatically covered (see above), you can manually cover it once though which will remove it from the event spawner, after which it will be included in automatic covering

---

### **`VehicleAutoCoverRequireCamonet`**
- **Type**: Bool
- **Description**: Require an attached camonet on the vehicle for autocover

---

## Vehicles Configuration

### **`VehiclesConfig`**
- **Type**: Array
- **Description**: A list of classnames (vehicles) and their config for player attachment

#### **`ClassName`**
- **Type**: String
- **Description**: The classname of the vehicle

#### **`CanPlayerAttach`**
- **Type**: Bool
- **Values**:
  - `0` = Players won't be able to attach on the vehicle
  - `1` = Players can attach on this vehicle while it's moving

#### **`LockComplexity`**
- **Type**: Float
- **Description**: Affects the lockpick chance (higher value = lower chance)

**Example**:
```json
{
    "ClassName": "OffroadHatchback",
    "CanPlayerAttach": 0,
    "LockComplexity": 1.0
}
```
