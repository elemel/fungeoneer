## Chapter 9: A Grain of Truth

{% assign problem = site.data.problems.a_grain_of_truth %}

You have entered the ninth dungeon. You stand at the bottom of the staircase where you entered, facing east. You consult the map:

```
{{ problem.map -}}
```

This dungeon contains tiles with bitwise operators: inverters (marked `~` on the map), and-gates (marked `&`), or-gates (marked `|`), exclusive-or-gates (marked `^`), and shifters (marked `\`). Inverters are unary, while the other bitwise operators are binary.

The binary bitwise operators handle arguments and results in the same way as the arithmetic operators (`+`, `-`, `*`, `/`, and `%`). Inverters are also similar, but pop only one argument from the stack.

The bitwise operators reinterpret their arguments as unsigned 32-bit integers after popping them from the stack. Then they apply the corresponding operations to the arguments. Finally, each operator reinterprets the result as a signed 32-bit integer before pushing it onto the stack.

Inverters, and-gates, or-gates, and exclusive-or-gates have their usual meanings. Shifters move the bits of `a` to the left by `b % 32` bit positions. The shift is circular: bits that disappear on one side reappear on the other.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/09/a-grain-of-truth.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map -}}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map.

```
{{ problem.example_log -}}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
