# DamageSystemSettings

---

For more consistent and reliable explosion damage to items, the Expansion damage system can be enabled and will be used in addition to the vanilla damage system.

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer
- **Description**: Contains the current setting version number, never change this value unless you really know what you are doing as it's used internally for automatic conversion of old settings whenever we change something

---

### **`Enabled`**
- **Type**: Bool
- **Description**: Turn the whole system on/off (default enabled if using Expansion Basebuilding)

---

### **`CheckForBlockingObjects`**
- **Type**: Bool
- **Description**: Whether to check if an object (building or large item) is blocking the path from the explosion source to the target (default enabled). When turning this off, the only determining factor for explosion damage is distance between explosion source and target, regardless if there are any objects in between

---

### **`ExplosionTargets`**
- **Type**: Array (string)
- **Description**: List of config or script classnames that should use the Expansion explosion damage system (default `["ExpansionBaseBuilding", "ExpansionSafeBase"]` if using Expansion Basebuilding)
- **Note**: These are not explosives, but items that should receive the damage!

---

### **`ExplosiveProjectiles`**
- **Type**: Map (string)
- **Description**: Classnames of explosive projectiles mapped to their respective explosive ammo (e.g. `{"Bullet_40mm_Explosive": "Explosion_40mm_Ammo"}`). This is needed for some vanilla projectiles like the M79 explosive grenade

---

## Example Configuration

```json
{
    "m_Version": 1,
    "Enabled": 1,
    "CheckForBlockingObjects": 1,
    "ExplosionTargets": [
        "ExpansionBaseBuilding",
        "ExpansionSafeBase"
    ],
    "ExplosiveProjectiles": {
        "Bullet_40mm_Explosive": "Explosion_40mm_Ammo"
    }
}
```
