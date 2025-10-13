## Chapter 11: Behind the Curtain

{% assign problem = site.data.problems.behind_the_curtain %}

You have entered the eleventh dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

```
{{ problem.map }}
```

This dungeon introduces tiles with stashes (marked `'` on the map), passages (marked `"`), and mimics (marked `$`).

When you trigger a stash tile, move forward to the next tile immediately, without triggering that tile. Push the extended ASCII code (0 through 255) of that tile onto the stack. All of this happens within the same tick, and lets you stand on any tile, including wall tiles.

For a passage tile, find the next passage tile in your facing direction. Push your position onto the stack, then move to the other passage tile, and finally push your position onto the stack again. All of this happens within the same tick, and lets you pass through any tile, including wall tiles.

For a mimic tile, pop a number from the stack. Act as if you triggered a symbol with that number as extended ASCII code. If the imitated symbol is a wall symbol, move backward to the tile before the mimic tile, then turn as specified by the wall symbol. All of this happens within the same tick.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/11/behind-the-curtain.md).


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
