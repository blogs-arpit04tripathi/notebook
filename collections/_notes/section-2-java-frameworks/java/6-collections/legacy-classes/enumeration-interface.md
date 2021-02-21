---
layout: post
title: Enumeration Interface
permalink: /:collection/java/collections/enumeration-interface
---

* To enumerate (obtain one at a time) the elements in a collection of objects. 
* Used with Legacy classes (Vector, Properties) and several other API classes.
* throws **NoSuchElementException** when enumeration is complete.

```java
boolean hasMoreElements()
E nextElement()
```
