# Screening-Tasks
Screening Tasks for Quantum open source foundation Cohort 9
# Task 3 & 4

## Table of Contents
- [Task Description](#Task-Description)
- [Maximum Independent Set Problem](#Maximum-Independent-Set-Problem)
-  [Gate based QAOA](#Gate-based-QAOA)
  - [VQAA](#VQAA)
  - [Bloqade](#Bloqade)
- [Results](#results)
- [References](#references)

## Task-Description
An independent set is a set of vertices in a graph such that no two of which are connected by an edge. The problem of finding Maximum Independent Sets (MIS) is NP-hard. In this task, you will solve small instances of the MIS with gate and analog-based quantum computing:

Create 4 graphs with 3, 5, 6, and 7 nodes. You can define the edges as you prefer. For each graph, find the MIS using the following methods: The Gate-Based QAOA
The Quantum adiabatic algorithm using analog based quantum computing. You can check the documentation in Pulser and Blockade for references. Compared the results
## Maximum-Independent-Set-Problem
a maximal independent set (MIS) or maximal stable set is an independent set that is not a subset of any other independent set. In other words, there is no vertex outside the independent set that may join it because it is maximal with respect to the independent set property.
The Maximum Independent Set (MIS) problem in graph theory is the task of finding the largest independent set in a graph, where an independent set is a set of vertices such that no two vertices are adjacent. There is currently no known efficient algorithm to find maximum independent sets.
![MISP](https://github.com/AbdullahKazi500/Screening-Tasks/assets/75779966/d1c42ea9-ae25-4720-97ca-dccb378ec5a6)

## Gate-based-QAOA
Gate based QAOA Gate-based Quantum Approximate Optimization Algorithm (QAOA) is a quantum algorithm designed for solving combinatorial optimization problems. These are problems where the goal is to find the best solution from a finite set of possible solutions. Examples include the Traveling Salesman Problem, Maximum Cut, and the Maximum Independent Set Problem. QAOA Objective Function Gate-based QAOA aims to minimize or maximize an objective function that represents the optimization problem. The objective function maps candidate solutions to real numbers, with the optimal solution corresponding to the minimum or maximum value.
Here we have used the [Classiq SDK](https://www.classiq.io/) To Calculate the Maximum independent set using Gate based QAOA Gate-based Quantum Approximate Optimization Algorithm (QAOA) is a quantum algorithm designed for solving combinatorial optimization problems we define a mathematical optimization model using the Pyomo library for the Maximum Independent Set (MIS) problem. The MIS problem aims to find the largest possible subset of vertices in a graph such that no two vertices in the subset are adjacent (i.e., connected by an edge).we code a script that utilizes the Classiq library to find the Maximum Independent Set (MIS) for randomly generated graphs of different sizes. We import the necessary libraries including NetworkX for graph operations, NumPy for numerical computations, Pyomo for modeling optimization problems, and various components from the Classiq library for quantum optimization.

The mis function defines a Pyomo ConcreteModel representing the MIS optimization model. It creates a binary variable for each node in the graph, adds constraints to ensure that no two adjacent nodes are both included in the independent set, and defines the objective function to maximize the total number of nodes in the independent set.

The find_mis function iterates over a list of the number of nodes for each graph. For each number of nodes:

It generates a random graph using NetworkX. Defines the MIS Pyomo model for the graph. Constructs the QAOA (Quantum Approximate Optimization Algorithm) optimization model using the Classiq library. Sets execution preferences for quantum backend simulation. Executes the quantum program, synthesizes it, and extracts optimization results. Prints the independent set and its size for the graph. Plots the graph with the independent set highlighted in red. List of Number of Nodes: The num_nodes_list contains the number of nodes for each graph.

Finally, the find_mis function is called with the list of number of nodes to find the MIS for each graph.
![image](https://github.com/AbdullahKazi500/Screening-Tasks/assets/75779966/680d8650-b09e-4920-86da-3cb642fd45ac)

## Pulser
We defined the functions to find the maximum independent set (MIS) of graphs. The code creates graphs with 3, 5, 6, and 7 nodes. For each graph size, a random adjacency matrix is generated using np.random.randint(0, 2, size=(num_nodes, num_nodes)). This matrix is then made symmetric by adding its transpose to itself (excluding the diagonal) to ensure that the graph is undirected.

The cost_function calculates the cost of a given state (a potential independent set) based on the adjacency matrix. It computes the sum of the weights of the edges connecting vertices in the set. Higher weights indicate fewer edges between vertices, favoring independent sets.

 The objective_function is the function to minimize, which is the negative of the cost function. Minimizing the negative of the cost function is equivalent to maximizing the cost function itself.
The find_max_independent_set function takes an adjacency matrix as input and returns the maximum independent set. It initializes a random initial state, normalizes it, and uses the minimize function from scipy.optimize to minimize the objective function subject to the constraint that the norm of the state vector is 1.

further we calculate the maximum independent set for each graph using find_max_independent_set, and store the result in the max_independent_sets dictionary.

we print the maximum independent set for each graph size.
We ran into issues while using Pulser from Pasqal and while importing the Solver QAA
## Bloqade adiabatic neutral atoms
## Results


## References

- E. Farhi, J. Goldstone, S. Gutmann, J. Lapan, A. Lundgren, and D. Preda, Science 292, 472 (2001).
.

- Quantum Optimization for Maximum Independent Set Using Rydberg Atom Arrays
Hannes Pichler, Sheng-Tao Wang, Leo Zhou, Soonwon Choi, Mikhail D. Lukin.”
- R. Barends, A. Shabani, L. Lamata, J. Kelly, A. Mezzacapo, U. L. Heras, R. Babbush, A. G. Fowler, B. Campbell, Y. Chen, Z. Chen, B. Chiaro, A. Dunsworth, E. Jeffrey, E. Lucero, A. Megrant, J. Y. Mutus, M. Neeley,
C. Neill, P. J. J. O’Malley, C. Quintana, P. Roushan,
D. Sank, A. Vainsencher, J. Wenner, T. C. White,
E. Solano, H. Neven, and J. M. Martinis, Nature 534,
222 (2016).
-  Max Independent Set (Wikipedia)

- Farhi, Edward, Jeffrey Goldstone, and Sam Gutmann. "A quantum approximate optimization algorithm." arXiv preprint arXiv:1411.4028 (2014).

- Barkoutsos, Panagiotis Kl, et al. "Improving variational quantum optimization using CVaR." Quantum 4 (2020): 256.
