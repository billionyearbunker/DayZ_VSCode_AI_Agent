# DayZ Custom Animal Stats

## Important Notes on Data
- The "HP" column refers to the approximate damage needed to kill them (e.g., a .308 round deals ~110 damage, so you can gauge one-shot potential).
- Name: The common display name of the animal as referred to by players.
- Class Name: The internal variable name used in the game code to spawn the entity.
- Size: The physical scale of the animal in the game world, or the inventory grid dimensions required to carry it if it is small enough to be picked up.
- Wgt: The mass of the animal in kilograms or grams, which affects carrying capacity if the animal is placed in the player's inventory.
- Location: The specific environmental biomes or map zones where this animal naturally spawns.
- Edible?: Indicates whether the meat harvested from this animal is safe to consume or carries specific disease risks (like Kuru).
- Steaks: The approximate quantity of meat items yielded when the animal is skinned and quartered with a knife.
- HP: The total hit points or damage required to kill the animal.
- Pack?: Describes the social behavior of the animal, specifying if it roams alone or spawns in groups.
- Aggr?: Short for "Aggression," indicating whether the animal is a predator that attacks players or prey that flees upon detection.
- Harvest Drops: A list of materials obtained when skinning the animal, such as pelts, bones, fat, and guts.
- Description: A summary of the animal's appearance and behavior to help identify it in the wild.

## Predators (Aggressive)
These animals will actively hunt the player. They often run in packs and require high-caliber weapons to take down safely.

| Name          | Class Name             | Size    | Wgt   | Location         | Edible? | Steaks | HP   | Pack?     | Aggr? | Harvest Drops              | Description                                                  |
|---------------|------------------------|---------|-------|------------------|---------|--------|------|-----------|-------|----------------------------|--------------------------------------------------------------|
| Bear          | Animal_UrsusArctos     | Massive | 400kg | Deep Forest      | Safe    | 10-14  | 800  | Solo      | Yes   | Bear Pelt, Bone, Fat, Guts | Highly dangerous apex predator. Extremely high health.       |
| Wolf          | Animal_CanisLupus_Grey | Medium  | 40kg  | Forest/High Tier | Safe    | 3-5    | 150  | Yes (3-8) | Yes   | Wolf Pelt, Bone, Fat, Guts | Fast pack hunters. Their howling signals an attack.          |
| Infected Wolf | ZmbM_Wolf_Heavy        | Medium  | 40kg  | Dynamic Events   | No      | 0      | 150  | Yes       | Yes   | None (Infected)            | Decayed wolf. Very rare dynamic event spawn.                 |
| Polar Bear    | Animal_UrsusMaritimus  | Massive | 500kg | Sakhal/Namalsk   | Safe    | 12-16  | 1200 | Solo      | Yes   | Bear Pelt, Bone, Fat, Guts | Rare, tougher variant of the brown bear found in snowy maps. |

## Livestock & Wild Game (Passive)
Primary food sources. They will flee if they hear gunshots or see players.

| Name            | Class Name            | Size  | Wgt   | Location         | Edible? | Steaks | HP  | Pack?    | Aggr?  | Harvest Drops                       | Description                                                 |
|-----------------|-----------------------|-------|-------|------------------|---------|--------|-----|----------|--------|-------------------------------------|-------------------------------------------------------------|
| Cow (Bull)      | Animal_BosTaurus_F    | Large | 1000kg | Farm, Fields     | Safe    | 10-15  | 300 | Herd     | No     | Cow Pelt, Bone, Fat, Guts           | Large domesticated cattle. Slow moving.                     |
| Red Deer (Stag) | Animal_CervusElaphus  | Large | 200kg | Forest, Clearing | Safe    | 6-8    | 200 | Herd     | Charge | Deer Pelt, Bone, Fat, Guts, Antlers | Large male deer. Can charge if cornered, but usually flees. |
| Red Deer (Doe)  | Animal_CervusElaphusF | Med   | 120kg | Forest, Clearing | Safe    | 4-6    | 150 | Herd     | No     | Deer Pelt, Bone, Fat, Guts          | Female deer. Skittish and fast.                             |
| Roe Deer        | Animal_Capreolus      | Med   | 40kg  | Forest Edge      | Safe    | 3-5    | 80  | Solo/Duo | No     | Deer Pelt, Bone, Fat, Guts          | Smaller deer species. Very fast.                            |
| Wild Boar       | Animal_SusScrofa      | Med   | 80kg  | Forest           | Safe    | 4-6    | 150 | Herd     | Charge | Pig Pelt, Bone, Fat, Guts, Tusks    | Wild pig. Will charge players if startled closerange.       |
| Pig (Farm)      | Animal_SusDomesticus  | Med   | 100kg | Farm, Town       | Safe    | 6-8    | 120 | Herd     | No     | Pig Pelt, Bone, Fat, Guts           | Domesticated pig. Slower than wild boars.                   |
| Sheep           | Animal_OvisAries      | Med   | 60kg  | Farm, High Grnd  | Safe    | 4-6    | 80  | Herd     | No     | Sheep Pelt, Bone, Fat, Guts         | Domestic sheep. Often found in open fields.                 |
| Goat            | Animal_CapraHircus    | Med   | 50kg  | Farm, Rocky      | Safe    | 3-5    | 80  | Herd     | Charge | Goat Pelt, Bone, Fat, Guts          | Domestic goat. Can headbutt if threatened.                  |
| Chicken         | Animal_GallusGallus   | Tiny  | 2kg   | Towns, Villages  | Safe    | 1-2    | 5   | Solo     | No     | Feathers, Bones                     | Small bird. Can be caught by hand if quick.                 |
| Rabbit          | Animal_LepusEuropaeus | Tiny  | 2kg   | Fields (Snare)   | Safe    | 1      | 5   | Solo     | No     | Rabbit Leg, Pelt, Bones             | Rare. Usually only caught via Snare Traps.                  |
| Fox             | Animal_VulpesVulpes   | Small | 8kg   | Forest           | Safe    | 2      | 30  | Solo     | No     | Fox Pelt, Bones                     | Elusive scavenger. Distinctive scream at night.             |

## Fish (Fishing)
Can only be obtained using a Fishing Rod or Fish Trap.

| Name        | Class Name  | Size | Wgt  | Location    | Edible? | Steaks        | HP  | Pack? | Aggr? | Harvest Drops | Description                                         |
|-------------|-------------|------|------|-------------|---------|---------------|-----|-------|-------|---------------|-----------------------------------------------------|
| Carp        | Carp        | 1x2  | 1kg  | Fresh Water | Safe    | 2 Fillets     | N/A | N/A   | No    | Guts          | Common freshwater fish (Ponds/Lakes).               |
| Mackerel    | Mackerel    | 1x2  | 1kg  | Salt Water  | Safe    | 2 Fillets     | N/A | N/A   | No    | Guts          | Common ocean fish. Found on the coast.              |
| Sardines    | Sardines    | 1x1  | 200g | Salt Water  | Safe    | 0 (Eat Whole) | N/A | N/A   | No    | None          | Tiny fish. Caught in bottle traps or shore fishing. |
| Bitterlings | Bitterlings | 1x1  | 100g | Fresh Water | Safe    | 0 (Eat Whole) | N/A | N/A   | No    | None          | Tiny bait fish. Caught in bottle traps.             |
