---
layout: post
title: Object Oriented Programming (OOP)
permalink: /:collection/java/oop
---

```
PROGRAMMING PARADIGM :   Computer Program = code + data.
```

**Object-oriented vs Object-based programming language?**
* Object based programming language --> OOP except Inheritance.
* Example = JavaScript and VBScript.

![oop]({{site.cdn}}/java/oop-and-ood/oops-concept.jpg)

- **Class**
  - Templates for creating objects. (Logical Entity)
  - Define custom data types and methods.
- **Object**
  - Entity with state and behaviour.
  - Memory is allocated.
  - example: chair, pen, table etc. (physical or logical).
- **Inheritance**
  - Parent Child concept, child acquires properties and behaviour of parent object.
  - Used for runtime polymorphism.
- **Abstraction**
  - Concept of hiding internal details and describing in simple terms.
  - Achieved by encapsulation and inheritance.
- **Encapsulation**
  - Wrapping code and data into single unit just like a capsule.
  - access restriction to class members and methods.
  - Achieved by access-modifiers (private, protected, public).
- **Polymorphism**
  - Concept where an object behaves differently in different situations.
  - ***Compile time polymorphism***
    - Method overloading (same name but different arguments)
    - when we have `“IS-A” relationship` between objects.
    - Working in terms of superclass, actual implementation class decided at runtime.
  - ***Runtime polymorphism***
    - Method overriding or dynamic method dispatch (subclass override superclass method)
- **Association**
  - Defines the multiplicity between independent objects. (One-To-Many)
  - **Aggregation**
    - `HAS-A relationship` with ownership, employee has an address.
  - **Composition**
    - More restrictive form of aggregation, `HAS-A relationship` but can’t exist on its own.
    - Example - House has-a Room. Here room can’t exist without house.
