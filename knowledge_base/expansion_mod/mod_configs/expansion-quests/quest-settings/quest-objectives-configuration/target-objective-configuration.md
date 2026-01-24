# Target Objective Configuration

---

## Example Configuration

```json
{
    "ConfigVersion": 26,
    "ID": 1,
    "ObjectiveType": 2,
    "ObjectiveText": "Kill 10 Infected with a sledgehammer",
    "TimeLimit": -1,
    "Active": 1,
    "Position": [
        2596.699951171875,
        306.1000061035156,
        6378.47021484375
    ],
    "MaxDistance": 150.0,
    "MinDistance": -1.0,
    "Amount": 10,
    "ClassNames": [
        "ZmbM_CitizenASkinny_Base",
        "ZmbM_CitizenASkinny_LT_Base",
        "ZmbM_CitizenBFat_Base",
        "ZmbM_ClerkFat_Base",
        "ZmbM_ClerkFat_LT_Base",
        "ZmbM_CommercialPilotOld_Base",
        "ZmbM_CommercialPilotOld_LT_Base",
        "ZmbM_ConstrWorkerNormal_Base",
        "ZmbM_DoctorFat_Base",
        "ZmbM_FarmerFat_Base",
        "ZmbM_FarmerFat_LT_Base",
        "ZmbM_FirefighterNormal_Base",
        "ZmbM_FishermanOld_Base",
        "ZmbM_HandymanNormal_Base",
        "ZmbM_HeavyIndustryWorker_Base",
        "ZmbM_HermitSkinny_Base",
        "ZmbM_HikerSkinny_Base",
        "ZmbM_HunterOld_Base",
        "ZmbM_Jacket_Base",
        "ZmbM_Jacket_LT_Base",
        "ZmbM_JoggerSkinny_Base",
        "ZmbM_Runner_Base",
        "ZmbM_JournalistSkinny_Base",
        "ZmbM_MechanicSkinny_Base",
        "ZmbM_MotobikerFat_Base",
        "ZmbM_OffshoreWorker_Base",
        "ZmbM_ParamedicNormal_Base",
        "ZmbM_PatientSkinny_Base",
        "ZmbM_PolicemanFat_Base",
        "ZmbM_PolicemanSpecForce_Base",
        "ZmbM_priestPopSkinny_Base",
        "ZmbM_PrisonerSkinny_Base",
        "ZmbM_SkaterYoung_Base",
        "ZmbM_SkaterYoung_LT_Base",
        "ZmbM_SurvivorDean_Base",
        "ZmbM_VillagerOld_Base",
        "ZmbM_VillagerOld_LT_Base",
        "ZmbF_BlueCollarFat_Base",
        "ZmbF_CitizenANormal_Base",
        "ZmbF_CitizenANormal_LT_Base",
        "ZmbF_CitizenBSkinny_Base",
        "ZmbF_Clerk_Normal_Base",
        "ZmbF_ClerkFat_Base",
        "ZmbF_Clerk_Normal_LT_Base",
        "ZmbF_DoctorSkinny_Base",
        "ZmbF_HikerSkinny_Base",
        "ZmbF_JoggerSkinny_Base",
        "ZmbF_Runner_Base",
        "ZmbF_JournalistNormal_Base",
        "ZmbF_JournalistNormal_LT_Base",
        "ZmbF_MechanicNormal_Base",
        "ZmbF_MilkMaidOld_Base",
        "ZmbF_MilkMaidOld_LT_Base",
        "ZmbF_NurseFat_Base",
        "ZmbF_ParamedicNormal_Base",
        "ZmbF_PatientOld_Base",
        "ZmbF_PoliceWomanNormal_Base",
        "ZmbF_ShortSkirt_Base",
        "ZmbF_ShortSkirt_LT_Base",
        "ZmbF_SkaterYoung_Base",
        "ZmbF_SkaterYoung_LT_Base",
        "ZmbF_SurvivorNormal_Base",
        "ZmbF_SurvivorNormal_LT_Base",
        "ZmbF_VillagerOld_Base",
        "ZmbF_VillagerOld_LT_Base"
    ],
    "CountSelfKill": 0,
    "AllowedWeapons": [
        "SledgeHammer"
    ],
    "ExcludedClassNames": [],
    "CountAIPlayers": 0,
    "AllowedTargetFactions": [],
    "AllowedDamageZones": []
}
```

---

## Objective Parameters

### **`Position`**
- **Type**: Vector
- **Description**: Objective positions where the given entities need to be eliminated. Leave empty or set to vector 0 to disable this condition

---

### **`MaxDistance`**
- **Type**: Float
- **Description**: If an objective position is defined then the quest players need to be outside the given range when they eliminate a target to count it for the objective

---

### **`MinDistance`**
- **Type**: Float
- **Description**: If an objective position is defined then the quest players need to be within the given range when they eliminate a target to count it for the objective

---

### **`Amount`**
- **Type**: Integer
- **Description**: Amount of eliminations that need to be executed on given entities to complete this objective

---

### **`ClassNames`**
- **Type**: Array[String]
- **Description**: Class names that will be used to control kills. If a unit gets killed that is not in this array the kill will not count for this objective

---

### **`CountSelfKill`**
- **Type**: Boolean
- **Description**: If the target entity is a type of player this parameter controls if player suicides or eliminations on the quest players will count towards the quest objective

---

### **`AllowedWeapons`**
- **Type**: Array[String]
- **Description**: If not empty then this array controls the allowed weapons the quest players can and need to use to kill certain objective targets. If empty this check is disabled

---

### **`ExcludedClassNames`**
- **Type**: Array[String]
- **Description**: Class names of entities that will not count towards the objective when eliminated

---

### **`CountAIPlayers`**
- **Type**: Boolean
- **Description**: If the target entity is a type of expansion AI unit this parameter controls if AI eliminations will count towards the quest objective

---

### **`AllowedTargetFactions`**
- **Type**: Array[String]
- **Description**: Names of the factions a kill target can be in when it is a player or AI. Kills will be only counted when the target is in one of the given factions

---

### **`AllowedDamageZones`**
- **Type**: Array[String]
- **Description**: If not empty then you can define valid hit zones where the player needs to hit to execute an AI unit to count the kill for the objective

**Valid AI/Players and Infected Damage Zones:**
- `Head`
- `Brain`
- `LeftArm`
- `RightArm`
- `LeftLeg`
- `RightLeg`
- `LeftFoot`
- `RightFoot`
- `Torso`

**Note**: For all other entities check the certain RV CfgVehicles configuration class (config.cpp) of the entity and look up the children of the DamageZones class of that type. The children's class names are the damage zone names used for this parameter.
