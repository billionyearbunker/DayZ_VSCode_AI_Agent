# Creating Custom Expansion Trader entities and NPCs

---

## Overview

If you plan to add your custom trader entities for the Expansion Market system, you can find some examples for the needed object configuration as well as the needed script classes for NPCs here.

---

## Example config.cpp

```cpp
class CfgPatches
{
    class MyMod_Market_TraderEntities
    {
        units[]={};
        weapons[]={};
        requiredVersion=0.1;
        requiredAddons[]=
        {
            "DZ_Characters",
            "DZ_Characters_Zombies",
            "DayZExpansion_Market_Objects",
            "DayZExpansion_Market_Scripts"
        };
    };
};

class CfgVehicles
{
    //! Default base classes for our config
    //! Make sure you include the correct base classes here depending on the object(s) you are going to add.
    class SurvivorF_Eva;
    class ZmbM_JournalistSkinny;

    //! NPC trader base class(es) from Expansion
    class ExpansionTraderDenis;

    //! Static trader base class from Expansion
    class ExpansionTraderStaticBase;

    //! Example for a static trader object
    class ExpansionTraderLockerClosedBlueV1Custom: ExpansionTraderStaticBase
    {
        scope = 1;
        displayName="$STR_EXPANSION_VENDING_MACHINE";
        model="\DZ\structures\furniture\cases\locker\locker_closed_blue_v1.p3d";
        rotationFlags=12;
    };

    //! Example for a NPC trader
    class MyCustomTraderEva: SurvivorF_Eva
    {
        scope = 2;
        displayName = "Eva";
        vehicleClass = "Expansion_Trader";
    };

    //! Example Enfusion AI NPC trader using Expansion NPC
    class MyCustomTraderAIDenis: ExpansionTraderDenis {};

    //! Example Enfusion AI NPC trader using your custom NPC
    class MyCustomTraderAIEva: MyCustomTraderEva {};

    //! Example Infected trader
    class MyCustomTraderZmbM_JournalistSkinny: ZmbM_JournalistSkinny
    {
        scope = 2;
        displayName = "...";
        vehicleClass = "Expansion_Trader";
    };
};
```

---

## Script Class Examples

### NPC Trader

Script class example for a NPC trader in the **4_World** script module of your mod:

```cpp
class MyCustomTraderDenis: ExpansionTraderNPCBase {};
```

### Enfusion AI NPC Trader

Script class example for an Enfusion AI NPC trader in the **4_World** script module of your mod:

```cpp
class MyCustomTraderAIDenis: ExpansionTraderAIBase {};
```

### Infected Trader

Script class example for an Infected trader in the **4_World** script module of your mod:

```cpp
class MyCustomTraderZmbM_JournalistSkinny: ExpansionTraderZombieBase {};
```

---

## Static Objects

Static objects don't need any additional script code.
