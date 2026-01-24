# How to Display Modded Kits Their Deployed Model in the Market

---

## Example config.cpp

```cpp
class CfgPatches
{
    class MyMod_MyCustomKits
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
	class Inventory_Base;

	//! This is an example on how to add a preview for an entity that wouldn't normally be able to displayed
	class MyDeployableItem_ExpansionMarketPreview: HouseNoDestruct
	{
		displayName="My Text";
		descriptionShort="My Description";
		model="\DZ\structures\furniture\cases\locker\locker_closed_blue_v1.p3d";
	};
};
```
