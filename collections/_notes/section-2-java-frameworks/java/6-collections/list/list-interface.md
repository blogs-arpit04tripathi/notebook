---
layout: post
title: List Interface
permalink: /:collection/java/collections/list-interface
---

* Duplicate elements are allowed.
* zero-based index.
* You can modify each element by using **replaceAll()**. (UnaryOperator is a functional interface added by JDK 8.)

```java
Collections.replaceAll(a1, "saran", "SARANYA");
```

* As a general rule, the collection classes are not synchronized, but it is possible to obtain synchronized versions.
* Several legacy classes, such as Vector, Stack, and Hashtable, have been re-engineered to support collections.
* **RandomAccess** interface contains no members, tells about support to efficient random access to its elements. 
* Although a collection might support random access, it might not do so efficiently.
* **Random Access classes** - ArrayList, HashMap, TreeMap, Hashtable