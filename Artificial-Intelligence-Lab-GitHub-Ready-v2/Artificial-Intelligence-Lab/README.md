# Artificial Intelligence Lab Practicals

**Author:** Abinash Panda  
**Program:** B.Tech — Computer Science and Engineering (AI/ML)  
**Institution:** GIET University  
**Repository type:** Academic practicals and learning exercises

## Overview

This repository contains 10 Python/Jupyter Notebook practicals on foundational Artificial Intelligence concepts. The exercises cover uninformed search, local search, heuristic search, adversarial game-tree search, backtracking, state-space search, and combinatorial optimization.

The notebooks are intended for learning, experimentation, and academic revision. Each experiment's aim, core idea, algorithm outline, inputs, expected result, and limitations are documented in [`EXPERIMENTS.md`](EXPERIMENTS.md).

## Experiment Index

| No. | Notebook | Experiment |
|---:|---|---|
| 1 | [`Iai1.ipynb`](Iai1.ipynb) | Breadth-First Search (BFS) graph traversal |
| 2 | [`Iai2.ipynb`](Iai2.ipynb) | Depth-First Search (DFS) graph traversal |
| 3 | [`Iai3.ipynb`](Iai3.ipynb) | Hill Climbing for numerical optimization |
| 4 | [`Iai4.ipynb`](Iai4.ipynb) | A* heuristic pathfinding |
| 5 | [`Iai5.ipynb`](Iai5.ipynb) | Minimax algorithm for game trees |
| 6 | [`Iai6.ipynb`](Iai6.ipynb) | Alpha-Beta pruning |
| 7 | [`Iai7.ipynb`](Iai7.ipynb) | Eight Queens problem using backtracking |
| 8 | [`IAI8.ipynb`](IAI8.ipynb) | Water Jug problem using BFS |
| 9 | [`IAI9.ipynb`](IAI9.ipynb) | Two-player Tic-Tac-Toe |
| 10 | [`Iai10.ipynb`](Iai10.ipynb) | Travelling Salesman Problem (brute-force permutations) |

## Learning Outcomes

- Represent problems using graphs, states, and search trees.
- Compare breadth-first and depth-first traversal.
- Understand heuristic evaluation and local optimization.
- Trace minimax decisions and alpha-beta cutoffs.
- Apply backtracking to constraint-satisfaction problems.
- Model state transitions and search for a valid solution.
- Evaluate the cost of exhaustive search for combinatorial problems.

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab

Install Jupyter if it is not already installed:

```bash
python -m pip install notebook
```

Launch it from this folder:

```bash
jupyter notebook
```

Alternatively, open the `.ipynb` files in Visual Studio Code with the Python and Jupyter extensions.

## How to Run

1. Download or clone this repository.
2. Open the repository folder in Jupyter Notebook, JupyterLab, or VS Code.
3. Open one notebook.
4. Run its cells in order.
5. When prompted, enter the required graph, values, capacities, moves, or distance matrix.

**Note:** These notebooks use interactive `input()` prompts. Run them in an environment that supports interactive input. For the Travelling Salesman experiment, provide a square adjacency/distance matrix and use consistent city indices.

## Scope and Limitations

These are educational implementations rather than production-ready AI systems. Runtime depends on the input size and problem structure. Some algorithms make assumptions about input format or use simplified examples; check the code and experiment notes before changing inputs.

## Author

**Abinash Panda**  
B.Tech — Computer Science and Engineering (AI/ML)  
GIET University
