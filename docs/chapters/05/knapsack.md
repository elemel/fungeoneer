## Chapter 5: Knapsack

{% assign problem = site.data.problems.knapsack %}

You have entered the fifth dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

```
{{ problem.map }}
```

This dungeon introduces tiles with getters (marked by lowercase letters on the map) and setters (marked by uppercase letters). These tiles operate on your inventory slots, also known as registers. Each register contains a number, all initially zero. Register names are case-insensitive: both `a` and `A` refer to register A. Registers P, R, and S are missing from the map.

Whenever you trigger a getter tile, get the number from the corresponding register, then push that number onto the stack. For a setter tile, pop a number from the stack, then set the corresponding register to that number.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/05/knapsack.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show the most recently used registers.

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
