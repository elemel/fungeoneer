## Chapter 11: Geomancer

{% assign problem = site.data.problems.geomancer %}

You have entered the last dungeon. You stand at the bottom of the staircase where you entered, facing east. On the bottom stair, you spot an empty flask and a magic marker. You pause for a moment, then sit down on the staircase, taking the marker. You consult the map:

```
{{ problem.map }}
```

This dungeon contains reader tiles (marked `?` on the map) and writer tiles (marked `!`).

Whenever you trigger a reader tile, pop a number `a` from the stack. Find the tile at position `a`, then get the extended ASCII code of that tile as another number `b`. Finally, push `b` onto the stack.

Whenever you trigger a writer tile, pop two numbers from the stack: first `b`, then `a`. Find the tile at position `a`, then set the extended ASCII code of that tile to `b % 256`.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/11/geomancer.md).

## Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map.

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
