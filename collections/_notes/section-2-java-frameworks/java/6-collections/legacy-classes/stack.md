---
layout: post
title: Stack
permalink: /:collection/java/collections/stack
---

* **Stack** is a subclass of **Vector** that implements a standard last-in, first-out stack. 
* **EmptyStackException** is thrown in case of stack underflow. 
* Stack includes all the methods defined by Vector and adds several of its own.
* One other point: although Stack is not deprecated, **ArrayDeque** is a better choice.

|Methods|||||
---|---|---|---|---
boolean empty( )|E pop( )|E peek( )|E push(E element)|int search(Object element)
