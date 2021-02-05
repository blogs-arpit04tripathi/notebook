---
layout: post
title: Greedy Algorithms Introduction
permalink: /:collection/cs/algorithms/greedy/introduction
---

**Greedy Strategy**
- Greedy algorithms work in stages.
- In each stage, a decision is made that is good at that point, without bothering about the future. 
- Some local best is chosen, it assumes that alocal good selection makes for a global optimal solution.

**Elements of Greedy Algorithms**
1. Greedy choice property
   - Iteratively makes one Greedy choice after another and reduces the given problem to a smaller one.
2. Optimal substructure
   - A problem exhibits optimal substructure if an optimal solution to the problem contains optimal solutions to the subproblems.
   - That means we can solve subproblems and build up the solutions to solve larger problems.

**Does Greedy Always Work?**
- Making locally optimal choices does not always work. Specially in DP problems.

**Advantages**
- straightforward
- easy to understand
- easy to code
- once we make a decision, we do not have to spend time reexamining the already computed values.

**Disadvantages**
- In many cases there is no guarantee that making locally optimal improvements in a locally optimal solution gives the optimal global solution.

**Greedy Applications**
- Sorting: Selection sort, Topological sort
- Priority Queues: Heap sort
- Huffman coding compression algorithm
- Prim’s and Kruskal’s algorithms
- Shortest path in Weighted Graph (Dijkstra’s)
- Coin change problem
- Fractional Knapsack problem
- Disjoint sets-UNION by size and UNION by height (or rank)
- Job scheduling algorithm
- Greedy techniques can be used as an approximation algorithm for complex problems