---
layout: post
title: Object Oriented Design (OOD)
permalink: /:collection/java/ood
---

- TOC
{:toc}

<hr><br>

# OOD (Object Oriented Design)

Process of planning a system of interacting objects for the purpose of solving a software problem.

1. Gather Requirements – could Do vs Must Do
2. Describe the App – Use Case vs User Story
3. Identify the main objects
4. Describe the interactions – Behavior, sequence diagram
5. Create class diagram

* Using design patterns to solve common problems is the best practice.
    - *Observer* – change in one object leads to change in many other objects
    - *Memento* – object changed by a lot of other objects and now you want to undo last changes.
* **User Story** - As a (type of user) I want (goal) so that (reason)
* **Use Case** - Title > actor > steps > preconditions > outcome

# FURPS+

> [Read Article on FURPS+](https://www.ibm.com/developerworks/rational/library/3975.html){:target="_blank"}

- Functional Requirement
- Usability Requirements
- Reliability – Disaster Recovery
- Performance
- Supportability
- Design
- Implementation
- Interface
- Physical

# Object Oriented Design Principles
> Read full article on [OOP Design Principles](https://javarevisited.blogspot.com/2018/07/10-object-oriented-design-principles.html){:target="_blank"}

## DRY (Don't repeat yourself)
- Use Abstraction to abstract common things in one place.
- extract method - if using same code block in more than two places.
- public final constant - if using hard-coded value more than once.

## Delegation principles

* Don't do all stuff by yourself,  delegate it to the respective class.
* Example - [equals() and hashCode() method in Java](http://javarevisited.blogspot.com/2011/02/how-to-write-equals-method-in-java.html).
  * To compare two objects for equality, we ask the class itself to do comparison instead of Client class doing that check.
  * The key benefit of this design principle is no duplication of code and pretty easy to modify behavior.

## KISS
* “Keep It Simple, Stupid”.

## YAGNI
* “You Ain’t Gonna Need It”. 
* `If you run into a situation where you are asking yourself, “What about adding extra (feature, code, …etc.) 

## Encapsulate What Changes
* encapsulate the code you expect or suspect to be changed in future.
* It's easy to test and maintain proper encapsulated code.
* Making variable and methods private by default and increase access step by step e.g. from private to protected and not public.
* Example - Factory design pattern encapsulates object creation code and provides flexibility to introduce a new product later with no impact on existing code.

## Favor Composition over Inheritance

* Always favor composition over inheritance, if possible. Some of you may argue this, but I found that 
* Composition is a lot more flexible than Inheritance.
* Composition allows changing the behavior of a class at run-time by setting property during run-time and by using Interfaces to compose a class.
  * We use polymorphism which provides flexibility to replace with better implementation any time.

![composition-vs-inheritance]({{site.cdn}}/java/oop-and-ood/composition-vs-inheritance.png)

## Programming for Interface not implementation

* Always ***program for the interface and not for implementation*** this will lead to flexible code which can work with any new implementation of the interface.
* So use interface type on variables, return types of method or argument type of methods in Java.

![intercepting-filter-pattern]({{site.cdn}}/java/oop-and-ood/intercepting-filter-pattern.png)
![intercepting-filter-pattern-class-diagram]({{site.cdn}}/java/oop-and-ood/intercepting-filter-pattern-class-diagram.png)