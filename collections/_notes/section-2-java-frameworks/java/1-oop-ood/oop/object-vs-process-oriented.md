---
layout: post
title: Object-oriented vs Process-oriented
permalink: /:collection/java/object-vs-process-oriented
---

|Object-oriented programming|Process-oriented model|
|---|---|
|Program around “who is being affected” (data).|Program around “what is happening” (code).|
|Data controlling access to code.|Characterizes program as a series of linear steps (code).|
|easier development and maintenance|Problems when programs grow larger and more complex.|
|can simulate real-world event more effectively.|Such emulation not easy.|
|Eg. Java, .Net etc.|Procedural languages such as C (code acting on data)|


# Why Java is not a purely Object-Oriented Language?
No, Java is not purely Object Oriented due to following points :
- ***static keyword*** :  When we declare a class as static then it can be used without the use of an object in Java.
- **Primitive Data Type** : Even wrapper uses primitives for operations via autoboxing and unboxing.

Pure Object-Oriented Language has *strictly* all of the following features :
- Abstraction
- Encapsulation/Data Hiding
- Inheritance
- Polymorphism
- All predefined types are objects
- All user defined types are objects
- All operations on objects by exposed methods only.
