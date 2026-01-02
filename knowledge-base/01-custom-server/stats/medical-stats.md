# DayZ Custom Medical Stats

## Important Notes on Data
- Name: The human-readable label used to identify the medical supply or instrument in the game inventory.
- Class Name: The technical identifier string used by the server configuration to spawn or reference the specific item.
- Size: The integer number of inventory grid slots the item occupies when stored.
- Wgt: The numeric mass of the item (typically in grams), abbreviated from "Weight," which contributes to player load.
- Location: The specific building types or map tiers (e.g., "Hospital," "Tier 3") where the item is configured to spawn.
- Used To Treat: The specific diseases, symptoms, or physical trauma (e.g., "Cholera," "Shock," "Bleeding") that the item remedies.
- Capacity (Full): The maximum unit count (pills), volume (milliliters), or percentage of uses available when the item is pristine.
- Rarity: A qualitative indicator describing the spawn probability relative to other medical loot.
- Description: A functional summary detailing the item's application method and its physiological effects on the player.

## Pharmaceuticals (Pills & Tablets)
The primary defense against sickness and disease. Note: Taking different pills simultaneously often cancels their effects (except Vitamins).

| Name                 | Class Name              | Size | Wgt | Location          | Used To Treat                   | Capacity (Full) | Rarity   | Description                                                 |
|----------------------|-------------------------|------|-----|-------------------|---------------------------------|-----------------|----------|-------------------------------------------------------------|
| Tetracycline         | TetracyclineAntibiotics | 1x2  | 20g | Hospital, Medical | Cholera, Wound Infection        | 12 Pills        | Uncommon | Antibiotics. Essential for bacterial infections.            |
| Charcoal Tablets     | CharcoalTablets         | 1x2  | 20g | Hospital, Medical | Salmonella, Food/Chem Poisoning | 12 Pills        | Common   | Absorbs toxins from raw meat or gasoline ingestion.         |
| Codeine Pills        | PainkillerTablets       | 1x2  | 20g | Hospital, Medical | Coughing (Flu/Cold)             | 12 Pills        | Common   | Suppresses coughing symptoms. Does not cure the cold itself.|
| Multivitamins        | VitaminBottle           | 1x2  | 20g | Hospital, Civ     | Weak Immune System              | 50 Pills        | Rare     | Boosts immunity to 100%. Helps fight all diseases faster.   |
| Water Purification   | PurificationTablets     | 1x2  | 20g | Camp, Hunt        | Dirty Water (Cholera Risk)      | 10 Pills        | Common   | One pill purifies a container of water.                     |

## Injectors & First Aid
Emergency treatments for trauma and critical conditions.

| Name           | Class Name      | Size | Wgt  | Location           | Used To Treat              | Capacity | Rarity  | Description                                                         |
|----------------|-----------------|------|------|--------------------|----------------------------|----------|---------|---------------------------------------------------------------------|
| Morphine       | Morphine        | 1x1  | 50g  | Hospital, Military | Limping (Broken Legs/Pain) | 1 Use    | Rare    | Suppresses pain for 1 minute. Allows sprinting with injury.         |
| Epinephrine    | Epinephrine     | 1x1  | 50g  | Hospital, Military | Unconsciousness, Stamina   | 1 Use    | Rare    | Wakes up unconscious players instantly. Infinite stamina for 1 min. |
| PO-X Antidote  | POXAntidote     | 1x1  | 50g  | NBC Zones, Mil     | Gas Zone Poisoning         | 1 Use    | V. Rare | The only cure for Gas Poisoning (besides clean blood).              |
| Bandage        | BandageDressing | 1x2  | 100g | Hospital, Mil      | Bleeding (Cuts)            | 4 Uses   | Common  | Sterile dressing. Stops bleeding faster than rags.                  |
| Blood Test Kit | BloodTestKit    | 1x1  | 50g  | Hospital           | Unknown Blood Type         | 1 Use    | Common  | Determines blood type (A, B, AB, O, +/-).                           |

## IV Fluids & Blood
Used to recover from massive blood loss or dehydration. Requires an IV Start Kit to function.

| Name              | Class Name    | Size | Wgt  | Location | Used To Treat           | Capacity | Rarity   | Description                                                |
|-------------------|---------------|------|------|----------|-------------------------|----------|----------|------------------------------------------------------------|
| IV Start Kit      | StartKitIV    | 1x1  | 50g  | Hospital | N/A (Tool)              | 1 Use    | Common   | Needle/tube required to inject Saline or Blood Bags.       |
| Saline Bag        | SalineBag     | 2x2  | 200g | Hospital | Hydration / Blood Regen | 500ml    | Uncommon | Increases hydration and speeds up natural blood recovery.  |
| Blood Bag (Empty) | BloodBagEmpty | 2x2  | 100g | Hospital | Collection              | 1 Use    | Common   | Used to draw blood from a donor.                           |
| Blood Bag (Full)  | BloodBagIV    | 2x2  | 500g | Crafted  | Blood Loss              | 500ml    | -        | Filled blood bag + IV Start Kit. Restores blood instantly. |

## Disinfectants & Tools
Used to clean wounds or purify items to prevent infection.

| Name               | Class Name        | Size | Wgt  | Location         | Used To Treat   | Capacity | Rarity | Description                                           |
|--------------------|-------------------|------|------|------------------|-----------------|----------|--------|-------------------------------------------------------|
| Alcohol Tincture   | AlcoholTincture   | 1x2  | 200g | Hospital, Garage | Wounds, Items   | 200ml    | Common | Disinfects rags/wounds. Can induce sickness if drunk. |
| Iodine Tincture    | IodineTincture    | 1x2  | 200g | Hospital         | Wounds, Items   | 200ml    | Common | Strong disinfectant. Do not drink.                    |
| Disinfectant Spray | DisinfectantSpray | 2x2  | 300g | Hospital, Civ    | Items, Surfaces | 350ml    | Common | Cleaning spray. Highly toxic if ingested.             |
| Thermometer        | Thermometer       | 1x1  | 50g  | Hospital         | Fever Diagnosis | Infinite | Common | Tells you if your character has a fever.              |
