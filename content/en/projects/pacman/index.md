---
title: Pacman
date: 2025-03-01
links:
  - type: site
    url: https://github.com/wlsdudwjd/pacman
tags:
  - python
  - HugoBlox
  - Markdown

featured: true

share: false

reading_time: false

math: true
---

This is the UC Berkeley Pacman AI project I completed as part of my Artificial Intelligence and Data Structures coursework. The core objective of this assignment was to implement fundamental Graph Search algorithms from scratch and apply them to solve tangible problems within the Pacman game environment.

My work involved implementing generic search algorithms in **search.py** and defining/solving specific Pacman problems in **searchAgents.py**.

## 1. Core Search Algorithm Implementation (search.py)

First, I implemented four fundamental search algorithms that can be applied to any search problem.

- DFS (Depth-First Search): Using a **Stack**, this algorithm explores nodes as deeply as possible first. It was implemented as a graph search, using an **explored** list to prevent cycles.
- BFS (Breadth-First Search): Using a **Queue**, this algorithm explores the shallowest (closest) nodes first. It guarantees the shortest path when all edge costs are uniform.
- UCS (Uniform Cost Search): Using a **PriorityQueue**, this algorithm prioritizes nodes by their total cumulative 'cost'. It always explores the path with the lowest cost first, guaranteeing the shortest cost path.
- A* (A-Star) Search: Also uses a **PriorityQueue**, but its priority is the sum of the 'cumulative cost to date' ($g(n)$) and an 'estimated cost to the goal' (heuristic, $h(n)$). This function is $f(n) = g(n) + h(n)$. As an informed search, it finds the optimal solution far more efficiently than UCS.

## 2. Defining and Solving Pacman Problems (searchAgents.py)

Beyond just implementing the algorithms, I modeled complex problems Pacman faces as formal 'search problems' and solved them.

📍 The Corners Problem (CornersProblem)
The challenge is to find a path for Pacman to visit all four corners of the map.

- State Definition: To solve this, the state space couldn't just be (x, y). I defined the state as **(currentPosition, (visitedCornersTuple))**. For example, a state might be **((5, 5), (True, False, False, True))**, tracking both the position and the visit-status of each corner.
- Goal Definition: The goal state is reached when all boolean values in the tuple state[1] are **True**.
- Successor Function: As Pacman moves, the function checks if the new position is one of the corners. If it is, it generates a new state with the corresponding boolean in the tuple updated to **True**.

💡 Corners Problem Heuristic (cornersHeuristic)

I designed a heuristic for solving the Corners Problem using A* search.

- Design: A heuristic must be admissible (never overestimates the true cost).
- Logic: The function calculates the Manhattan Distance from the 'current position' to 'every unvisited corner'. It then returns the maximum (max) value among these distances.
- Justification: This is admissible because Pacman must travel at least as far as the farthest remaining corner to complete the goal. This value serves as a safe lower bound on the true remaining cost.

🍔 All Food Heuristic (foodHeuristic)

This heuristic was for the **FoodSearchProblem**, which involves finding a path to eat all the food dots on the map.
- Logic: Similar to the corners heuristic, I calculated the actual maze distance (**mazeDistance**) from the 'current position' to 'every remaining food dot' and returned the maximum (max) value.
- Using **mazeDistance**: Unlike Manhattan distance, **mazeDistance** is a helper function that runs a BFS to find the true shortest path considering walls, providing a much more accurate (and still admissible) estimate.

🎯 Closest Dot Search Agent

Finding a path to eat all food is very complex (NP-hard). Therefore, I implemented a greedy algorithm that repeatedly finds and eats the closest food dot.
- **findPathToClosestDot** Implementation: I defined a sub-problem called **AnyFoodSearchProblem** (where the goal is to reach any single food dot).
- Using UCS: I applied **UCS** to this sub-problem. This finds the path to the food dot with the lowest cost (i.e., the closest dot). (Since costs are uniform, **BFS** would also have guaranteed the same result).

<!--more-->
