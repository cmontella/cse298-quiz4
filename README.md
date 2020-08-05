# CSE 298 - Quiz 4

Due: 8/04 by end of day

Make at least 1 commit per question.

## Question 1

What is the difference between Dijkstra's Algorithm and A*. Why would one use Dijkstra's over A* and vice versa?

The difference between Dijkstra’s Algorithm and A* is that Dijkstra’s doesn’t use a heuristic function therefore classifying it as an uniformed search Algorithm. With a lot of grids it is better better to use A* as it is faster though in very small grids its better to use Dijkstra’s.

## Question 2

Consider the following robot in a grid 2D grid world:

![Gridworld](https://github.com/cmontella/cse298-quiz4/blob/master/gridworld.png?raw=true)

The cell (0,0) is at the bottom left. The robot starts at cell (3,3) and is facing in the 0 radians direction. The robot's goal cell is (12,1), facing the 0 radians direction as well.

Perform the A* algorithm by hand to find the shortest path from the robot's starting location to the goal. Write down each step of the algorithm, including the current cell, open set of cells O, the closed set of cells C, the parent of each cell, and the current g-score and f-scores for each cell (these can be a sparse lists i.e. you don't need to write the scores/parents of the cells haven't been considered by the algorithm yet). You can use any heuristic you like, but specify the one you are using.

Using the Heuristic Function(The Distance formula[The one given in the video]) find the distance to the destination
Step 1
Current cell (3,3)
O: [adjacent cells: (4,3),(3,4),(2,3),(3,2), (4,4),(2,2),(2,4)(4,2)]
C : [0]
P: [0]
Adjacent g-scores
(4,3),(3,4),(2,3),(3,2)- 1 Horizontal and Vertical Cells
(4,4),(2,2),(2,4)(4,2)- sqrt(2) Diagonal Cells
Adjacent f-score
Use distance formula from the neighboring cell to solve
Notable F-scores (4,3) = 1+  sqrt(68), (3,2) = 1 + sqrt(82) ,(4,2) = sqrt(2) + sqrt(65)
(4,3) smallest f score
Step 2
Current cell (4,3)
O: [adjacent cells of starting position plus new adjacent cells]
C : [3,3]
P: [3,3]
Adjacent g-scores
1 Horizontal and Vertical Cells
sqrt(2) Diagonal Cells
Adjacent f-score
Notable F-scores (5,3) = 1 + sqrt(53), (4,2) = 1 + sqrt(82), (5,2) = sqrt(2) + sqrt(50)
This repeats for Steps 3,4,5,6 until cell (10,3)
Step 7
Current cell (10,3)
O: [adjacent cells + adjacent cells for previous iterations]
C : [(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,3)]
P: [9,3]
Adjacent g-scores
1 Horizontal and Vertical Cells
sqrt(2) Diagonal Cells
Adjacent f-score
Notable F-scores (11,3) = 1 + sqrt(5), (10,2) = 1 + sqrt(5), (11,2) = sqrt(2) + sqrt(2)
Lowest f score is for (11,2)
Step 8
O: [adjacent cells + adjacent cells for previous iterations]
C : [(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,3)]
P: [9,3]
Adjacent g-scores
1 Horizontal and Vertical Cells
sqrt(2) Diagonal Cells
Adjacent f-score
Notable F-scores (11,3) = 1 + sqrt(5), (10,2) = 1 + sqrt(5), (11,2) = sqrt(2) + sqrt(2)
Lowest f score is for (11,2)
Step 9
Current cell (11,2)
O: [adjacent cells + adjacent cells for previous iterations]
C : [(3,3), (4,3), (5,3), (6,3), (7,3), (8,3), (9,3),(10,3)]
P: [10,3]
Adjacent g-scores
1 Horizontal and Vertical Cells
sqrt(2) Diagonal Cells
Lowest f score is for (12,1) = sqrt(2) + 0
Step 10
Checks if current cell is equal to goal cell, Passes


## Question 3

List out the cells that represent the shortest path you found above. Then list the commands that would need to be sent to the robot to follow this path. The robot in question moves perfectly without any error, and reponds to two commands: it can either move forward a specified number of cells with `move(cells)`, or it can turn with `turn(radians)`. The robot should end at the goal the same direction at which it faced originally.

Shortest path
Move (3,3) to (10,3) Move 7 cells forward
Turn – pi/4 radians or pi/4 radians to the right
Move (10,3) to (12,1) Move 2*sqrt(2) cells forward
Turn pi/4 radians or pi/4 radians to the left

This would be for the global plan with a local plan involved and trajectory rollout there would be smoother turning involved.

