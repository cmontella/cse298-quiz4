# CSE 298 - Quiz 4

Due: 8/04 by end of day

Make at least 1 commit per question.

## Question 1

What is the difference between Dijkstra's Algorithm and A*. Why would one use Dijkstra's over A* and vice versa?

## Question 2

Consider the following robot in a grid 2D grid world:

![Gridworld](https://github.com/cmontella/cse298-quiz4/blob/master/gridworld.png?raw=true)

The cell (0,0) is at the bottom left. The robot starts at cell (3,3) and is facing in the 0 radians direction. The robot's goal cell is (12,1), facing the 0 radians direction as well.

Perform the A* algorithm by hand to find the shortest path from the robot's starting location to the goal. Write down each step of the algorithm, including the current cell, open set of cells O, the closed set of cells C, the parent of each cell, and the current g-score and f-scores for each cell (these can be a sparse lists i.e. you don't need to write the scores/parents of the cells haven't been considered by the algorithm yet). You can use any heuristic you like, but specify the one you are using.

```
Initial robot: (3,3)
Goal node: (12,1)
Heuristic function: Euclidean distance

Init:
n_c: (3,3)
O: {(3,3)}
C: {}
Parents:
  Empty
G-scores:
	(3,3): 0
F-scores:
	(3,3): 0

Step 1
n_c: (3,3)
O: {(4,3), (3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2)}
C: {(3,3)}
Parents:
	(4,3): (3,3)
	(3,4): (3,3)
	(2,3): (3,3)
	(3,2): (3,3)
	(4,2): (3,3)
	(4,4): (3,3)
	(2,4): (3,3)
	(2,2): (3,3)
G-score:
	(4,3): 1
	(3,4): 1
	(2,3): 1
	(3,2): 1
	(4,2): sqrt(2)
	(4,4): sqrt(2)
	(2,4): sqrt(2)
	(2,2): sqrt(2)
F-score:
->(4,3): 9.25
	(3,4): 10.49
	(2,3): 11.20
	(3,2): 10.06
	(4,2): 9.47
	(4,4): 9.95
	(2,4): 11.85
	(2,2): 11.46

Step 2
n_c: (4,3)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,3), (5,4)}
C: {(3,3), (4,3)}
Parents:
	(5,2): (4,3)
	(5,3): (4,3)
	(5,4): (4,3)
G-score:
	(5,3): 2
	(4,4): 2
	(3,3): 2
	(4,2): 2
	(5,4): 2.41
	(5,2): 2.41
	(3,2): 2.41
	(3,4): 2.41
F-score:
->(5,3): 9.28
	(4,4): 10.54
	(3,3): 11.22
	(4,2): 10.06
	(5,4): 10.03
	(5,2): 9.48
	(3,2): 11.47
	(3,4): 11.9

Step 3
n_c: (5,3)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,3), (6,4)}
C: {(3,3), (4,3), (5,3)}
Parents:
	(6,2): (5,3)
	(6,3): (5,3)
	(6,4): (5,3)
G-score:
	(5,4): 3
	(5,2): 3
	(6,3): 3
	(4,3): 3
	(6,4): 3.41
	(6,2): 3.41
	(4,2): 3.41
	(4,4): 3.41
F-score:
	(5,4): 10.62
	(5,2): 10.07
->(6,3): 9.32
	(4,3): 11.25
	(6,4): 10.12
	(6,2): 9.49
	(4,2): 11.47
	(4,4): 11.95

Step 4
n_c: (6,3)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,4), (7,2), (7,3), (7,4)}
C: {(3,3), (4,3), (5,3), (6,3)}
Parents:
	(7,2): (6,3)
	(7,3): (6,3)
	(7,4): (6,3)
G-score:
	(6,4): 4
	(6,2): 4
	(7,3): 4
	(5,3): 4
	(7,4): 4.41
	(7,2): 4.41
	(5,2): 4.41
	(5,4): 4.41
F-score:
	(6,4): 10.71
	(6,2): 10.08
->(7,3): 9.39
	(5,3): 11.28
	(7,4): 10.24
	(7,2): 9.51
	(5,2): 11.48
	(5,4): 12.03

Step 5
n_c: (7,3)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,4), (7,2), (7,4), (8,2), (8,3), (8,4)}
C: {(3,3), (4,3), (5,3), (6,3), (7,3)}
Parents:
	(8,2): (7,3)
	(8,3): (7,3)
	(8,4): (7,3)
G-score:
	(7,4): 5
	(7,2): 5
	(8,3): 5
	(6,3): 5
	(8,4): 5.41
	(8,2): 5.41
	(6,2): 5.41
	(6,4): 5.41
F-score:
	(7,4): 10.83
	(7,2): 10.10
->(8,3): 9.47
	(6,3): 11.32
	(8,4): 10.41
	(8,2): 9.53
	(6,2): 11.49
	(6,4): 12.12

Step 6
n_c: (8,3)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,4), (7,2), (7,4), (8,2), (8,4), (9,2), (9,3), (9,4)}
C: {(3,3), (4,3), (5,3), (6,3), (7,3), (8,3)}
Parents:
	(9,2): (8,3)
	(9,3): (8,3)
	(9,4): (8,3)
G-score:
	(8,4): 6
	(8,2): 6
	(9,3): 6
	(7,3): 6
	(9,4): 6.41
	(9,2): 6.41
	(7,2): 6.41
	(7,4): 6.41
F-score:
	(8,4): 11.00
	(8,2): 10.12
	(9,3): 9.61
	(7,3): 11.39
	(9,4): 10.65
->(9,2): 9.57
	(7,2): 11.51
	(7,4): 12.24

Step 7
n_c: (9,2)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,4), (7,2), (7,4), (8,2), (8,4), (9,3), (9,4) (8,1), (9,1), (10,1), (10,2), (10,3)}
C: {(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,2)}
Parents:
	(8,1): (9,2)
	(9,1): (9,2)
	(10,1): (9,2)
	(10,2): (9,2)
	(10,3): (9,2)
G-score:
	(9,3): 6.42
	(9,1): 6.42
	(8,2): 6.42
	(10,2): 6.42
	(10,3): 7.82
	(10,1): 7.82
	(8,3): 7.82
	(8,1): 7.82
F-score:
	(9,3): 11.02
	(9,1): 11.41
	(8,2): 11.53
->(10,2): 9.65
	(10,3): 10.65
	(10,1): 9.98
	(8,3): 12.29
	(8,1): 11.82

Step 8
n_c: (10,2)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,4), (7,2), (7,4), (8,2), (8,4), (9,3), (9,4) (8,1), (9,1), (10,1), (10,3), (11,1), (11,2), (11,3)}
C: {(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,2), (10,2)}
Parents:
	(11,1): (10,2)
	(11,2): (10,2)
	(11,3): (10,2)
G-score:
	(10,3): 7.42
	(10,1): 7.42
	(9,2): 7.42
	(11,2): 7.42
	(11,3): 8.82
	(11,1): 8.82
	(9,3): 8.82
	(9,1): 8.82
F-score:
	(10,3): 11.24
	(10,1): 11.57
	(9,2): 11.57
->(11,2): 9.82
	(11,3): 11.06
	(11,1): 9.82
	(9,3): 12.43
	(9,1): 11.82

Step 9
n_c: (11,2)
O: {(3,4), (2,3), (3,2), (4,2), (4,4), (2,4), (2,2), (5,2), (5,4), (6,2), (6,4), (7,2), (7,4), (8,2), (8,4), (9,3), (9,4) (8,1), (9,1), (10,1), (10,3), (11,1), (11,3), (12,1), (12,2), (12,3)}
C: {(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,2), (10,2), (11,2)}
Parents:
	(12,1): (11,2)
	(12,2): (11,2)
	(12,3): (11,2)
G-score:
	(11,3): 8.42
	(11,1): 8.42
	(10,2): 8.42
	(12,2): 8.42
	(12,3): 9.82
	(12,1): 9.82
	(10,3): 9.82
	(10,1): 9.82
F-score:
	(11,3): 11.24
	(11,1): 11.57
	(10,2): 11.57
	(12,2): 10.41
	(12,3): 11.06
->(12,1): 9.82
	(10,3): 12.43
	(10,1): 11.82

Step 10

n_c == goal, so the algorithm is complete.
```

## Question 3

List out the cells that represent the shortest path you found above. Then list the commands that would need to be sent to the robot to follow this path. The robot in question moves perfectly without any error, and reponds to two commands: it can either move forward a specified number of cells with `move(cells)`, or it can turn with `turn(radians)`. The robot should end at the goal the same direction at which it faced originally.


`[(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,2), (10,2), (11,2), (12,1)]`

```
move(5);
turn(-pi/4);
move(sqrt(2));
turn(pi/4);
move(2);
turn(-pi/4);
move(sqrt(2));
turn(pi/4);
```
