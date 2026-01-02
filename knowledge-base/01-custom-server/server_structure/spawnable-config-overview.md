# DayZ Custom Spawnable Configurations: cfgspawnabletypes.xml Architecture

**Subject:** DayZ Server Structure  
**Version Context:** 1.26 (Stable)  
**Purpose:** Technical documentation of cfgspawnabletypes.xml architecture, attachment logic, and spawning mechanics

---

## 1. File Overview & Scope

**Path:** `/mpmissions/dayzOffline.chernarusplus/cfgspawnabletypes.xml`

**Role:** The "Decorator" of the economy. It dictates the state of an item immediately after the Central Economy (`types.xml`) decides to spawn it.

**Primary Function:** It answers the question, "This object has spawned; now, what is attached to it or inside it?"

**Key Use Cases:**
- Spawning guns with magazines and optics.
- Spawning cars with wheels, doors, and spark plugs.
- Spawning Infected (Zombies) with specific clothing sets.
- Spawning First Aid kits containing bandages.

---

## 2. The Dependency: cfgrandompresets.xml
This file rarely works alone. It relies heavily on "Presets" defined in a sibling file: cfgrandompresets.xml.

This file rarely works alone. It relies heavily on "Presets" defined in a sibling file: `cfgrandompresets.xml`.

**Concept:** Instead of listing every possible fruit inside a backpack spawn, `cfgspawnabletypes.xml` will simply reference `<cargo preset="foodFruit" />`.

**Resolution:** The engine looks up "foodFruit" in `cfgrandompresets.xml`, picks an item from that list, and inserts it.

Wrapped in a generic root tag.

```xml
<spawnabletypes>
    </spawnabletypes>

Links the configuration to a specific class name.

**Inheritance:** Unlike `config.cpp`, this file does not support inheritance.

**Implication:** If you define a configuration for `ZmbM_SoldierNormal_Base`, it will not automatically apply to `ZmbM_SoldierNormal_Summer`. You must explicitly define the type for every specific class name you want to affect.

---

## 5. Logic A: Attachments (Weapons & Vehicles)
4. The <type> Definition
Links the configuration to a specific class name.

**Inheritance:** Unlike `config.cpp`, this file does not support inheritance.

**Implication:** If you define a configuration for `ZmbM_SoldierNormal_Base`, it will not automatically apply to `ZmbM_SoldierNormal_Summer`. You must explicitly define the type for every specific class name you want to affect.

---

## 5. Logic A: Attachments (Weapons & Vehicles)

Used to attach items to the proxy slots of the parent entity.

### Syntax

```xml
<type name="M4A1">
    <attachment chance="1.00">
        <item name="M4_OEBttstck" chance="1.00" />
    </attachment>
    <attachment chance="0.50">
        <item name="M4_CarryHandleOptic" chance="1.00" />
    </attachment>
</type>
```

### Attributes

- `<attachment chance="0.50">`: The probability (0.0 to 1.0) that this slot will be filled.
- `<item name="..." chance="1.00">`: If the slot is selected to be filled, this is the probability that this specific item is chosen.
- **Logic:** You can list multiple `<item>` tags inside one `<attachment>` tag. The engine will roll the dice to pick one.

### The Vehicle Use Case (Ready-to-Drive)

To make a car spawn with full parts, you must edit the `<type>` for that vehicle.


To make a car spawn with full parts, you must edit the `<type>` for that vehicle.

- **Wheels:** Often defined individually or by passing a preset.
- **Batteries/Plugs:** Defined as attachments.
- **Doors/Hoods:** Defined as attachments.

**Example:** Changing `<attachment chance="0.30">` to "1.00" for the Spark Plug ensures every car found has a plug.

---

## 6. Logic B: Cargo (Inventory Contents)

Used to place items inside the inventory of the spawned object (Backpacks, Clothing, Containers).

### Syntax

```xml
<type name="FirstAidKit">
    <cargo chance="1.00">
        <item name="BandageDressing" chance="1.00" />
        <item name="BloodBagIV" chance="0.10" />
    </cargo>
</type>
```

### Attributes

- `<cargo chance="...">`: Probability that the cargo logic runs at all.
- `<item name="...">`: Specific item to insert.
- `<tag name="...">`: References a category of items (often used for Infected loot).

**Example:** `<tag name="floor" chance="0.10" />` implies it pulls from a generic "floor loot" definition often hardcoded or defined in presets.

---

## 7. Logic C: Quality & State (Damage)


You can randomize the damage state of the attached items using `<hoarder />` tags or implicit logic within the entry.

### The <hoarder /> Tag (Spawn Quality)

Despite the name, in `cfgspawnabletypes.xml`, this tag controls the quality (damage) of the attachments/cargo, not "hoarding" behavior.

```xml
<hoarder class="20" />
```

- **Class Values:** usually map to probability tables defined in engine presets for "Ruined", "Badly Damaged", "Damaged", "Worn", "Pristine".
- **Default:** If omitted, attachments usually spawn Pristine (or randomized based on global defaults).

---

## 8. Complex Example: The Infected (Zombie) Setup

Zombies are defined here to randomize their appearance.

```xml
<type name="ZmbM_JournalistSkinny_Base">
    <cargo preset="foodCommon_Any" />
    <attachment chance="1.00">
        <item name="ZmbM_JournalistSkinny_Blue_Bottoms" chance="0.25" />
        <item name="ZmbM_JournalistSkinny_Green_Bottoms" chance="0.25" />
        <item name="ZmbM_JournalistSkinny_Red_Bottoms" chance="0.25" />
    </attachment>
</type>
```

**Analysis:**
- **Cargo:** Uses a preset `foodCommon_Any` (from `cfgrandompresets.xml`) to put food in the zombie's inventory.
- **Attachment:** Forces a 100% chance to have pants, but splits the 100% chance evenly between Blue, Green, and Red variants.

### Magazines & Ammo

- Weapons spawned via `cfgspawnabletypes` with magazines will usually have the magazine attached, but the magazine might be empty.
- To ensure ammo is inside the magazine, specific `cfgmagazinetypes.xml` files or `cfgrandompresets` logic is often involved, or it is hardcoded in the weapon class `config.cpp` default behavior.

### Conflict with types.xml

- If `types.xml` says "Spawn M4A1", the CLE spawns the M4A1 entity.
- Then, `cfgspawnabletypes.xml` fires to add the buttstock and handguard.
- **Crucial:** If you delete the M4A1 entry from `cfgspawnabletypes.xml`, the gun will spawn "Naked" (Receiver only). It will not be functional.

### Vehicles & "Ruined" Parts

- Even if you set attachment chance to 1.00, the condition of that part (Pristine vs Ruined) is often governed by a global variable in `globals.xml` or the `<hoarder>` class value. A car might spawn with 4 wheels, but 2 might be ruined if the server difficulty is high.

---

## 10. Modding Best Practices

**File Name:** Create `custom_spawnabletypes.xml`.

**Registration:**

```xml
<ce folder="db">
    <file name="cfgspawnabletypes.xml" type="spawnabletypes" />
    <file name="custom_spawnabletypes.xml" type="spawnabletypes" />
</ce>
```

**Validation:** XML syntax errors here (e.g. unclosed tags) will often result in "Naked Spawns" globally—zombies with no clothes, cars with no wheels, guns with no stocks.
