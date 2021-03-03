---
layout: post
title: Constructors
permalink: /:collection/java/constructors
---

* Constructors has no return type, not even **void**, because implicit return type is the class type itself.
* default constructor initializes all instance variables to their default values. (0, null, false).

**Why Java Static Constructor is not allowed?**
- ***Static Belongs to Class, Constructor to Object.***
  - Constructor is not class property, it makes sense that it’s not allowed to be static.
- ***Static Block/Method can’t access non-static variables***
  - while constructors are used to initialize instance variables.
  - this - Cannot use this in a static context.
- ***Static Constructor will break inheritance***
  - In java class hierarchy, subclass constructor calls superclass constructor using super() method (JVM calls implicitly).
  - super() method, it’s not static. So if the constructor becomes static, we won’t be able to use it and that will break inheritance in java.

**Java Static Constructor Alternative**
- To initialize some static variables in the class, you can use static block.
- We can’t pass arguments to the static block, so if you want to initialize static variables then you can do that in the normal constructor too.

