## Chapter 9: Ledger Lines

{% assign problem = site.data.problems.ledger_lines %}

You have entered the ninth dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnome sits on the bottom stair, sipping from a flask of mushroom brew. As he looks up at you, then down at the purse of stacking on your belt, you recognize him as the cartographer from the first dungeon. He leans forward, as if about to speak. With a magic marker and a flick of the wrist, he scribbles a line of credit onto your purse, in the shape of an S. He pauses for a moment, then sits back, taking another sip.

The purse of stacking now tracks the stack size as register S. The stack size is initially zero, indicating an empty stack. Stack slots are indexed from zero. Pushing writes a number to slot S, then increments register S. Popping decrements register S, then reads a number from slot S.

A stack size below zero causes stack underflow, while one above the stack limit causes stack overflow.

With your affairs in order, you consult the map:

```
{{ problem.map }}
```

This dungeon introduces tiles with getters and setters for register S (marked `s` or `S`  on the map), along with peekers (marked `,`) and pokers (marked `;`). When you trigger an S-getter tile, push register S onto the stack. For an S-setter tile, pop register S from the stack. This resizes the stack.

For a peeker tile, pop a number `a` from the stack. Read another number `b` from slot `a`. Push `b` onto the stack. For a poker tile, pop two numbers from the stack: first `a`, then `b`. Write `b` to slot `a`.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/09/ledger-lines.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show the stack size as register S (labeled `S`).

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
