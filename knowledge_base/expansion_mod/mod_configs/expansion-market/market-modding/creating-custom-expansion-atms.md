# Creating Custom Expansion ATMs

---

## Example config.cpp

```cpp
class CfgPatches
{
    class MyMod_Market_ATM
    {
        units[]={};
        weapons[]={};
        requiredVersion=0.1;
        requiredAddons[]=
        {
            "DZ_Data"
        };
    };
};
class CfgVehicles
{
	class HouseNoDestruct;
	class MyCustomATM: HouseNoDestruct
	{
		scope=1;
		vehicleClass = "Expansion_Static";
		model="\DZ\structures\furniture\cases\locker\locker_closed_blue_v1.p3d";
	};
};
```

---

## Script Class Example

For an ATM in the `4_World` script module of your mod:

```cpp
class MyCustomATM: ExpansionATMBase {};
```
