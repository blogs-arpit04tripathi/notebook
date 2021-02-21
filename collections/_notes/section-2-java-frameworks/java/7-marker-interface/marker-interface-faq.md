---
layout: post
title: Marker Interface FAQ
permalink: /:collection/java/marker-interface/faq
---

**Q. What are the Problems with Marker Interfaces?**
* When a class implements them, all of its **subclass by default inherits it**.
* In below example, class B inheritably behaves as Serializable, ***can not remove or unimplement*** Serializable from it.
* Need to handle such exceptional cases by ***throwing exceptions from child classes***.

```java
class A implements Serializable{}        
class B extends A {}
```

**Q. Can't We Achieve the Same Behaviour with Annotations?**
* Yes, they're much more flexible as Annotations can have parameters of various kinds.
* Most of the thing that can be done with marker interfaces can be done with annotations.
* *Drawbacks of Annotations*
	- To check **instanceof** with annotation have high runtime as it requires Java reflection calls.
	- Cannot be used to define types as opposed to in case of Marker interfaces.

```java
public void writeToFile(Serializable object);
```

**Q. Is runnable a Marker interface?**
- ***No***, it has run method declared.

**Q. Difference between serializable and externalizable interface?**
- Serializable is a marker interface whereas externalizable is not.
