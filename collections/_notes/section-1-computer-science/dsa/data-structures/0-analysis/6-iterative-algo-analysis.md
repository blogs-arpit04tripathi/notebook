---
layout: post
title: Iterative Algorithm Analysis
permalink: /algorithms/analysis/iterative
---

- TOC
{:toc}

<hr><br>

- Algorithms can be Iterative or recursive.
  - Here performance (running time) depends on the input-size. 
- If neither iterative nor recursive then its O(1), constant time.
  - Hence no dependency on input-size.
- Program written using iteration can also be written in recursive and vice-versa.

# O(1)
- Time complexity of a function (or set of statements) is considered as O(1) if it doesn’t contain loop, recursion and call to any other non-constant time function.
  - For example swap() function has O(1) time complexity.
- A loop or recursion that runs a constant number of times is also considered as O(1).

```java
for (int i = 1; i <= c; i++) { // Here c is a constant   
// some O(1) expressions 
} 
```

# O(n): 
- Time Complexity of a loop is considered as O(n) if the loop variables are incremented / decremented by a constant amount.

```java
for (int i = 1; i <= n; i += c) { // Here c is a positive integer constant
	// some O(1) expressions
}
```

# O(n^c)
- Time complexity of nested loops is equal to the number of times the innermost statement is executed. 
- For example, Selection sort and Insertion Sort have O(n^2) time complexity.
- For example, the following sample loops have O(n^2) time complexity.

```java
for (int i = 1; i <=n; i += c) {
    for (int j = 1; j <=n; j += c) { // some O(1) expressions }
}
```

# O(Logn) 
Time Complexity of a loop is considered as O(Logn) if the loop variables is divided / multiplied by a constant amount.
```java
for (int i = 1; i <=n; i *= c) {  
    // some O(1) expressions  
}
```
- For example Binary Search(refer iterative implementation) has O(Logn) time complexity. 
- Let us see mathematically how it is O(Log n). The series that we get in first loop is 1, c, c2, c3, … ck. If we put k equals to Logcn, we get c^(Logcn) which is n.

# O(LogLogn) 
Time Complexity of a loop is considered as O(LogLogn) if the loop variables is reduced / increased exponentially by a constant amount.
```java
for (int i = 2; i <=n; i = pow(i, c)) {  // Here c is a constant greater than 1
    // some O(1) expressions
}
for (int i = n; i > 0; i = fun(i)) {/* some O(1) expressions */}
//Here fun is sqrt or cuberoot or any other constant root
```

**How to combine time complexities of consecutive loops?**
- When there are consecutive loops, we calculate time complexity as sum of time complexities of individual loops.

```java
for (int i = 1; i <=m; i += c) { /* some O(1) expressions */ }
for (int i = 1; i <=n; i += c) { /* some O(1) expressions */ }
```
- Time complexity of above code is O(m) + O(n) which is O(m+n)
- If m == n, the time complexity becomes O(2n) which is O(n). 

**How to calculate time complexity when there are many if, else statements inside loops?**
- Mostly Worst case time complexity is useful, We evaluate the situation when values in if-else conditions cause maximum number of statements to be executed.
- For example consider the linear search function where we consider the case when element is present at the end or not present at all. When the code is too complex to consider all if-else cases, we can get an upper bound by ignoring if else and other complex control statements.

```java
i=1; s=1
While(s<=n){
    i++;    // I -> 1 2 3 4  5  6 
    s=s+i;  // s -> 1 3 6 10 15 21
}

This is sum of natural numbers series. (k(k+1)/2) > n
k = O{sqrt(n)}
```