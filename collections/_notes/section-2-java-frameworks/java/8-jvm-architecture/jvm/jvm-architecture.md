---
layout: post
title: JVM - Java Virtual Machine
permalink: /:collection/java/jvm/architecture
---

> TODO : Read full article [here](#).

![jvm-architecture]({{site.cdn}}/java/jvm-architecture/jvm-architecture.png "jvm-architecture")

|JVM Components				|		|
|---						|---	|
|Classloader				|used to load class files.|
|Class (Method) Area		|stores per-class structure. (runtime constant pool, field and method data, code for methods)|
|Heap						|runtime data area where objects are allocated.|
|Stack						|stores call frames (local variables, partial results, method invocation and return).|
|Program Counter Register	|PC (program counter) register, Address of JVM instruction currently being executed.|
|Native Method Stack		|contains all the native methods used in the application|
|Execution Engine			|A virtual processor<br>Interpreter: Read bytecode stream then execute the instructions.<br>Just-In-Time (JIT) compiler|
