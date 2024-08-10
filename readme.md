# CSE 3111 / CSE 3213 - ARTIFICIAL INTELLIGENCE - FALL 2023
## Programming Assignments Report

**Contributors:**
- Furkan Bulut
- İsmet Eren Yurtcu
- Gonca Arabacı

**Submission Date:** 5 January 2024

---

## Table of Contents

1. [Development Environment](#1-development-environment)
2. [Problem Formulation](#2-problem-formulation)
3. [Results](#3-results)
   - [Breadth-First Search (BFS)](#breadth-first-search-bfs)
   - [A* Search](#a-search)
   - [Depth-Limited Search (DLS)](#depth-limited-search-dls)
   - [Hill Climbing Search](#hill-climbing-search)
4. [Discussion](#4-discussion)

---

## 1. Development Environment

- **Operating System:** Windows 11
- **Python Version:** 3.11.7
- **IDE:** PyCharm 2023.3.1 (Professional Edition)
- **Packages:** 
  - `jupyter==1.0.0`
  - `simpleai==0.8.3`

---

## 2. Problem Formulation

- **State Representation:** The state is represented as a tuple of length N, where each element corresponds to the row position of a queen in the respective column.
- **Initial State:** Can be provided by the user (manual input) or generated randomly. The state must be a valid configuration of N queens on the board.
- **Actions:** Moving a queen to a different row within its column. Each action is represented as a tuple where the first element is the new state resulting from the move, and the second element is the cost of that action.
- **Transition Model:** Implemented in the `actions` and `result` methods. The `actions` method generates all possible moves for each queen, while the `result` method computes the new state after performing an action.
- **Goal Test:** Checks if the current state represents a solution where no two queens threaten each other. This is done in the `is_goal` method.
- **Path Cost:** Determined by the number of attacking pairs of queens in the current state. The goal is to minimize this cost to find an optimal solution.

The problem is formulated as a search issue, where different search techniques are used to find a reasonable queen placement on the chessboard. The objective is to reach a state with no attacking pairs by exploring different configurations of the queens.

---

## 3. Results

### Breadth-First Search (BFS)

- **Completeness:** BFS is complete and will find a solution if one exists by exploring the state space level by level.
- **Optimality:** Guarantees optimality when step costs are uniform. With varying step costs, BFS may not always find the optimal solution.
- **Time Complexity:** High, due to exploring all nodes at a given depth before moving to the next level.
- **Space Complexity:** High, as it needs to store all nodes at a given level.

### A* Search

- **Completeness:** Complete, provided the heuristic is admissible and consistent.
- **Optimality:** Optimal when the heuristic is admissible, as it considers both the cost to reach the current node and the estimated cost to reach the goal.
- **Time Complexity:** Can be efficient, depending on the quality of the heuristic.
- **Space Complexity:** Generally higher than BFS, due to the use of a priority queue for nodes based on estimated costs.

### Depth-Limited Search (DLS)

- **Completeness:** Not complete. It may terminate without finding a solution if the depth limit is reached without success.
- **Optimality:** Not guaranteed. May result in a suboptimal solution if it terminates at the depth limit.
- **Time Complexity:** Lower compared to BFS, as it avoids exploring deeper levels.
- **Space Complexity:** Relatively low, storing only nodes up to the specified depth limit.

### Hill Climbing Search

- **Completeness:** Not complete. Can get stuck in local optima and may not find the global optimum.
- **Optimality:** Not guaranteed. Effectiveness depends on the starting point and may converge to a local optimum.
- **Time Complexity:** Can be computationally efficient, exploring the immediate neighborhood of a state.
- **Space Complexity:** Low, as it does not need to store a large number of nodes.

---

## 4. Discussion

- **A* Search:** Balances completeness and optimality well, making it a strong candidate for various search scenarios. Its effectiveness depends on the quality of the heuristic used.
- **Hill Climbing Search:** Offers swift performance and may be suitable for integration into various algorithms. Its agility makes it a viable option in specific contexts, though it lacks completeness and optimality guarantees.

In summary, while A* provides a robust approach for finding optimal solutions with an effective heuristic, hill climbing search proves to be valuable for its speed and applicability in certain scenarios.

