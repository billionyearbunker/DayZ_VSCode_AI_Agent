# Adding an ATM

---

## Overview

If you want to add an ATM you can use any mapping method (.map, dayz editor, vpp mapping, etc). In this guide we will explain with the .map method.

---

## Steps

1. Go to `dayzserver/mpmissions/dayzoffline.mapname/expansion/objects/`
2. Create a file named **MyMappingATM.map** (or open a file you already made)
3. In this file add the following line:

```
ExpansionATMLocker|11855.7 140.565 12453.6|-70.000000 0.000000 0.000000
```

---

## Format Structure

```
Classname|Position X Y Z|Rotation
```

---

## ATM Classnames

- `ExpansionATMLocker`
- `ExpansionATM_1`
- `ExpansionATM_2`
- `ExpansionATM_3`
