# Adding Custom Mapping

## Overview

You can spawn objects as well as remove existing world objects.

**Requirements:**
- Any tools which can spawn objects, place them and save will work
- We recommend using the **DayZ Editor**

Yes, you can also use any other tools which can provide you the position of an object or use any other mapping formats for props and atms (but not for traders, they need to be in our `.map` format).

If you use VPP and want to use the VPP Editor, yes you can for example :)

---

## .map Files

Expansion loads custom mapping and removals from simple text files with the extension `.map`

Create new `.map` file(s) in the directory:

```
dayzOffline.WORLDNAME\expansion\objects
```

Paste in the exported lines.

The file can be named whatever you want as the system will load every correct `.map` file in this folder.

---

## Spawning Objects

Example spawning ATMs at Green Mountain:

```
ExpansionATMLocker|3683.187744 402.672913 5981.407227|160.837372 -0.000000 -0.000000
ExpansionATM_1|3684.090820 402.672913 5981.735840|159.101990 0.000000 0.000000
ExpansionATM_2|3681.674805 402.672913 5983.201172|-111.389977 -0.000000 -0.000000
ExpansionATM_3|3682.115967 402.672913 5982.123047|-109.500908 -0.000000 -0.000000
```

- **First column:** The classname of the object to be spawned
- **Second column:** The position
- **Third column:** The orientation (yaw/pitch/roll)
- **Fourth column (optional):** When set to true will light the object on fire if it is a fireplace or flare

---

## Removing Objects

Example removing an existing world object:

```
-Land_House_1W02|4389.718262 304.723969 6460.789551
```

- **First column:** The classname of the object preceded by a minus sign (`-`) indicating that the object should be removed. The classname can contain a single asterisk (`*`) as a placeholder character (e.g. `Land_House_*`)
- **Second column:** The position
- **Third column (optional):** The radius in meters (default 0.1)
