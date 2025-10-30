## Chapter 10: A Grain of Truth

{% assign problem = site.data.problems.a_grain_of_truth %}

You have entered the tenth dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

<pre><code>{{ problem.map | safe }}</code></pre>

This dungeon introduces tiles with bitwise operators: inverters (marked `~` on the map), and-gates (marked `&`), or-gates (marked `|`), exclusive-or-gates (marked `^`), and shifters (marked `#`).

When you trigger an inverter tile, apply bitwise inversion to the number at the top of the stack.

For the other bitwise operator tiles, pop two numbers from the stack: first `a`, then `b`. Apply the operator with `b` as the left operand and `a` as the right. Push the result onto the stack.

And-gates, or-gates, and exclusive-or-gates perform bitwise-and, bitwise-or, and bitwise-exclusive-or, respectively.

Shifters perform bit shifting, moving the bits of `b` to the left by `a` bit positions, or to the right if `a` is negative. Right shifts are arithmetic, preserving the sign of `b`.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/10/a-grain-of-truth.md).


### Example

Consider an example dungeon:

<pre><code>{{ problem.example_map | safe }}</code></pre>

The log below shows you exploring the example dungeon, with your location marked `@` on the map.

<pre><code>{{ problem.example_log | safe }}</code></pre>

You leave the example dungeon after {{ problem.example_answer }} ticks.
