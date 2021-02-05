---
layout: post
title: Asymptotic Notations
permalink: /:collection/cs/ds/algorithms-analysis/asymptotic-notations
---

- TOC
{:toc}

<hr><br>

- **Asymptotic Analysis** - To have a measure of efficiency of algorithms indepent of machine-specific constants without implementing the algorithm.
- **Asymptotic Notations** - Mathematical tools to represent time complexity of algorithms for asymptotic analysis.

![o-notation.png](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/algorithms/analysis/o-notation.png)

# Θ Notation: 
- Bounds a function from above and below, so it defines exact asymptotic behavior.
- 3n^3 + 6n^2 + 6000 = Θ(n^3), there will always be a number n0 after which Θ(n^3) has higher values than Θn^2) irrespective of the constants involved.

```
Θ(g(n)) = { f(n): there exist positive constants c1, c2 and n0 
such that 0 <= c1*g(n) <= f(n) <= c2*g(n) for all n >= n0 }
```
The above definition means,
- if f(n) is Θ(g(n)), then the value f(n) is always between c1*g(n) and c2*g(n) for large values of n (n >= n0).
- f(n) must be non-negative for values of n greater than n0.

# Big O Notation (Worst Case)
- Defines an upper bound of an algorithm, it bounds a function only from above.
- If we use Θ notation to represent time complexity of Insertion sort, we have to use two statements for best and worst cases:
    1. The best-case time complexity of Insertion Sort is Θ(n).
    2. The worst-case time complexity of Insertion Sort is Θ(n2), also covers linear time.

Useful when we only have upper bound on time complexity of an algorithm.
```
O(g(n)) = {f(n): there exist positive constants c and n0 
such that 0 <= f(n) <= cg(n) for all n >= n0}
```

# Ω Notation (Best Case)
Ω notation provides an asymptotic lower bound, best-case performance and least used notation.

For a given function g(n), we denote by Ω(g(n)) the set of functions.

```
Ω (g(n)) = {f(n): there exist positive constants c and n0 
such that 0 <= cg(n) <= f(n) for all n >= n0}.
```

# Little ο asymptotic notation
- Little o provides strict upper bound (equality condition is removed from Big O) 
- Big-Ο (O(n)) is used as a ***tight upper-bound***.
- Little-ο (ο(n)) notation is used for ***loose upper-bound***.

Let f(n) and g(n) be functions that map positive integers to positive real numbers. 
```
f(n) = ο(g(n)) OR ο(g(n)) = { f(n): there exist positive constants c > 0, n0 > 1
such that 0 <= f(n) < c.g(n)  for all n > n0 }
```

![little-o-example.png](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/algorithms/analysis/little-o-example.png)

# Little ω asymptotic notation
- Little omega provides strict lower bound (equality condition removed from big omega)

Let f(n) and g(n) be functions that map positive integers to positive real numbers. 
```
f(n) = ω(g(n)) OR ω(g(n)) = { f(n): there exist positive constants c > 0, n0 ≥ 1
such that f(n) > c.g(n) ≥ 0  for all n > n0 }
```
- Symbolises Loose lower bound. 
- f(n) has a higher growth rate than g(n). 

```
For Big Omega f(n)=Ω(g(n)), bound is 0<=c*g(n0), For little omega, it is true for all constant c>0.
f(n) = ω(g(n)) if and only if g(n) = ο((f(n)).
```
![little-omega-example.png](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dsa/algorithms/analysis/little-omega-example.png)