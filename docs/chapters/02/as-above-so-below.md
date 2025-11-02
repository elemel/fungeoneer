## Chapter 2: As Above, So Below

{% assign problem = site.data.problems.as_above_so_below %}

You have entered another dungeon. You stand at the bottom of the staircase where you entered, facing east. In this dungeon, there are two levels, separated by a blank line on the map:

<pre><code>{{ problem.map | safe }}</code></pre>

The top level is shown at the top of the map, and the bottom level at the bottom.

There are many staircase tiles in this dungeon: down-staircases (marked `>` on the map) and up-staircases (marked `<`). When you trigger a down-staircase tile, move down to the next lower level. For an up-staircase tile, move up to the next higher level. This additional move happens immediately, without triggering another tile.

Staircase tiles illustrate a general rule: you can only trigger one tile per tick. If triggering a tile causes you to move again during the same tick, that move does not trigger another tile.

As before, you leave the dungeon by triggering the staircase tile where you entered. It is the only up-staircase tile on the top level. After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/02/as-above-so-below.md).


### Example

Consider an example dungeon:

<pre><code>{{ problem.example_map | safe }}</code></pre>

The log below shows you exploring the example dungeon, with your location marked `@` on the map. In dungeons with multiple levels, coordinates are written as `(x, y, z)`, where `z` increases downward with each level. The origin is still at the first tile on the map, in the northwest corner of the top level.

<pre><code>{{ problem.example_log | safe }}</code></pre>

You leave the example dungeon after {{ problem.example_answer }} ticks.
