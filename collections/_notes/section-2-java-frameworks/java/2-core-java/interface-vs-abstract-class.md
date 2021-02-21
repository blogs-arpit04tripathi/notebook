---
layout: post
title: Abstract Class vs Interface
permalink: /:collection/java/interface-vs-abstract-class
---

|Interface|Abstract Class|
---|---
Variables - public static final.|Variables - private, protected etc.
Can’t store state|Can store state
methods - public or public static|methods – can be private and protected too
establishes relation for unrelated classes.|establishes relation for interrelated objects.
Use interfaces when full implementation required i.e. to define the role that classes can play, regardless of their position in the inheritance tree.|when you want partial pieces for your design (for reusability) i.e. a template for a group of sub-classes, with some implementation code.
implements keyword – multiple|extends keyword - only one
set of methods without concrete implementations.|Subclasses provide implementations, or become  abstract.
provides IS-A relationship.|purpose is to provide superclass that can be inherited to share a common design.
Example-Comparable or Cloneable.|Example- AbstractMap ==> HashMap, TreeMap, ConcurrentHashMap (Methods - get, put, isEmpty, containsKey, containsValue)