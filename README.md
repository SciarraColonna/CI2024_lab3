# CI2024_lab3

## Problem representation
Any disposition of the numbers on the game board is stored as a list of integers and is interpreted as a matrix with row major<br>
The starting state is obtained by generating the final correct solution and by applying 10.000 random actions to it.

## Approach 1 (*Breadth-first search*)
The algorithm explores the possible problem paths using a breadth-first search and a side data structure that is a tree stored in a list in a similar way to an heap (but without the guarantee of being binary or quasi-complete).<br>
The search starts from the root (starting state) and, at each step, inserts the current node's children in the tree and then iterates over the node that follows the current one in the tree list. Once the correct solution is reached, the search stops and the tree list is used to "climb" the tree from children to parent until we reach the root, so that we can reconstruct the solution path.
This algorithm, because of the use of the tree list, is quite memory consuming (especially with promblem size greater than 3) but it guarantees to find the path with the lower number of steps (that is, the closest solution to the root).

## Approach 2 (*Depth-first search*)
The algorithm explores the possible problem paths using a depth-first search and the same tree list as before.<br>
The search starts from the root (starting state) and, at each step, inserts the current node's children in the tree and then iterates over the last node inserted in the tree list. Once the correct solution is reached, the search stops and the tree list is used to "climb" the tree from children to parent until we reach the root, so that we can reconstruct the solution path.
The search also implements a sort of backtrack that is used to detect the situations of infinite loops over the same dispositions and avoid them by moving the search to the fisrt (from the bottom) node that has been disvovered but not yet visited.
This algorithm is much more memory consuming and does not guarantee the solution to be the one with the lowest number of steps.

## Approach 3 (*A-star problem*)
This approach implements an A-star algorithm where the cost *f(n) = g(n) + h(n)* is based on the number of moves to reach the current state (*g(n)*) and the Manhattan distance with respect to the final solution (*h(n)*).<br>
This algorithm guarantees a faster execution and a much lower memory usage but the provided solution is often not optimal. 
<br>
<br>
<br>

**WARNING**: Both detph-first and breadth-first algorithm become highly memory consuming when solving problems with dimension greater or equal to 4, leading the execution to an unexpected crash. Moreover, the depth-first search works for problems with dimension 3 but requires a long execution time.
