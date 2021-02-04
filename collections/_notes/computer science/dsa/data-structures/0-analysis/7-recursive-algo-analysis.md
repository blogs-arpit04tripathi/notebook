---
layout: post
title: Recursive Algorithm Analysis
permalink: /algorithms/analysis/recursive
---

- TOC
{:toc}

<hr><br>

# Recursive Algorithm Analysis
- Recursive algorithms are have a recurrence relation for time complexity. 
- We get running time on an input of size n as a function of n and the running time on inputs of smaller sizes. 
- For example in Merge Sort, to sort a given array, we divide it in two halves and recursively repeat the process for the two halves. Finally we merge the results.
  - Time complexity of Merge Sort can be written as `T(n) = 2T(n/2) + cn`.
- There are many other algorithms like Binary Search, Tower of Hanoi, etc.

**There are mainly three ways for solving recurrences:**
1. Substitution Method
2. Recurrence Tree Method
3. Master Method

### Substitution Method
- We make a guess for the solution and then we use mathematical induction to prove the guess is correct or incorrect.
- For example consider the recurrence T(n) = 2T(n/2) + n
  - We guess the solution as T(n) = O(nLogn). Now we use induction to prove our guess.
  - We need to prove that T(n) <= cnLogn. We can assume that it is true for values smaller than n.

```java
T(n) = 2T(n/2) + n <= cn/2Log(n/2) + n
    =  cnLogn - cnLog2 + n
    =  cnLogn - cn + n
    <= cnLogn
```

### Recurrence Tree Method: 
- In this method, we draw a recurrence tree and calculate the time taken by every level of tree.
- Finally, we sum the work done at all levels.
- To draw the recurrence tree, we start from the given recurrence and keep drawing till we find a pattern among levels.
- The pattern is typically a arithmetic or geometric series.

![recurrence-tree.png](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/algorithms/analysis/recurrence-tree.png)

### Master Method:
- Master Method is a direct way to get the solution.
- The master method works only for following type of recurrences or for recurrences that can be transformed to following type.

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/algorithms/analysis/master-theorem.png)

**How does this work?**
- Master method is mainly derived from recurrence tree method.
- If we draw recurrence tree of `T(n) = aT(n/b) + f(n)`, we can see that the work done at root is f(n) and work done at all leaves is Θ(nc) where c is Logba. And the height of recurrence tree is Logbn.

![master-method.png](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/algorithms/analysis/master-method.png)

In recurrence tree method, we calculate total work done.
- If the work done at leaves is polynomially more, then leaves are the dominant part, and our result becomes the work done at leaves (Case 1).
- If work done at leaves and root is asymptotically same, then our result becomes height multiplied by work done at any level (Case 2).
- If work done at root is asymptotically more, then our result becomes work done at root (Case 3).

Examples of some standard algorithms whose time complexity can be evaluated using Master Method 
- Merge Sort: T(n) = 2T(n/2) + Θ(n). It falls in case 2 as c is 1 and Logba] is also 1. So, the solution is Θ(n Logn)
- Binary Search: T(n) = T(n/2) + Θ(1). It also falls in case 2 as c is 0 and Logba is also 0. So, the solution is Θ(Logn).

Notes:
- It is not necessary that a recurrence of the form T(n) = aT(n/b) + f(n) can be solved using Master Theorem. The given three cases have some gaps between them. 
- For example, the recurrence T(n) = 2T(n/2) + n/Logn cannot be solved using master method.
- Case 2 can be extended for f(n) = Θ(n^c (Log n)^k)
- If f(n) = Θ(n^c (Log n)^k) for some constant k >= 0 and c = (Log a/Log b), then T(n) = Θ(n^c (Log n)^(k+1))

