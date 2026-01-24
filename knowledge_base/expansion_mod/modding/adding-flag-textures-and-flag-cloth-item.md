# Adding Flag Textures & Flag Cloth Item

## DISCLAIMER

We are not going to teach you how to create a mod or convert images to `.paa`/`.edds`.

---

## Contents

- [config.cpp](#configcpp)
- [FlagSample.c](#flagsamplec)
- [Flag dimensions](#flag-dimensions)

---

## Setup

You will need to setup a mod with the usual `config.cpp` for a basic mod. All the files we will create will need to add new flags.

The hierarchy of the mod we have provided looks like this:

**Hierarchy mod**

---

## config.cpp

```cpp
class CfgPatches
{
	class ExpansionFlagSample
	{
		units[] = {};
		weapons[] = {};
		requiredVersion = 0.1;
		requiredAddons[] = {"DZ_Characters_Tops", "DZ_Gear_Camping"};
	};
};
class CfgMods
{
	class ExpansionFlagSample
	{
		dir = "ExpansionFlagSample";
		picture = "";
		action = "";
		hideName = 1;
		hidePicture = 1;
		name = "ExpansionFlagSample";
		credits = "ExpansionModTeam";
		author = "ExpansionModTeam";
		authorID = "0";
		version = "1.0";
		extra = 0;
		type = "mod";
		dependencies[] = {"Game"};
		class defs
		{
			class gameScriptModule
			{
				value = "";
				files[] = {"ExpansionFlagSample/scripts/3_Game"};
			};
		};
	};
};
class CfgVehicles
{
	// config for the flag item
	class Flag_Base;
	class Expansion_Flag_BohemiaInteractive: Flag_Base
	{
		scope=2;
		hiddenSelectionsTextures[]=
		{
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa"
		};
		color="Expansion_BohemiaInteractive"; // for armbands - optional
	};

	// config for the flag armband item - optional
	class Armband_ColorBase;
	class Expansion_Armband_BohemiaInteractive: Armband_ColorBase
	{
		scope=2;
		visibilityModifier=0.94999999;
		color="Expansion_BohemiaInteractive";
		hiddenSelectionsTextures[]=
		{
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa",
			"\ExpansionFlagSample\data\flag_bohemiainteractive_co.paa"
		};
	};
};
FlagSample.c
In case you do NOT create a flag item as shown above, you have to add the flag texture for the flag menu manually by adding the following to your mod within the game script module (3_Game):

modded class ExpansionFlagTextures
{
	override void Load()
	{
		super.Load();
		// This is where you want to add or remove flags !
		Add("<path to flag texture>", "Flag Example 1");
		Add("<path to flag texture>", "Flag Example 2");  // etc
	};
};
If you want to remove a flag that is already added by expansion you will need to add the following line to that modification:

Remove("DayZExpansion\\Objects\\Structures\\Flags\\data\\logos\\flag_expansion_co.paa");
This is an example for adding 2 new flags and remove the expansion logo flag from the expansion mod:

modded class ExpansionFlagTextures
{
	override void Load()
	{
		super.Load();
		// This is where you want to add or remove flags !
		Add("ModName\\data\\flag_name_co.paa", "MyFlagName");
		Add("ModName\\data\\flag_name2_co.paa", "MyFlagName2");
		Remove("DayZExpansion\\Objects\\Structures\\Flags\\data\\logos\\flag_expansion_co.paa");
	};
};
Flag dimensions
The texture need to have 2:1 dimensions. For example a texture of 512 pixels by 256 pixels will work.
