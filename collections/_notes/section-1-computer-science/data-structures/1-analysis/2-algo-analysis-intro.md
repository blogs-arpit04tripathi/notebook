---
layout: post
title: Algorithms Analysis - Introduction
permalink: /:collection/cs/ds/algorithms-analysis/intro
---

**Algorithm vs Programs**
- ***Algorithm*** - Design, requires Domain Knowledge, Any Language, Hardware and Software independent, Analyze	phase.
- ***Programs*** - Implementation, Programmer, Programming Language, Hardware and Software Dependent, Testing phase.

**Priori Analysis vs Posteriori Testing**
- ***Priori Analysis*** - for Algorithm, Language independent, Hardware independent, in terms of Time and Space Function
- ***Posteriori Testing*** - for Programs, Language dependent, Hardware dependent, Watch time and bytes

# How to analyse an algorithm?
- Time
- Space
- Network consumption
- Power
- CPU Registers consumed (driver development)

Why? - All things (user friendliness, modularity, security, maintainability, etc) depends on performance.

Given two algorithms for a task, how do we find out which one is better?
1. Naive way – implement both and run them for different inputs and see which one takes less time. 
2. Asymptotic Analysis
 
There are many problems with this approach for analysis of algorithms:
- There can be many sets of input
- For some inputs, 1st algorithm performs better than the second and vice-versa – (binary vs linear search)
- For some inputs, 1st algorithm performs better on one machine and vice-versa.

![performance-sample.png]({{site.cdn}}/cse/algo/analysis/performance-sample.png)

```
lg n < n^0.5 < n < n lg n < n^2 < n^3 <2^n < n!
```