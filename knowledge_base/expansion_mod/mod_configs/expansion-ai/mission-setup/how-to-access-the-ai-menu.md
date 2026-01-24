# How to Access the AI Menu

---

## 1. Finding AISettings.json

Inside your server profile go to `ExpansionMod/Settings/AISettings.json`

**Note**: The server profile is where you will find the crash logs, script logs, rpt, permissionframework, expansionmod, console.log and many other folders related to mods. This folder sadly can be renamed and can be found under many names like "config", "instance", "profile" or "sc" to only name a few.

---

## 2. Setting Yourself Admin

Inside this file you will see a setting similar to this:

```json
"Admins":[]
```

You will need to give your SteamID64 to make yourself admin:

```json
"Admins":["76561198959715227"]
```

You can also make your friends admin as shown with this example:

```json
"Admins":[
    "76561198959715227",
    "76561198144647312",
    "76561198045934831",
    "76561197968396131",
    "76561198103677868"
]
```

---

## 3. Using the Menu

**Default Key**: **T**

**Functionality**:
- If you have allied AI following you, you can make them change formation, tell them to stop or rejoin formation and set or clear waypoints
- As admin, you will also be able to spawn friendly or hostile AI from various factions as well as Zs and wolves/bears
