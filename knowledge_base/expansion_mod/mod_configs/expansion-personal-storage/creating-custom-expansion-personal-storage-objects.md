# Creating Custom Expansion Personal Storage Objects

---

## Overview

If you plan to add your custom personal storage object for the Expansion Personal Storage system, you can find some examples for the needed object configuration as well as the needed script classes for the object here.

---

## Example config.cpp

```cpp
class CfgPatches
{
    class MyMod_PersonalStorage_Objects
    {
        units[]={};
        weapons[]={};
        requiredVersion=0.1;
        requiredAddons[]=
        {
            "DayZExpansion_PersonalStorage_Objects"
        };
    };
};

class CfgVehicles
{
	class ExpansionPersonalStorageBase;
	class MY_PERSONAL_STROAGE: ExpansionPersonalStorageBase
	{
		scope = 1;
		model = "\DZ\gear\camping\sea_chest.p3d";
	};
};
```

---

## Script Class Example

For a personal storage object in the `4_World` script module of your mod:

```cpp
class MY_PERSONAL_STROAGE: ExpansionPersonalStorageBase {};
```
