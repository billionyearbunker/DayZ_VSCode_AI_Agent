DayZ AI Territories: territories.xml Architecture
1. File Overview & Scope
Path: /mpmissions/dayzOffline.chernarusplus/env/territories.xml

Role: The "Spatial Constraints" manager for dynamic AI (specifically Animals and potentially dynamic Infected herds).

Function: Defines the geometric boundaries (Circles) where specific AI species are allowed to spawn and roam.

Relationship: It acts as the geographic filter for events.xml.

events.xml: "Spawn a Wolf Pack."

territories.xml: "Here are the 50 circles on the map where Wolf Packs are allowed to exist."

2. Core Structure
The file is divided into <territory> blocks, each corresponding to a specific AI "Type" defined in events.xml.

<territories>
    <territory type="HerdDeer">
        <zone name="Deer_1" s="1" dmin="1" dmax="3" x="4500.0" z="8000.0" r="200" />
        <zone name="Deer_2" s="1" dmin="1" dmax="3" x="6200.0" z="9100.0" r="200" />
    </territory>
    
    <territory type="Bear">
        <zone name="Bear_Tisy" s="1" dmin="0" dmax="1" x="1200.0" z="14000.0" r="500" />
    </territory>
</territories>

3. Element Definition: <zone>
Each <zone> tag represents a single valid spawn circle on the map.

Attributes
name: (String) Internal label. Useful for debugging but does not affect logic.

s (Selection Weight):

Integer: Determines the probability of this zone being chosen relative to others.

Usage: If Zone A has s="1" and Zone B has s="2", Zone B is twice as likely to be picked by the event manager.

dmin / dmax (Dynamic Min/Max):

Technically: Intended to control density within the zone.

Reality: In modern DayZ versions, the Quantity of animals is primarily driven by the <child> elements in events.xml. These tags in territories.xml are often legacy or secondary limiters.

x / z:

Floats: The center point of the territory circle (Map Coordinates).

r (Radius):

Float: The radius (in meters) around the center point.

Behavior: The AI will spawn randomly somewhere inside this circle. It defines their "Home" range.

4. The "Leash" Logic (Roaming Behavior)
The territories.xml file defines more than just spawn points; it defines AI behavior limits.

Spawn: The event triggers. The engine picks a <zone> from territories.xml. It spawns the animals inside that circle.

Roam: The animals wander randomly.

The Hard Boundary: Animals generally attempt to stay within or near their defined radius (r).

Aggression vs. Territory:

If a Wolf chases a player, it can leave the territory radius.

However, once the player escapes or dies, the AI's "Return to Territory" logic triggers. They will travel back to their defined circle or eventually despawn if too far out.

5. Event Mapping (territory type="...")
The type attribute in the <territory> tag serves as the link key.

Linkage:

In events.xml: <event name="AnimalWolf">

In territories.xml: <territory type="AnimalWolf">

Inheritance:

You can have multiple different events share the same territory.

Example: Both AnimalRoeDeer and AnimalRedDeer could theoretically point to a territory named HerdDeer if configured that way in the event configs (though vanilla usually separates them).

6. Specific Use Cases
A. Predators (Wolves/Bears)
Radius: Usually Large (e.g., r="300" or r="500").

Location: Deep woods, far from towns.

Logic: High radius makes them harder to predict. You might hear them before you see them because they patrol a massive area.

B. Prey (Sheep/Cows/Goats)
Radius: Often smaller or centered on farms.

Location: Open fields, near barns.

C. Domesticated (Pigs/Hens)
Oddity: Often spawned via cfgeventspawns.xml (exact points) rather than territories.xml (zones), or they use very small territory radii (r="50") near village centers.

7. Operational Oddities & Troubleshooting
"The Empty Woods":

If you increase <nominal> in events.xml (e.g., 50 Bear spawns) but you only have 2 <zone> entries in territories.xml, the server can only spawn 2 Bears.

Rule: Available Zones > Nominal Count. You must have enough territory circles to accommodate the requested number of events.

Overlap:

Territories can overlap. A Bear zone can sit on top of a Wolf zone.

Result: "Zone Wars" where AI fight each other (if factions are set hostile).

Debugging:

Use the admin tool "ESP" or "Show Zones" to visualize these circles in-game. They appear as giant wireframe cylinders.

Validation:

Ensure coordinates (x, z) are valid map positions. A zone centered on 0,0 (Debug Ocean) will result in animals spawning underwater and drowning immediately.

8. Modding Implications
Custom Maps: When porting a server to a new map (e.g., Deer Isle), you must replace territories.xml.

Risk: Using Chernarus territories on Namalsk will result in animals spawning in the void (out of bounds) or not spawning at all, as the coordinate systems do not match.

Expansion/AI Mods: Mods that add AI bandits or custom monsters often require you to add new <territory type="MyCustomMonster"> blocks to this file to define where they live.