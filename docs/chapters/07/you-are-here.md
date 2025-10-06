## Chapter 7: You Are Here

{% assign problem = site.data.problems.you_are_here %}

You have entered the seventh dungeon. You stand at the bottom of the staircase where you entered, facing east. In a haystack by the staircase, you find a needle: a magic pin. Out of concern for any beast of burden that may stray here to feed, you decide to keep the pin. You press it into the symbol of the staircase on your magic map.

With every move you make in the dungeon, the pin moves along on the map, reflecting your location. As register P, the pin also reveals your position as a number, starting from zero at the top-left symbol, and increasing with each symbol in left-to-right, top-to-bottom reading order.

Anchored by the pin, you consult the map:

```
{{ problem.map }}
```

This dungeon contains getters and setters for register P (marked `p` or `P`  on the map), along with altar tiles (marked `_`). Whenever you trigger a P-getter tile, get your position as a number, then push that number onto the stack. For a P-setter tile, pop a number from the stack, then set your position to that number. This teleports you to the corresponding location.

For an altar tile, pop a number `b` from the stack, then get your position as another number `a`, then push `a` onto the stack, and finally set your position to `b`. As above, this teleports you to the corresponding location.

You leave the dungeon when your position is outside the dungeon. After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/07/you-are-here.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show your position (labeled `P`).

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
