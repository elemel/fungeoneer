## Chapter 4: The Art of Reckoning

{% assign problem = site.data.problems.the_art_of_reckoning %}

You have entered the fourth dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

```
{{ problem.map }}
```

This dungeon introduces tiles with arithmetic operators: adders (marked `+` on the map), subtractors (marked `-`), multipliers (marked `*`), dividers (marked `/`), and modulators (marked `%`).

Whenever you trigger an operator tile, pop two numbers from the stack: first `a`, then `b`. Apply the operator with `b` as the left operand and `a` as the right, then push the result onto the stack.

Adders, subtractors, and multipliers perform addition, subtraction, and multiplication, respectively. Dividers perform floor division, rounding down toward negative infinity.

Modulators perform the modulo operation: `c = b % a`, where the result `c` has the same sign as the divisor `a`. Alternatively, the modulo operation can be expressed using floor division: `c = b - (b / a) * a`.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/04/the-art-of-reckoning.md).


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
