## Chapter 3: Turning the Scales

{% assign problem = site.data.problems.turning_the_scales %}

You have entered the third dungeon. You stand at the bottom of the staircase where you entered, facing east. On the bottom stair, you spot a purse of stacking, clearly left behind by accident. You grab it for safekeeping.

Though empty for the time being, the purse has plenty of room for a tall stack of numbers. Adding a number to the top is called pushing, while removing the number at the top is called popping. Popping an empty stack raises an error.

After securing the purse to your belt, you consult the map:

<pre><code>{{ problem.map | safe }}</code></pre>

This dungeon introduces tiles with digits (marked `0` through `9` on the map) and junctions (marked `=`). When you trigger a digit tile, push the corresponding number onto the stack. This is called taking. Taking a number only affects the stack, while leaving the tile unchanged.

For a junction tile, pop two numbers from the stack: first `a`, then `b`. If `b` is less than `a`, turn 90 degrees to the left. If `b` is greater than `a`, turn 90 degrees to the right. If the numbers are equal, continue straight.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/03/turning-the-scales.md).


### Example

Consider an example dungeon:

<pre><code>{{ problem.example_map | safe }}</code></pre>

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status line now also shows the stack (labeled `St`). The stack is displayed as a list of numbers, with the top of the stack on the right. An empty stack appears as `[]`. For large stacks, only the numbers at the top are shown.

<pre><code>{{ problem.example_log | safe }}</code></pre>

You leave the example dungeon after {{ problem.example_answer }} ticks.
