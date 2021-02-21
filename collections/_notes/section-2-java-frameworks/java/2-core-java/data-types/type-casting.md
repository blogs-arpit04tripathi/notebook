---
layout: post
title: Type Casting
permalink: /:collection/java/type-casting
---


* compatible types, implicit conversion, assign int value to a long variable. (***widening***)
* incompatible types, use a cast for explicit conversion between incompatible types. (***narrowing***)

# Automatic Type Promotion in expression
```java
byte b = 50;
b = b * 2; // Error! Cannot assign an int to a byte!
b = (byte) b * 2;
double result=(f*b)+(i/c)-(d*s);
```

- boolean --> int
- byte --> int
- char --> int
- short --> int
- int --> int
- long --> long
- float --> float
- double --> double
- reference --> reference
- returnAddress --> returnAddress