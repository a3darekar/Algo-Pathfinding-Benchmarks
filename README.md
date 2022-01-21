# Benchmarking Path Search Algorithms

## Authors
Amey Darekar, Konstantin Tenman

## Poster

[Link to the poster](https://github.com/a3darekar/UT-Algo-Pathfinding-Benchmarks/blob/main/Benchmarking_Path_Search_Algorithms_poster.pdf)

## Introduction

The major goal of this project is to revisit popular path-finding and graph traversal algorithms in order to determine how well they perform when applied to the sliding puzzle problem.

In this project we implemented three search algorithms: breadth-first, depth-first, and A* search algorithms. We compared these path finding techniques in terms of their efficiency and speed, as well as set a baseline for their performance

## Sliding Puzzle Problem

A sliding block puzzle is a type of combination problem in which neighbouring blocks or tiles are slid into the empty space to achieve a certain goal pattern or configuration. In our example problem we use a simple numbered tile sliding problem, with zero representing the blank tile. The goal state, as seen in Figure 1, is arranged as so that all tiles should be arranged in increasing order, with tile one at the top of left corner of the board and two next to it, and so on until the end. The blank tile slot goes to the last place, in the bottom right end of the board.

With every move (sliding a tile into empty slot), we generate a new state of the board. Each such state leads to several new states (between 2 to 4). We can map these connected states as a graph by representing each state as a node. Using the graph search algorithms, we can look for a path from the initial state to the goal state.

## Results
We generated 50 problems by creating random permutations for 2x3 and 3x3 puzzles. We recorded how many states were visited for each algorithm and time taken as each path was being expanded. We observed that significant number of problems were impossible to solve as we cannot swap any tiles, so we opted to benchmark both solvable and unsolvable problems independently and report a comparative analysis. Following data shows that BFS performed better compared to DFS. A* performed at par with BFS in smaller problems and outperformed both BFS and DFS for 3x3 solvable problems.

Comparing average times taken by each of the algorithms, we notice that time differences are insignificant for small size problems, but difference is visible for times of 3x3 problems. BFS and DFS run with similar speed in both Solvable and unsolvable cases. A* algorithms takes significantly smaller times for solvable problem but it is terribly slower for unsolvable problems due to overhead of computing heuristic function for each node.

## Comparison (A* vs BFS vs DFS)    
Based on the results of these tests, we found that A* search against Breadth First Searching (BFS) and Depth First Search (DFS) algorithms and discovered that fewer states are being expanded with A*. A* expands paths that are already less expensive by using the heuristic and edge cost function.
With problems that does not have a valid solution, the algorithms will traverse all of the possible state combinations and eventually return appropriate outcome. Since the problem example can result in multiple such cases, we decided to form two separate groups of such problem examples. We observed that A* outperforms other algorithms in cases where solution is reachable. On the other hand, the heuristic value calculation at every state and O(log(n)) complexity of priority queue makes execution significantly longer for cases where solution cannot be reached.

## Future Work
We observed that as the problem size grows, the number of possible states and the underlying graph of possible moves between these states. While size of puzzle problem does not seem as vast, the memory usage increases vastly over increase in size of puzzle board. 2x2 matrix has 12 unique states while 2z3 has 360 such states. This number grows to 181440 for a 3x3 puzzle. Since the path search algorithms implemented in our case keep track of huge list of visited and unvisited states in memory, the performance of the algorithm decreases very quickly. Poor Space Complexity is a major practical drawback in case of these algorithms.

Space optimized algorithms such as ID-DFS and IDA* can be explored for implemented for such cases, as these algorithms do not store the expanded states.
