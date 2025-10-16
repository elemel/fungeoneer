## Chapter 11: Behind the Curtain

{% assign problem = site.data.problems.behind_the_curtain %}

You have entered the eleventh dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

```
{{ problem.map }}
```

This dungeon introduces tiles with stashes (marked `'` on the map), passages (marked `"`), and mimics (marked `$`). These tiles operate on other map tiles, revealing their symbols as numbers. Tiles can store any number, but only some numbers correspond to valid symbols. Conversions between symbols and numbers use the ASCII table.

When you trigger a stash tile, move forward to the next tile. Read a number from it, then push that number onto the stack. All of this happens within the same tick, without triggering another tile. Stash tiles allow you to stand on any tile, including wall tiles.

For a passage tile, move forward until you reach another passage tile. For each tile you pass between the passage tiles, read a number from that tile, then push that number onto the stack. All of this happens within the same tick, without triggering another tile. Passage tiles allow you to pass through any tile, including wall tiles.

For a mimic tile, pop a number from the stack. Act as if you instead triggered a tile with that number. If the imitated tile is a wall tile, move backward to the tile before the mimic tile, then turn as specified by the imitated wall tile. All of this happens within the same tick.

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
