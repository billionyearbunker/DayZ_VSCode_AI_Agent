# How to Assign a Player to a Faction

---

**Note**: You can also give a faction to a player with DayZ Expansion Quests, however we won't explain how in this guide.

---

## 1. Finding AISettings.json

Inside your server profile go to `ExpansionMod/Settings/AISettings.json`

**Note**: The server profile is where you will find the crash logs, script logs, rpt, permissionframework, expansionmod, console.log and many other folders related to mods. This folder sadly can be renamed and can be found under many names like "config", "instance", "profile" or "sc" to only name a few.

---

## 2. Adding New PlayerFactions

Inside this file you will see a setting similar to this:

```json
"PlayerFactions":[]
```

This setting allows you to specify what faction your players will be in (randomly).

---

## Available Factions

You can currently choose between these factions:

| **Name**                  | **Friendly With**                                                                                                        |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Civilian**              | Everyone that is friendly to them                                                                                        |
| **East**                  | East and Civilian                                                                                                        |
| **West**                  | West and Civilian                                                                                                        |
| **Guards**                | Guards, and players as long as they don't act aggressive (punching, driving fast towards them, raising your weapon, etc) |
| **InvincibleGuards**      | Same as Guards but cannot be killed                                                                                      |
| **Mercenaries**           | Other Mercenaries                                                                                                        |
| **Observers**             | Everyone (won't engage in combat, but will react to surroundings by looking)                                             |
| **InvincibleObservers**   | Same as Observers but cannot be killed                                                                                   |
| **Passive**               | Always friendly toward others until attacked                                                                             |
| **Raiders**               | Nobody, including other Raiders (unless they are part of the same group)                                                 |
| **Shamans**               | Shamans, animals and Infected (Infected and animals won't attack this faction)                                           |
| **YeetBrigade**           | YeetBrigade                                                                                                              |

**Note**: All factions ignore the Passive faction.

---

## Configuration Examples

**Single Faction**:
```json
"PlayerFactions":["West"]
```

**Multiple Factions** (random assignment):
```json
"PlayerFactions":["West","East","Raiders"]
```
