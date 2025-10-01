## Chapter 2: As Above, So Below

{% assign problem = site.data.problems.as_above_so_below %}

You have entered another dungeon. You stand at the bottom of the staircase where you entered, facing east. In this dungeon, there are two levels, separated by a blank line on the map:

```
{{ problem.map }}
```

The top level is shown at the top of the map, and the bottom level at the bottom. A dungeon with two or more levels is considered deep, while a shallow dungeon only has a single level.

There are many staircase tiles in this dungeon: staircases down (marked `>` on the map) and staircases up (marked `<`). Whenever you trigger a staircase-down tile, move down to the next lower level, increasing your z-coordinate by one. For a staircase-up tile, move up to the next higher level, decreasing your z-coordinate by one. The vertical move happens during the same tick, without triggering any additional tile.

As before, you leave the dungeon by triggering the staircase tile where you entered, which is the only staircase-up tile on the top level. After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/02/as-above-so-below.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map.

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
