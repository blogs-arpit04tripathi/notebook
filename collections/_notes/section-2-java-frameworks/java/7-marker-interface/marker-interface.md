---
layout: post
title: Marker Interface
permalink: /:collection/java/marker-interface
---

* Empty interfaces used to mark or identify a special operation.

# Java Marker Interfaces
1. **Serializable interface (java.io.Serializable)**
   - makes classes eligible for Serialization and Deserialization.
   - **NotSerializableException** – Attempt to serialize an object of a class not implementing Serializable interface.
2. **Cloneable interface**
   - clone() method of Object class may be called. 
   - **CloneNotSupportedException** - clone() Invocation on a non Cloneable interface.

3. **RandomAccess interface**
   - Used by List implementations to indicate that they support fast (generally constant time) random access.
4. **Remote interface**
   - Identify interfaces whose methods may be invoked from a non-local virtual machine.

# Custom Marker Interface
How to Create Our Own Marker Interface? - by creating a blank interface.

```java
public interface MyMarkerInterface {}
public class MyMarkedClass implements MyMarkerInterface {}
public myMethod(MyMarkerInterface x) {}
if (obj instanceof MyMarkerInterface ) {
	// do something
}
```
