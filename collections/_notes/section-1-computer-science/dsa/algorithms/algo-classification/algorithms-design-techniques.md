---
layout: post
title: Algorithms Design Techniques
permalink: /algorithms/design-techniques
---

- TOC
{:toc}

<hr><br>

# Classification by Implementation Method

1. **Recursion or Iteration**
   - Recursive
   - Iterative
2. **Procedural or Declarative (non-Procedural)**
   - Declarative
     - We tell what we want without telling how to do it.
     - example : SQL, queries don't specify the steps to produce result
   - Procedural
     - We have to specify the exact steps to get the result.
     - example : C, PHP, and PERL
3. **Serial or Parallel or Distributed**
   - Serial : we assume that computers execute one instruction at a time. 
   - Parallel : take advantage of computer architectures to process several instructions at a time.
     - They divide the problem into subproblems and serve them to several processors or threads.
     - Iterative algorithms are generally parallelizable.
   - Distributed : When the parallel algorithms are distributed on to different machines.
4. **Deterministic or Non-Deterministic**
   - Deterministic : solve the problem with a predefined process.
   - Non-Deterministic : guess the best solution at each step through the use of heuristics.
5. **Exact or Approximate**
   - Exact : algorithms for which we are able to find the optimal solutions 
   - Approximate : generally associated with NP-hard problems

# Classification by Design Method
1. **Greedy Method**
   - Work in stages. In each stage, a decision is made that is good at that point, without bothering about the future consequences.
   - local best is chosen. It assumes that the local best selection also makes for the global optimal solution.
2. **Divide and Conquer**
   - 3 Steps
     - Divide: Breaking the problem into sub problems that are themselves smaller instances of the same type of problem.
     - Recursion: Recursively solving these sub problems.
     - Conquer: Appropriately combining their answers.
   - No overlap of subproblems.
   - Examples: merge sort and binary search algorithms.
3. **Dynamic Programming**
   - Dynamic programming (DP) and memoization work together.
   - There will be an overlap of sub-problems.
   - By using memoization [maintaining a table for already solved sub problems], DP reduces the exponential complexity to polynomial complexity (O(n2), O(n3), etc.) for many problems.
   - The difference between dynamic programming and recursion is in the memoization of recursive calls. 
4. **Linear Programming**
   - there are inequalities in terms of inputs and maximizing (or minimizing) some linear function of the inputs.
   - Many problems (example: maximum flow for directed graphs) can be discussed using linear programming.
5. **Reduction [Transform and Conquer]**
   - we solve a difficult problem by transforming it into a known problem for which we have asymptotically optimal algorithms. 
   - example : the selection algorithm for finding the median in a list involves first sorting the list and then finding out the middle element in the sorted list.

# Other Classifications
1. **Classification by Research Area**
   - In computer science each field has its own problems and needs efficient algorithms.
   - Examples: search algorithms, sorting algorithms, merge algorithms, numerical algorithms, graph algorithms, string algorithms, geometric algorithms, combinatorial algorithms, machine learning, cryptography, parallel algorithms, data compression algorithms, parsing techniques, and more.
2. **Classification by Complexity**
3. **Randomized Algorithms**
   - A few algorithms make choices randomly.
   - For some problems, the fastest solutions must involve randomness.
   - Example: Quick Sort.
4. **Branch and Bound Enumeration and Backtracking**
