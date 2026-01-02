# DayZ Custom Food Stats

## Important Notes on Data
- Name: The human-readable label displayed in the game inventory to identify the edible item.
- Class Name: The technical identifier string used to spawn the base item or reference it in loot tables.
- Size: The integer number of inventory slots the food item occupies.
- Weight: The mass of the item (typically in grams), affecting player stamina and load.
- Spoil: A boolean or condition flag indicating if the item is capable of rotting over time or upon opening.
- Raw Energy: The caloric value (kilocalories) gained by the player when consuming the item in its uncooked state.
- Raw Water: The hydration value (milliliters) gained by the player when consuming the item in its uncooked state.
- Baked Energy: The caloric value gained when the item is consumed after being cooked on a pan or fat.
- Baked Water: The hydration value gained when the item is consumed after being cooked on a pan or fat (usually lower than raw).
- Boiled Energy: The caloric value gained when the item is consumed after being cooked in a pot with water.
- Boiled Water: The hydration value gained when the item is consumed after being cooked in a pot with water (usually the highest hydration method).
- Dried Energy: The caloric value gained when the item is consumed after being preserved via drying or smoking.
- Dried Water: The hydration value gained when the item is consumed after being preserved via drying or smoking (significantly reduced).

## Meats (Steaks & Fillets)
Cooking significantly increases Energy (Calories) but usually reduces Water content (except Boiling).

| Name        | Class Name         | Size | Weight | Spoil | Raw Energy | Raw Water | Baked Energy | Baked Water | Boiled Energy | Boiled Water | Dried Energy | Dried Water |
|-------------|--------------------|------|--------|-------|------------|-----------|--------------|-------------|---------------|--------------|--------------|-------------|
| Bear Steak  | BearSteakMeat      | 1x3  | 400g   | 24h   | 250        | 68        | 400          | 95          | 300           | 92           | 260          | 11          |
| Boar Steak  | PigSteakMeat       | 1x3  | 400g   | 24h   | 185        | 62        | 350          | 83          | 250           | 82           | 225          | 11          |
| Cow Steak   | CowSteakMeat       | 1x3  | 400g   | 24h   | 188        | 62        | 338          | 83          | 260           | 82           | 225          | 11          |
| Deer Steak  | DeerSteakMeat      | 1x3  | 400g   | 24h   | 196        | 63        | 310          | 84          | 240           | 83           | 225          | 11          |
| Goat Steak  | GoatSteakMeat      | 1x3  | 400g   | 24h   | 196        | 63        | 310          | 84          | 240           | 83           | 225          | 11          |
| Sheep Steak | SheepSteakMeat     | 1x3  | 400g   | 24h   | 196        | 63        | 310          | 84          | 240           | 83           | 225          | 11          |
| Wolf Steak  | WolfSteakMeat      | 1x3  | 400g   | 24h   | 196        | 63        | 310          | 84          | 240           | 83           | 225          | 11          |
| Chicken     | ChickenBreastMeat  | 1x2  | 200g   | 24h   | 95         | 71        | 180          | 89          | 150           | 88           | 130          | 13          |
| Rabbit      | RabbitLegMeat      | 1x2  | 200g   | 24h   | 95         | 71        | 180          | 89          | 150           | 88           | 130          | 13          |
| Carp        | CarpFilletMeat     | 1x2  | 250g   | 12h   | 148        | 203       | 280          | 236         | 200           | 230          | 180          | 28          |
| Mackerel    | MackerelFilletMeat | 1x2  | 250g   | 12h   | 148        | 203       | 280          | 236         | 200           | 230          | 180          | 28          |
| Fat         | Lard               | 2x2  | 500g   | 48h   | 860        | 0         | 1445         | 0           | 1000          | 0            | 850          | 0           |
| Human       | HumanSteakMeat     | 1x3  | 400g   | 24h   | 165        | 42        | 300          | 48          | 225           | 45           | 160          | 7           |

## Natural Foods (Fruits, Veggies, Mushrooms)
Baking generally improves Energy slightly, while Boiling preserves the Water content best.

| Name        | Class Name       | Size | Weight | Spoil | Raw Energy | Raw Water | Baked Energy | Baked Water | Boiled Energy | Boiled Water | Dried Energy | Dried Water |
|-------------|------------------|------|--------|-------|------------|-----------|--------------|-------------|---------------|--------------|--------------|-------------|
| Apple       | Apple            | 2x2  | 150g   | 48h   | 53         | 164       | 85           | 173         | 70            | 185          | 60           | 22          |
| Pear        | Pear             | 2x2  | 170g   | 48h   | 53         | 164       | 85           | 173         | 70            | 185          | 60           | 22          |
| Plum        | Plum             | 1x1  | 70g    | 48h   | 40         | 125       | 75           | 135         | 50            | 145          | 45           | 17          |
| Pumpkin     | Pumpkin          | 3x3  | 800g   | 72h   | N/A        | N/A       | N/A          | N/A         | N/A           | N/A          | N/A          | N/A         |
| Pump. Slice | PumpkinSlice     | 2x2  | 250g   | 24h   | 100        | 200       | 180          | 150         | 150           | 250          | 120          | 30          |
| Potato      | Potato           | 2x2  | 200g   | 160h  | 40         | 60        | 150          | 40          | 100           | 80           | 120          | 10          |
| Zucchini    | Zucchini         | 1x2  | 300g   | 48h   | 25         | 223       | 55           | 232         | 40            | 244          | 35           | 33          |
| Tomato      | Tomato           | 1x1  | 50g    | 48h   | 20         | 130       | 45           | 139         | 35            | 150          | 30           | 18          |
| Grn Pepper  | GreenBellPepper  | 1x1  | 50g    | 48h   | 20         | 130       | 45           | 139         | 35            | 150          | 30           | 18          |
| Parasol     | MushroomParasol  | 1x1  | 50g    | 24h   | 50         | 50        | 110          | 30          | 80            | 70           | 70           | 5           |
| Penny Bun   | MushroomAuricula | 1x1  | 50g    | 24h   | 50         | 50        | 110          | 30          | 80            | 70           | 70           | 5           |

## Canned Food (Processed)
Values are for the "Open" can state. Opening a can with a bad tool (knife/axe) reduces the % of food inside.

| Name           | Class Name            | Size | Weight | Spoil Time | Energy (Total) | Water (Total) | Stomach |
|----------------|-----------------------|------|--------|------------|----------------|---------------|---------|
| Tactical Bacon | TacticalBaconCan_Open | 2x2  | 250g   | Never      | 1500           | 50            | 250     |
| Baked Beans    | BakedBeansCan_Open    | 2x2  | 350g   | Never      | 550            | 100           | 350     |
| Peaches        | PeachesCan_Open       | 2x2  | 350g   | Never      | 430            | 200           | 350     |
| Spaghetti      | SpaghettiCan_Open     | 2x2  | 350g   | Never      | 500            | 100           | 350     |
| Sardines       | SardinesCan_Open      | 1x2  | 130g   | Never      | 330            | 50            | 150     |
| Tuna           | TunaCan_Open          | 1x2  | 170g   | Never      | 360            | 60            | 170     |
| Dog Food       | DogFoodCan_Open       | 2x2  | 350g   | Never      | 380            | 0             | 350     |
| Cat Food       | CatFoodCan_Open       | 1x2  | 150g   | Never      | 220            | 0             | 150     |
| Unknown Food   | UnknownFoodCan_Open   | 2x2  | 300g   | Never      | 300            | 0             | 300     |
| Lunchmeat      | Lunchmeat_Open        | 1x2  | 150g   | Never      | 250            | 0             | 150     |
| Pajka          | Pajka_Open            | 1x2  | 150g   | Never      | 250            | 0             | 150     |
| Pate           | Pate_Open             | 1x2  | 150g   | Never      | 250            | 0             | 150     |
| Brisket Spread | BrisketSpread_Open    | 1x2  | 150g   | Never      | 250            | 0             | 150     |

## Dry Foods
High energy, but negative water (Dehydrating).

| Name          | Class Name   | Size | Weight | Spoil Time | Energy | Water | Stomach |
|---------------|--------------|------|--------|------------|--------|-------|---------|
| Rice          | Rice         | 2x2  | 1kg    | Never      | 3500   | -1000 | 1000    |
| Powdered Milk | PowderedMilk | 2x2  | 300g   | Never      | 1000   | -200  | 300     |
| Cereal        | CerealBox    | 1x2  | 220g   | Never      | 950    | -50   | 250     |
| Marmalade     | Marmalade    | 1x2  | 250g   | Never      | 1000   | 100   | 250     |
| Honey         | Honey        | 1x2  | 100g   | Never      | 500    | 20    | 100     |
| Salty Sticks  | SaltySticks  | 1x2  | 50g    | Never      | 200    | -20   | 50      |
| Chips         | Chips        | 1x2  | 40g    | Never      | 200    | -5    | 50      |
| Crackers      | Crackers     | 1x2  | 50g    | Never      | 250    | -10   | 50      |

## Drinks
Liquids fill the stomach very fast but digest quickly. Water values are per unit (Total Capacity varies by container).

| Name           | Class Name     | Size | Weight     | Energy (Total) | Water (Total) | Stomach |
|----------------|----------------|------|------------|----------------|---------------|---------|
| Canteen        | Canteen        | 2x2  | 1kg (Full) | 0              | 1000ml        | 1000    |
| PET Bottle     | WaterBottle    | 1x3  | 1kg (Full) | 0              | 1000ml        | 1000    |
| Glass Bottle   | Vodka (Empty)  | 1x3  | 450g       | 0              | 1000ml        | 1000    |
| Soda (Cola)    | SodaCan_Cola   | 1x2  | 340g       | 130            | 330ml         | 330     |
| Soda (Pipsi)   | SodaCan_Pipsi  | 1x2  | 340g       | 130            | 330ml         | 330     |
| Soda (Spite)   | SodaCan_Spite  | 1x2  | 340g       | 130            | 330ml         | 330     |
| Kvass          | SodaCan_Kvass  | 1x2  | 340g       | 150            | 330ml         | 330     |
| Mad Monk Kvass | SodaCan_Fronta | 1x2  | 340g       | 150            | 330ml         | 330     |
