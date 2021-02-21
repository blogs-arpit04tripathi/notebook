---
layout: post
title: VarArgs - Variable Length Arguments
permalink: /:collection/java/varargs
---

# Using Command-Line Arguments
* variable number of arguments to methods. (varargs method)
* A variable-length argument is **specified by three periods (…)**.
* Example - command-line arguments stored as String[] are passed to main() when you run the app.

```java
static void vaTest(String msg, int...v) {
    for (int x: v) System.out.print(x + " ");
}
vaTest("hi");
vaTest("hi", 1, 2, 3);
int doIt(int a, int b, int...vals, boolean stopFlag) {
    // Error!
}
```

# Restrictions
* vararg should be the last.
* Only one vararg parameter is allowed

# varargs method overloading
* Different type of vararg parameter - vaTest(int ...) and vaTest(boolean ...).
* add 1 or more normal parameters.

# Varargs and Ambiguity
```java	
static void vaTest(int ... v) { 
static void vaTest(boolean ... v) {
static void vaTest(String msg, int ... v) {
vaTest(); // Error: Ambiguous!
```
```java
static void vaTest(int ... v) { // ...
static void vaTest(int n, int ... v) { // ...
vaTest(1)
```