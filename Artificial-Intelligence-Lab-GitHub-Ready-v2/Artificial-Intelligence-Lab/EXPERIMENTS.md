# Experiment Record: Artificial Intelligence Lab

**Student:** Abinash Panda  
**Course:** B.Tech — Computer Science and Engineering (AI/ML)  
**Institution:** GIET University

This document explains the purpose and working of each supplied notebook. It describes the code's actual approach at a learning level; it does not claim that every possible input has been tested.

---

## Experiment 1 — Breadth-First Search (BFS)

**Notebook:** `Iai1.ipynb`

### Aim
To traverse a graph from a selected starting vertex using Breadth-First Search.

### Concept
BFS explores vertices level by level. It visits the start vertex first, then its immediate neighbours, followed by vertices at the next distance. A FIFO queue maintains the exploration order, and a visited set prevents repeated visits.

### Algorithm
1. Read the number of vertices and each vertex's adjacent vertices.
2. Read the starting vertex.
3. Add the starting vertex to the queue and visited set.
4. Remove the front vertex from the queue and print it.
5. Add each unvisited neighbour to the visited set and queue.
6. Continue until the queue is empty.

### Input
A graph entered as adjacency lists and a valid starting vertex.

### Expected result
The notebook prints the graph and the BFS traversal order reachable from the start vertex.

### Complexity
With an adjacency-list representation, BFS is typically **O(V + E)** time and **O(V)** auxiliary space, where V is the number of vertices and E is the number of edges.

### Limitation
The input must refer to vertices consistently. The traversal only visits vertices reachable from the chosen start vertex.

---

## Experiment 2 — Depth-First Search (DFS)

**Notebook:** `Iai2.ipynb`

### Aim
To traverse a graph by exploring one branch as deeply as possible before backtracking.

### Concept
DFS uses recursion in this implementation. A visited set stops the same vertex from being processed repeatedly and helps prevent infinite recursion in cyclic graphs.

### Algorithm
1. Enter the graph as adjacency lists.
2. Choose a starting vertex.
3. If the current vertex has not been visited, print it and mark it visited.
4. Recursively visit each unvisited neighbour.
5. Finish when all reachable branches have been explored.

### Input
Number of vertices, each vertex's neighbours, and a starting vertex.

### Expected result
The notebook prints the graph and DFS traversal order. The exact order depends on the order in which neighbours are entered.

### Complexity
Typically **O(V + E)** time and **O(V)** space for visited vertices and recursion in the adjacency-list model.

### Limitation
DFS traversal order is not necessarily the shortest path. Very deep graphs may exceed Python's recursion limit.

---

## Experiment 3 — Hill Climbing

**Notebook:** `Iai3.ipynb`

### Aim
To find a high value of an objective function using local search.

### Objective function
The notebook uses:

`f(x) = -x² + 10`

This function reaches its global maximum of 10 at x = 0.

### Concept
Hill climbing compares the current solution with nearby candidates and moves to a neighbour only when that neighbour has a higher objective value. The supplied code checks one step to the left and one step to the right.

### Algorithm
1. Read a starting value, step size, and maximum number of iterations.
2. Evaluate the objective at the current position.
3. Evaluate the left and right neighbouring positions.
4. Move to a neighbour if it improves the objective.
5. Stop when neither neighbour improves the value or the iteration limit is reached.
6. Print the final position and objective value.

### Expected result
The program prints the best position reached and its function value. With a suitable step size and starting value, it can approach x = 0.

### Complexity
For a fixed number of iterations, the work is **O(I)** objective evaluations, where I is the number of iterations.

### Limitation
Hill climbing is a local-search method. Results depend on the starting point and step size; a fixed step size may stop short of the exact optimum or fail to improve further.

---

## Experiment 4 — A* Search

**Notebook:** `Iai4.ipynb`

### Aim
To find a low-cost path from a start node to a goal node using path costs and heuristic estimates.

### Concept
A* evaluates nodes using `f(n) = g(n) + h(n)`, where `g(n)` is the known path cost from the start and `h(n)` is the estimated remaining cost to the goal. The notebook defines a weighted graph and a heuristic table in the code.

### Algorithm
1. Initialize the open list with the start node.
2. Select the open node with the lowest `g + h` score.
3. If it is the goal, reconstruct the path through predecessor links.
4. Otherwise, inspect its outgoing edges and update better path costs and predecessors.
5. Continue until the goal is reached or no candidates remain.

### Input
The graph, edge weights, heuristic values, start node, and goal node are defined/used in the notebook.

### Expected result
The implementation returns a path and its path cost when a route is found; otherwise it reports that no route was found.

### Complexity
A* performance depends strongly on the graph and heuristic. With a priority queue, a common graph-search implementation is often described around **O((V + E) log V)** under suitable assumptions; this notebook uses a list-based selection, so its selection step is less efficient.

### Limitation
A* optimality depends on suitable edge costs and heuristic properties. The heuristic must be defined for every node the algorithm evaluates. The provided graph is a small demonstration, not a general-purpose pathfinding library.

---

## Experiment 5 — Minimax

**Notebook:** `Iai5.ipynb`

### Aim
To compute the minimax value of a binary game tree.

### Concept
Minimax models a two-player, adversarial decision process. The maximizing player chooses the larger child value, while the minimizing player chooses the smaller child value. At the leaf level, the supplied values act as terminal evaluations.

### Algorithm
1. Read eight leaf-node scores.
2. Start at the root as the maximizing player.
3. Recursively evaluate both children.
4. At maximizing levels, return the maximum child value.
5. At minimizing levels, return the minimum child value.
6. Print the optimal value for the root.

### Expected result
The program prints the minimax value calculated from the eight supplied leaf scores.

### Complexity
For a tree with branching factor b and depth d, minimax takes **O(b^d)** time. For this binary tree, b = 2 and the configured height is 3.

### Limitation
The notebook computes a tree value from supplied leaf scores; it does not itself implement a complete playable game or generate the scores.

---

## Experiment 6 — Alpha-Beta Pruning

**Notebook:** `Iai6.ipynb`

### Aim
To compute a minimax value while pruning branches that cannot affect the final decision.

### Concept
Alpha-beta pruning tracks:
- **Alpha:** the best value currently guaranteed to the maximizing player.
- **Beta:** the best value currently guaranteed to the minimizing player.

When `alpha >= beta`, remaining children of that branch can be skipped because they cannot change the final choice.

### Algorithm
1. Read eight leaf values and set the tree height to 3.
2. Start recursive evaluation at the maximizing root.
3. Update alpha at maximizing nodes and beta at minimizing nodes.
4. Stop exploring a node's remaining children when alpha is at least beta.
5. Return and print the root's value.

### Expected result
For the same tree and leaf order, alpha-beta pruning should return the same minimax value while potentially evaluating fewer nodes.

### Complexity
Worst-case time is **O(b^d)**, like minimax. With ideal move ordering, alpha-beta can approach **O(b^(d/2))**. Actual pruning depends on the order of the children.

### Limitation
The notebook demonstrates value calculation for a fixed binary tree. It does not count visited nodes or display a pruning visualization.

---

## Experiment 7 — Eight Queens Problem

**Notebook:** `Iai7.ipynb`

### Aim
To place eight queens on an 8×8 chessboard so that no two queens attack each other.

### Constraints
No two queens may share the same row, column, or diagonal.

### Concept
The program uses backtracking. It places one queen per row, checks whether a position is safe, and reverses a placement when it prevents a complete solution.

### Algorithm
1. Begin with an empty 8×8 board.
2. For the current row, test each column.
3. Check the column and both upper diagonals for an existing queen.
4. If safe, place a queen and recurse to the next row.
5. If a later row cannot be solved, remove the queen and try another column.
6. Stop when all eight rows are filled.

### Expected result
The notebook prints a valid board arrangement if a solution is found.

### Complexity
Backtracking has exponential worst-case search behaviour; a loose upper bound for trying column placements row by row is **O(N!)** with pruning, with N = 8 here.

### Limitation
The supplied code stops after finding its first solution; it does not enumerate every valid arrangement.

---

## Experiment 8 — Water Jug Problem

**Notebook:** `IAI8.ipynb`

### Aim
To find a sequence of operations that leaves a target amount of water in one of two jugs.

### State representation
A state is `(jug1, jug2)`, representing the current amount of water in each jug.

### Available operations
- Fill either jug completely.
- Empty either jug.
- Pour water from one jug into the other until the source is empty or the destination is full.

### Concept
The notebook uses BFS over jug states. BFS explores states by number of operations, while a visited set prevents repeated processing of states.

### Algorithm
1. Read the capacities of both jugs and the target amount.
2. Start from `(0, 0)`.
3. Generate all states reachable by one legal operation.
4. Add unvisited states to the queue with their path.
5. Stop when either jug contains the target amount.
6. Print the sequence of states, or report no solution.

### Expected result
A sequence of jug states is printed when the target is reached; otherwise the notebook reports that no solution was found.

### Complexity
There are at most `(capacity1 + 1) × (capacity2 + 1)` distinct integer states. BFS is proportional to the number of reachable states and transitions.

### Limitation
The implementation seeks the target in either jug, not necessarily the combined total. A target must be feasible for the given capacities.

---

## Experiment 9 — Tic-Tac-Toe

**Notebook:** `IAI9.ipynb`

### Aim
To implement a basic two-player Tic-Tac-Toe game in the terminal.

### Concept
The board is a 3×3 grid. Players alternate between X and O. A winner is detected when a row, column, or diagonal contains three matching non-empty symbols.

### Algorithm
1. Initialize an empty 3×3 board and set the current player to X.
2. Display the board and ask for row and column numbers.
3. Check that the selected position is within range and empty.
4. Place the current player's symbol.
5. Check for a winning row, column, or diagonal.
6. If there is no winner, switch players and continue for at most nine turns.
7. Finish with a winner or a draw.

### Expected result
The game displays the board after moves and reports a win or draw based on the moves entered.

### Complexity
Each move checks a constant-sized board, so winner checking is **O(1)** for a fixed 3×3 board.

### Limitation
This is a human-versus-human game; it does not include an AI opponent. Inputs must be valid integers in the expected range.

---

## Experiment 10 — Travelling Salesman Problem (TSP)

**Notebook:** `Iai10.ipynb`

### Aim
To find the minimum-cost round trip that starts at a selected city, visits every other city once, and returns to the start.

### Concept
The notebook uses exhaustive search. It generates every permutation of cities other than the start city, calculates the total round-trip cost, and keeps the cheapest route.

### Algorithm
1. Read the number of cities.
2. Read the square distance/cost matrix.
3. Read the starting city index.
4. Generate every ordering of the remaining cities.
5. Sum the costs along the route and the return edge.
6. Keep the route with the smallest total cost.
7. Print the best path and minimum cost.

### Expected result
The program prints the best route found and its total cost for the supplied matrix.

### Complexity
The brute-force approach evaluates `(n − 1)!` possible orders, with route evaluation taking O(n) each, giving approximately **O(n!)** time and **O(n)** working space aside from permutation generation details.

### Limitation
The factorial runtime makes this approach suitable only for small city counts. The matrix should be square, and the chosen start index must be in the range `0` to `n−1`.

---

## Overall Conclusion

These ten practicals demonstrate several foundational AI approaches: systematic graph traversal (BFS and DFS), local improvement (hill climbing), heuristic path search (A*), adversarial tree evaluation (minimax and alpha-beta pruning), constraint solving (Eight Queens), state-space exploration (Water Jug), rule-based game logic (Tic-Tac-Toe), and exhaustive combinatorial optimization (TSP).

Together, they illustrate how the choice of representation and search strategy affects correctness, solution quality, and computational cost.
