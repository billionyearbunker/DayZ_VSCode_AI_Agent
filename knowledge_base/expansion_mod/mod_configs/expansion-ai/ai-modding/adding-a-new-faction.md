# Adding a New Faction

---

## Overview

In this example we are creating a new faction named "Reforger". If you want to create a faction with a different name, simply rename ALL the "Reforger" mentions.

---

## Code Implementation

**File Location**: `YourMod/Scripts/3_Game`

```cpp
[eAIRegisterFaction(eAIFactionReforger)]
class eAIFactionReforger : eAIFaction
{
	void eAIFactionReforger()
	{
		// The name of your Faction
		m_Name = "Reforger";

		// The name of the loadout your Faction will use by DEFAULT
		// used if the server doesn't specify a loadout
		m_Loadout = "ReforgerLoadout";

		// ==============================================
		// OPTIONAL SETTINGS - REMOVE IF YOU DONT NEED IT
		
		// Is this Faction meant to behave like Guards
		m_IsGuard = true;

		// If you want your faction to be invicible (godmode)
		m_IsInvincible = true;

		// Peacefull, Obeserver
		m_IsPassive = true;

		// 1.0 = default | 2.0 = 2x
		m_MeleeDamageMultiplier = 100.0;

		// Joke settings
		m_MeleeYeetForce = 15.0;
		m_MeleeYeetFactors = "0.5 1 0.5";

		// Prevent AIs with this setting to pick up weapons
		m_DisableWeaponPickup = true;
		
		// AIs have unlimited Stamina
		m_HasUnlimitedStamina = true;
		
		// You can also apply permanent diseases to AIs.
		// BRAIN will make them laugh (kuru) and flies.. well you got it
		AddModifier(eModifiers.MDF_BRAIN);
		AddModifier(eModifiers.MDF_FLIES);

		// OPTIONAL SETTINGS - REMOVE IF YOU DONT NEED IT
		// ==============================================
	}

	// Used to check if the target Faction should be considered Friendly
	override bool IsFriendly(notnull eAIFaction other)
	{
		// If you dont want your own Faction to kill each others make them friendly to their own Faction
		if (other.IsInherited(eAIFactionReforger)) return true;

		if (other.IsInherited(eAIFactionCivilian)) return true;
		
		// You can also do this for Guards and Passive factions
		// instead of adding all of them one by one 
		if (other.IsPassive()) return true;
		if (other.IsGuard()) return true;

		return false;
	}

	// Used to check if the target EntityAI should be considered Friendly
	// You do not need to add this function unless if you want a special behavior
	// The default behaviour doesnt require this function.
	override bool IsFriendlyEntity(EntityAI other)
	{
		return other.IsInherited(DayZCreatureAI);
	}

	// You can use localized strings for the Faction Display Name if you want to as well
	override string GetDisplayName()
	{
		return "#STR_EXPANSION_AI_FACTION_YEETBRIGADE";
	}
};
```

---

## Default Factions

These are the default factions we are providing:

- `eAIFactionCivilian`
- `eAIFactionEast`
- `eAIFactionWest`
- `eAIFactionMercenaries`
- `eAIFactionRaiders`
- `eAIFactionGuards`
- `eAIFactionPassive`
- `eAIFactionShamans`
