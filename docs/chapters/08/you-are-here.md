## Chapter 8: You Are Here

{% assign problem = site.data.problems.you_are_here %}

You have entered the eighth dungeon. You stand at the bottom of the staircase where you entered, facing east. In a haystack by the staircase, you find a needle: a magic pin. Out of concern for any beast of burden that may stray here to feed, you decide to keep the pin. You press it into the symbol of the staircase on your magic map.

As you move through the dungeon, the pin moves along on the map, tracking your position as register P. Positions start at zero for the top-left symbol, then increase with each symbol in left-to-right, top-to-bottom reading order.

Anchored by the pin, you consult the map:

```
{{ problem.map }}
```

This dungeon introduces getters and setters for register P (marked `p` or `P`  on the map). When you trigger a P-getter tile, read the number from register P, then push that number onto the stack. For a P-setter tile, pop a number from the stack, then write that number to register P. This teleports you to the corresponding location.

A minor change in position can translate to a major change in coordinates. While this is permitted for staircase and teleportation effects, including P-setter tiles, it is forbidden for regular moves. Moving across the edge of a dungeon level raises an error for invalid coordinates. This rule applies both to the forward move at the start of a tick and to moves caused by triggered effects.

You leave the dungeon when your position is outside the dungeon. After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/08/you-are-here.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show your position as register P (labeled `P`).

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
