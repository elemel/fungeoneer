# Chapter 1: Wallflower

You have entered a dungeon. You stand at the bottom of the staircase where you entered, facing east. A gnomish cartographer peers at you from an adjacent tile. As he steps onto the staircase, he thrusts a scroll into your hands. Before you can respond, he has already left the dungeon.

You unroll the scroll, identifying it as a magic map. It flickers and shifts into a symbolic representation of the dungeon:

```
###########[########[####[###############]#[###]##]#########[#################
########[[.....]###[.[....[#############]...][...]....]###[....]##############
#######[.[[.]#..]###.#..]..#############..].....]..[...]##][.#..]#############
#######]..[.....[###.#[.##.############[.....]].....[]..][...[[.[#############
########..]..[.]####.[..##.###########[...][]###].#.#][.....[....[############
##[#[[....[]...#][#]...]##<[#########[...]...]][..[....[#].#].#[##############
#[.[.[..]..#[.....[#....]].#[#########.]..]..]...[].#.[.#[]]...]##############
[..]..[..].[...[...#[...#..[.#[#####[...].......]##]#.]...[##].###############
]......[.[....]#.#.[]..]#.[....[#]#[#[].#[#.]##.[####.#.]..#[...]#############
#..[[.[..]..].#].]..[.].]....[..]........][...][####]...][.##.[]##############
#[..]...]#[]#]]#]#].....[....[..###.[....#]..]..]##]###]...[...]#]############
##[.###]#####].]#]#[.[..#[.].]..#[[....]..]].#]...].]#]##.][[]..]....][#######
#[..##]######..[]....[.]#]....]...].#[]#[.#..[...]].....]...[#[...]#.[.#######
[..]##.]####].....].#[.###]#].#[#.[][.....[....].[...].]##.][##[#.#[...[###][#
#.]#]#.#####..[##.]....[#]....[.]...].###]#.[..]..[].].......[##]...[...]#]..]
#..]....]###.[.....][...[..[....[]....#][##[]..#[....#]#[#..####[[###[]..]...[
#[...[..##[.....][][..[##.#][]#.#...[]]...]###]#[.##][...].......[[...#[...].#
##[#]]....][.#]....]..[#[....]#...].####..###][[..[][#.]....[##]..#.[...[[.[.#
####.].[#]...]#..]...[##].#.]##[#.[.####....]....[]....[].]#[###[...#.]...[#.#
###].....]]..[#[.#[].##]#]#.]####[#.]##].[#..].#...].#.#[....[##].#]].##]....#
####..]#.]..[###.[....]...]...]####..]#..]#[.].#[....[..]..##][##]###]######]#
[.....[....]####[...]...[..].]#####..[#..##]...[#[]###[..].....[##############
#[##][..]..[#####[].#[###..[.######[..]..[#...[########[....].################
####]#.]..[########]#####[.#.#######[...[#]....]########..[...]###############
###].....[################...[####[....[####[..[########[##[..[###############
######]###################[########[#]#######[]#############[]################
```

The staircase is marked `<` on the map, with east to the right. Compelled to walk through the dungeon, you always step forward when possible, turning only when instructed. Stepping onto a floor tile (marked `.`) has no additional effect.

The dungeon contains wall tiles (marked `[`, `]`, or `#`). Whenever you would step onto a wall tile, turn in place instead. This still counts as a step. For a `[` tile, turn 90 degrees to the left. For a `]` tile, turn 90 degrees to the right. For a `#` tile, turn 0 degrees, in effect halting until you catch fire.

As demonstrated by the gnome, you leave the dungeon by stepping onto the staircase from an adjacent tile. After how many steps do you leave the dungeon?


## Example

Consider a smaller dungeon:

```
#####][#####][#
[......[###[.<[
#............[#
#[##].........]
############[]#
```

Below is a log of walking through the smaller dungeon. Your coordinates are shown as `(x, y)`, and your location is marked `@` on the map.

```
Step count: 0
Coordinates: (13, 1)
Direction: East
Next symbol: [

#####][#####][#
[......[###[.@[
#............[#
#[##].........]
############[]#

---

Step count: 1
Coordinates: (13, 1)
Direction: North
Next symbol: [

#####][#####][#
[......[###[.@[
#............[#
#[##].........]
############[]#

---

Step count: 2
Coordinates: (13, 1)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.@[
#............[#
#[##].........]
############[]#

---

Step count: 3
Coordinates: (12, 1)
Direction: West
Next symbol: [

#####][#####][#
[......[###[@<[
#............[#
#[##].........]
############[]#

---

Step count: 4
Coordinates: (12, 1)
Direction: South
Next symbol: .

#####][#####][#
[......[###[@<[
#............[#
#[##].........]
############[]#

---

Step count: 5
Coordinates: (12, 2)
Direction: South
Next symbol: .

#####][#####][#
[......[###[.<[
#...........@[#
#[##].........]
############[]#

---

Step count: 6
Coordinates: (12, 3)
Direction: South
Next symbol: [

#####][#####][#
[......[###[.<[
#............[#
#[##].......@.]
############[]#

---

Step count: 7
Coordinates: (12, 3)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##].......@.]
############[]#

---

Step count: 8
Coordinates: (13, 3)
Direction: East
Next symbol: ]

#####][#####][#
[......[###[.<[
#............[#
#[##]........@]
############[]#

---

Step count: 9
Coordinates: (13, 3)
Direction: South
Next symbol: ]

#####][#####][#
[......[###[.<[
#............[#
#[##]........@]
############[]#

---

Step count: 10
Coordinates: (13, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##]........@]
############[]#

---

Step count: 11
Coordinates: (12, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##].......@.]
############[]#

---

Step count: 12
Coordinates: (11, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##]......@..]
############[]#

---

Step count: 13
Coordinates: (10, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##].....@...]
############[]#

---

Step count: 14
Coordinates: (9, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##]....@....]
############[]#

---

Step count: 15
Coordinates: (8, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##]...@.....]
############[]#

---

Step count: 16
Coordinates: (7, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##]..@......]
############[]#

---

Step count: 17
Coordinates: (6, 3)
Direction: West
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##].@.......]
############[]#

---

Step count: 18
Coordinates: (5, 3)
Direction: West
Next symbol: ]

#####][#####][#
[......[###[.<[
#............[#
#[##]@........]
############[]#

---

Step count: 19
Coordinates: (5, 3)
Direction: North
Next symbol: .

#####][#####][#
[......[###[.<[
#............[#
#[##]@........]
############[]#

---

Step count: 20
Coordinates: (5, 2)
Direction: North
Next symbol: .

#####][#####][#
[......[###[.<[
#....@.......[#
#[##].........]
############[]#

---

Step count: 21
Coordinates: (5, 1)
Direction: North
Next symbol: ]

#####][#####][#
[....@.[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 22
Coordinates: (5, 1)
Direction: East
Next symbol: .

#####][#####][#
[....@.[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 23
Coordinates: (6, 1)
Direction: East
Next symbol: [

#####][#####][#
[.....@[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 24
Coordinates: (6, 1)
Direction: North
Next symbol: [

#####][#####][#
[.....@[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 25
Coordinates: (6, 1)
Direction: West
Next symbol: .

#####][#####][#
[.....@[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 26
Coordinates: (5, 1)
Direction: West
Next symbol: .

#####][#####][#
[....@.[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 27
Coordinates: (4, 1)
Direction: West
Next symbol: .

#####][#####][#
[...@..[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 28
Coordinates: (3, 1)
Direction: West
Next symbol: .

#####][#####][#
[..@...[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 29
Coordinates: (2, 1)
Direction: West
Next symbol: .

#####][#####][#
[.@....[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 30
Coordinates: (1, 1)
Direction: West
Next symbol: [

#####][#####][#
[@.....[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 31
Coordinates: (1, 1)
Direction: South
Next symbol: .

#####][#####][#
[@.....[###[.<[
#............[#
#[##].........]
############[]#

---

Step count: 32
Coordinates: (1, 2)
Direction: South
Next symbol: [

#####][#####][#
[......[###[.<[
#@...........[#
#[##].........]
############[]#

---

Step count: 33
Coordinates: (1, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#@...........[#
#[##].........]
############[]#

---

Step count: 34
Coordinates: (2, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#.@..........[#
#[##].........]
############[]#

---

Step count: 35
Coordinates: (3, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#..@.........[#
#[##].........]
############[]#

---

Step count: 36
Coordinates: (4, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#...@........[#
#[##].........]
############[]#

---

Step count: 37
Coordinates: (5, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#....@.......[#
#[##].........]
############[]#

---

Step count: 38
Coordinates: (6, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#.....@......[#
#[##].........]
############[]#

---

Step count: 39
Coordinates: (7, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#......@.....[#
#[##].........]
############[]#

---

Step count: 40
Coordinates: (8, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#.......@....[#
#[##].........]
############[]#

---

Step count: 41
Coordinates: (9, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#........@...[#
#[##].........]
############[]#

---

Step count: 42
Coordinates: (10, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#.........@..[#
#[##].........]
############[]#

---

Step count: 43
Coordinates: (11, 2)
Direction: East
Next symbol: .

#####][#####][#
[......[###[.<[
#..........@.[#
#[##].........]
############[]#

---

Step count: 44
Coordinates: (12, 2)
Direction: East
Next symbol: [

#####][#####][#
[......[###[.<[
#...........@[#
#[##].........]
############[]#

---

Step count: 45
Coordinates: (12, 2)
Direction: North
Next symbol: .

#####][#####][#
[......[###[.<[
#...........@[#
#[##].........]
############[]#

---

Step count: 46
Coordinates: (12, 1)
Direction: North
Next symbol: ]

#####][#####][#
[......[###[@<[
#............[#
#[##].........]
############[]#

---

Step count: 47
Coordinates: (12, 1)
Direction: East
Next symbol: <

#####][#####][#
[......[###[@<[
#............[#
#[##].........]
############[]#

---

Step count: 48
Direction: East
```

You leave the smaller dungeon after 48 steps.
