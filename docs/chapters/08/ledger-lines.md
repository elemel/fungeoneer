## Chapter 8: Ledger Lines

{% assign problem = site.data.problems.ledger_lines %}

You have entered the eighth dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnome sits on the bottom stair, sipping from a flask of mushroom brew. As he looks up at you, then down at the purse of stacking on your belt, you recognize him as the cartographer from the first dungeon. He leans forward, as if about to speak. With a magic marker and a flick of the wrist, he scribbles a line of credit onto your purse, in the shape of register S. He pauses for a moment, then sits back, taking another sip.

Register S serves as both stack size and stack pointer, always pointing to the slot just above the top of the stack. It initially points to slot 0, indicating an empty stack. Pushing writes a number to slot S, then increments S. Popping decrements S, then reads a number from slot S.

The stack is invalid if the stack size goes below 0, which is called stack underflow, or above the stack limit, called stack overflow.

You consult the map:

```
{{ problem.map }}
```

This dungeon contains tiles with getters and setters for register S (marked `s` or `S`  on the map), along with peekers (marked `,`) and pokers (marked `;`). Whenever you trigger an S-getter tile, get the stack size as a number, then push that number onto the stack. For an S-setter tile, pop a number from the stack, then set the stack size to that number.

Peekers and pokers treat the stack and inventory as a unified sequence of slots. Slots with index zero or higher refer to the stack. Slots with a negative index refer to the inventory. Registers A through Z are mapped to slot index -1 through -26, respectively.

For a peeker tile, pop an argument `a` from the stack. Then get another number `b` from slot `a`. Finally, push `b` onto the stack. For a poker tile, pop two arguments from the stack: first `b`, then `a`. Set the number in slot `a` to `b`.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/08/ledger-lines.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show the stack size (labeled `S`).

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
