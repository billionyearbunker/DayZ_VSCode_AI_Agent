# Hardline Settings

---

## Finding HardlineSettings.json

Inside your `mpmissions/dayzoffline.mapname/expansion/settings/` you will find the **HardlineSettings.json**

---

## Setting Parameters

### **`m_Version`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Current setting file version. Never change this unless you know what you are doing!

---

## Item Rarity Requirements

### **`PoorItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "poor"

---

### **`CommonItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "common"

---

### **`UncommonItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "uncommon"

---

### **`RareItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "rare"

---

### **`EpicItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "epic"

---

### **`LegendaryItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "legendary"

---

### **`MythicItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "mythic"

---

### **`ExoticItemRequirement`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Required player reputation points to buy/sell an item from the market that has the rarity "exotic"

---

## HUD and Display Settings

### **`ShowHardlineHUD`**
- **Type**: Boolean
- **Description**: Show/hide the hardline reputation points indicator in the main HUD

---

## Reputation System

### **`UseReputation`**
- **Type**: Boolean
- **Description**: Use the hardline reputation system and let players gain reputation points for certain actions like eliminating an entity

---

### **`UseFactionReputation`**
- **Type**: Boolean
- **Description**: Use the faction reputation system and let players gain reputation points for all valid eAIFactions individually that they can join

---

### **`EnableFactionPersistence`**
- **Type**: Boolean
- **Description**: Enable/disable faction persistence so players can join a faction and stay in that faction over server restarts

---

## Item Rarity System

### **`EnableItemRarity`**
- **Type**: Boolean
- **Description**: Enable/disable the item rarity system. Will display the configured rarity given in the "ItemRarity" array on items in tooltips, icons or some menus

---

### **`UseItemRarityOnInventoryIcons`**
- **Type**: Boolean
- **Description**: Enable/disable if items icons and slots get colorized with the configured rarity color given in the "ItemRarity" array. The feature can also be disabled in the in-game client settings if this setting is enabled so players can always disable the colors

---

### **`UseItemRarityForMarketPurchase`**
- **Type**: Boolean
- **Description**: Enable/disable if players can only buy items from the market if they have the required reputation points for the certain item defined in the item required parameters for each individual item rarity. So if an item has a rarity has an Epic rarity defined in the "ItemRarity" array the player will need the required reputation points defined in the "EpicItemRequirement" parameter to buy the certain item

---

### **`UseItemRarityForMarketSell`**
- **Type**: Boolean
- **Description**: Enable/disable if players can only sell items at the market if they have the required reputation points for the certain item defined in the item required parameters for each individual item rarity. So if an item has a rarity has an Epic rarity defined in the "ItemRarity" array the player will need the required reputation points defined in the "EpicItemRequirement" parameter to sell the certain item

---

### **`MaxReputation`**
- **Type**: Integer
- **Description**: Max reputation points a player can reach overall

---

### **`ReputationLossOnDeath`**
- **Type**: Integer
- **Description**: Reputation points a player will lose whenever he dies to an enemy player or another entity

---

### **`DefaultItemRarity`**
- **Type**: Integer<ExpansionHardlineItemRarity>
- **Description**: Default item rarity for all items that have no entry defined in the "ItemRarity" array

---

## Entity and Item Configuration

### **`EntityReputation`**
- **Type**: Map<String, Integer>
- **Description**: Need to be a valid entity class name and a reputation value that should get added or deducted from the player when eliminating the certain entity. Can be a base class name or a specific one

---

### **`ItemRarity`**
- **Type**: Map<String, ExpansionHardlineItemRarity>
- **Description**: Defines item rarity of an item when the "EnableItemRarity" parameter is enabled. Needs to be a valid item base class name and an item rarity value (ExpansionHardlineItemRarity)

---

## Item Rarities [ExpansionHardlineItemRarity]

- **Poor** = 1
- **Common** = 2
- **Uncommon** = 3
- **Rare** = 4
- **Epic** = 5
- **Legendary** = 6
- **Mythic** = 7
- **Exotic** = 8
- **Quest** = 9
- **Collectable** = 10
- **Ingredient** = 11

---

## Example Configuration

Example setting JSON file:

```json
{
    "m_Version": 10,
    "PoorItemRequirement": 0,
    "CommonItemRequirement": 0,
    "UncommonItemRequirement": 0,
    "RareItemRequirement": 0,
    "EpicItemRequirement": 0,
    "LegendaryItemRequirement": 0,
    "MythicItemRequirement": 0,
    "ExoticItemRequirement": 0,
    "ShowHardlineHUD": 1,
    "UseReputation": 1,
    "UseFactionReputation": 1,
    "EnableFactionPersistence": 1,
    "EnableItemRarity": 1,
    "UseItemRarityOnInventoryIcons": 1,
    "UseItemRarityForMarketPurchase": 0,
    "UseItemRarityForMarketSell": 0,
    "MaxReputation": 10000,
    "ReputationLossOnDeath": 100,
    "DefaultItemRarity": 2,
    "EntityReputation": {
        "Animal_GallusGallusDomesticus": 1,
        "eAIBase": 100,
        "AnimalBase": 10,
        "ZmbM_SoldierNormal_Base": 20,
        "Animal_UrsusArctos": 50,
        "ZmbM_NBC_Grey": 20,
        "ZombieBase": 10,
        "PlayerBase": 100,
        "Animal_UrsusMaritimus": 50,
        "ZmbM_NBC_Yellow": 20
    },
    "ItemRarity": {
        "aviatorglasses": 3,
        "booniehat_blue": 4,
        "canvas_backpack_red": 4,
        "civsedandoors_driver_black": 4,
        "tomato": 3,
        "joggingshoes_black": 2,
        "sparkplug": 4,
        "mag_cz550_10rnd": 5,
        "flag_chel": 1
    }
}
```
