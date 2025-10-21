## Chapter 7: Rose of Eight Winds

{% assign problem = site.data.problems.rose_of_eight_winds %}

You have entered the seventh dungeon. You stand at the bottom of the staircase where you entered, facing east. A skeleton is slumped against the staircase. A glimmer on its bony fist catches your eye: a ring of revolution. You cautiously retrieve the ring, claiming it as register R.

The ring tracks your rotation in octants (increments of 45 degrees), starting at zero for east. Turning left (counter-clockwise) decreases the rotation, while turning right (clockwise) increases it. The rotation does not reset after a full revolution of eight octants, instead extending arbitrarily high or low.

After slipping the ring onto your right ring finger, you turn your attention to the map:

```
{{ problem.map }}
```

Your direction can now also be diagonal: southeast, southwest, northwest, or northeast.

This dungeon introduces wall tiles for turning diagonally: backward-left-turners (marked `{` on the map), forward-left-turners (marked `(`), forward-right-turners (marked `)`), and backward-right-turners (marked `}`).

As before, wall tiles block you from moving forward to them, but you still trigger their effect. For a backward-left-turner tile, turn 135 degrees to the left. For a forward-left-turner tile, turn 45 degrees to the left. For a forward-right-turner tile, turn 45 degrees to the right. For a backward-right-turner tile, turn 135 degrees to the right.

This dungeon also introduces tiles with getters and setters for register R (marked `r` or `R`). For an R-getter tile, read the number from register R, then push that number onto the stack. For an R-setter tile, pop a number from the stack, then write that number to register R. This changes your direction to align with the new rotation.

After how many ticks do you leave the dungeon?

From here, you can [continue to the answer](../../answers/chapters/07/rose-of-eight-winds.md).


### Example

Consider an example dungeon:

```
{{ problem.example_map }}
```

The log below shows you exploring the example dungeon, with your location marked `@` on the map. The status lines now also show your rotation as register R (labeled `R`).

```
{{ problem.example_log }}
```

You leave the example dungeon after {{ problem.example_answer }} ticks.
