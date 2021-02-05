---
layout: post
title: Recurrence Relations
permalink: /:collection/cs/ds/algorithms-analysis/recurrence-relations
---

- TOC
{:toc}

<hr><br>

# Type 1: Divide and conquer recurrence relations

Following are some of the examples of recurrence relations based on divide and conquer.
```
T(n) = 2T(n/2) + cn
```
- These types of recurrence relations can be easily solved using master method (Put link to master method).
- For recurrence relation T(n) = 2T(n/2) + cn, the values of a = 2, b = 2 and k =1. Here logb(a) = log2(2) = 1 = k. Therefore, the complexity will be Θ(nlog2(n)).

``` 
T(n) = 2T(n/2) + √n
```
Similarly, for recurrence relation T(n) = 2T(n/2) + √n, the values of a = 2, b = 2 and k =1/2. Here logb(a) = log2(2) = 1 > k. Therefore, the complexity will be Θ(n).

# Type 2: Linear recurrence relations

```
T(n) = T(n-1) + n for n>0 and T(0) = 1
```
These types of recurrence relations can be easily solved using substitution method (Put link to substitution method). For example,
- T(n) = T(n-1) + n = T(n-2) + (n-1) + n = T(n-k) + (n-(k-1))….. (n-1) + n
Substituting k = n, we get
- T(n) = T(0) + 1 + 2+….. +n = n(n+1)/2 = O(n^2)

# Type 3: Value substitution before solving

Sometimes, recurrence relations can’t be directly solved using techniques like substitution, recurrence tree or master method. Therefore, we need to convert the recurrence relation into appropriate form before solving. For example,
```
T(n) = T(√n) + 1
```
To solve this type of recurrence, substitute n = 2^m as:
```
T(2^m) = T(2^m /2) + 1
Let T(2^m) = S(m), S(m) = S(m/2) + 1 
```
Solving by master method, we get
```
S(m) = Θ(logm)
As n = 2^m or m = log2(n),
T(n) = T(2^m) = S(m) = Θ(logm) = Θ(loglogn)
```

**What is the time complexity of Tower of Hanoi problem?**
1. T(n) = O(sqrt(n))
2. T(n) = O(n^2)
3. T(n) = O(2^n)
4. None

Solution: For Tower of Hanoi, 
```java
T(n) = 2T(n-1) + c for n>1 and T(1) = 1.
// Solving this,
T(n) = 2T(n-1) + c
     = 2(2T(n-2)+ c) + c  = 2^2*T(n-2) + (c + 2c)
     = 2^k*T(n-k) + (c + 2c + .. kc)
Substituting k = (n-1), we get
T(n) = 2^(n-1)*T(1) + (c + 2c + (n-1)c) = O(2^n)
```

**Consider the following recurrence: T(n) = 2 * T(ceil (sqrt(n) ) ) + 1, T(1) = 1, Which one of the following is true?**
1. T(n) = (loglogn)
2. T(n) = (logn)
3. T(n) = (sqrt(n))
4. T(n) = (n)

Solution: To solve this type of recurrence, substitute n = 2^m as:
```java
T(2^m) = 2T(2^m /2) + 1
Let T(2^m) = S(m), S(m) = 2S(m/2) + 1 
// Solving by master method, we get
S(m) = Θ(m)
As n = 2m or m = log2n,
T(n) = T(2^m) = S(m) = Θ(m) = Θ(logn)
```
