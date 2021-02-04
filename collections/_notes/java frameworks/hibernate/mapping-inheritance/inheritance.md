---
layout: post
title: Mapping Inheritance Hierarchies
permalink: /hibernate/inheritance
---

Hibernate supports the three basic inheritance mapping strategies:
-	table per class hierarchy
-	table per subclass
-	table per concrete class

In addition, Hibernate supports a fourth, slightly different kind of polymorphism:
-	implicit polymorphism

Feature of OOP, no equivalent in Relational Model.

![](https://github.com/arpit04tripathi/files-cdn/raw/cdn/hibernate/mapping-inheritance.png)

Use hibernate implementation of inheritance of when strong implementation of inheritance is used like polymorphism, dynamic assignment of objects.

```
InheritanceType.SINGLE_TABLE
InheritanceType.TABLE_PER_CLASS
InheritanceType.JOINED
```
