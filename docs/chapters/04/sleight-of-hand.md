## Chapter 4: Sleight of Hand

{% assign problem = site.data.problems.sleight_of_hand %}

You have entered the fourth dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

<pre><code>{{ problem.map | safe }}</code></pre>

This dungeon introduces tiles with stack operations: duplicators (marked `:`), swappers (marked `\`), and altars (marked `_`). When you trigger a duplicator tile, duplicate the number at the top of the stack. For a swapper tile, swap the two numbers at the top of the stack. For an altar tile, pop and discard a number from the stack. This is called dropping. Dropping a number only affects the stack, while leaving the tile unchanged.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/04/sleight-of-hand.md).


### Example

Consider an example dungeon:

<pre><code>{{ problem.example_map | safe }}</code></pre>

The log below shows you exploring the example dungeon, with your location marked `@` on the map.

<pre><code>{{ problem.example_log | safe }}</code></pre>

You leave the example dungeon after {{ problem.example_answer }} ticks.
