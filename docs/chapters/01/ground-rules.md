## Chapter 1: Ground Rules

{% assign problem = site.data.problems.ground_rules %}

You have entered a dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnomish cartographer, carrying a bundle of scrolls, peers at you from nearby. As he moves to the staircase, he thrusts a scroll into your hands. Before you can respond, he has already left the dungeon.

Unrolling the scroll, you identify it as a magic map. It ripples and shifts into a symbolic representation of the dungeon:

```
{{ problem.map }}
```

The dungeon is arranged as a grid of tiles. The directions on the map are right for east, down for south, left for west, and up for north. The staircase tile is marked `<` on the map.

You discover a contraption that was rolled into the map: an amulet of timekeeping. You sling it around your neck, resting close to your heart. With every tick of the clockwork, you are compelled to move forward to the next tile and trigger its effect. Triggering a lit or unlit floor tile (marked `.` or <code>&nbsp;</code>) has no effect. All floor tiles in this dungeon are lit.

Besides the staircase and floor tiles, the dungeon also contains wall tiles of different kinds: left-turners (marked `[`), right-turners (marked `]`), and halters (marked `#`). Wall tiles block you from moving forward to them, but you still trigger them from the adjacent tile. For a left-turner tile, turn 90 degrees to the left. For a right-turner tile, turn 90 degrees to the right. For a halter tile, do not turn at all, effectively halting forever.

As demonstrated by the gnome, you leave the dungeon by triggering the staircase tile. After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/01/ground-rules.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status line uses the labels `Dx` for direction, `Co` for coordinates, and `Tk` for ticks. Coordinates are shown as `(x, y, z)`, where `x` increases to the east, `y` to the south, and `z` downward. The origin is at the northwest corner of the map.

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
