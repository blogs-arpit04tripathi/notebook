---
layout: post
title: Synchronization
permalink: /:collection/java/multithreading/synchronization
---

- TOC
{:toc}

<hr><br>

* **Synchronization** - ensures that resource will be used by only one thread at a time.
* **Monitor** - an object used as a mutually exclusive lock. 
	- Every object has a lock associated with it. Only one thread can own a monitor at a given time.
	- thread acquires a lock; it has entered the monitor.
	- other threads will be waiting for the monitor ie. suspended until the first thread exits the monitor. 
	- thread owning a monitor can re-enter the same monitor if it so desires.
* Java’s messaging system allows a thread to enter a synchronized method on an object, and then wait there until some other thread explicitly notifies it to come out.

# Synchronized Methods
* To enter an object’s monitor, just call a method that has been modified with the synchronized keyword. 
* While a thread is inside a **synchronized** method, all other threads that try to call it (or any other synchronized method) on the same instance have to wait. 
* To exit the monitor and relinquish control of the object to the next waiting thread, the owner of the monitor simply returns from the synchronized method.
* In this program, nothing exists to stop all three threads from calling the same method, on the same object, at the same time. This is known as a **race condition**, because the three threads are racing each other to complete the method.
* Any time that you have a method, or group of methods, that manipulates the internal state of an object in a multithreaded situation, you should use the **synchronized keyword** to guard the state from race conditions.

```java
class Callme {
    synchronized void call(String msg) { ...} 
}
Output - [Hello][Synchronized][World]
```
* Once a thread enters any synchronized method on an instance, no other thread can enter any other synchronized method on the same instance. However, non-synchronized methods on that instance will continue to be callable.

# Synchronized Statement
* Suppose, you want to synchronize access to objects of a class that was not designed for multithreaded access or class was not created by you, but by a third party, and you do not have access to the source code. Thus, you can’t add **synchronized** to the appropriate methods within the class.
* A **synchronized block** ensures that a call to a synchronized method that is a member of objRef’s class occurs only after the current thread has successfully entered objRef’s monitor.

```java
synchronized(objRef) {
    objRef.call(msg); // statements to be synchronized
}
Current Output :  Hello[Synchronized[World] ] ]
```

# Static Synchronization
If you make any ***static method as synchronized***, the lock will be on the class not on object.

**Problem without static synchronization**
* Suppose there are two objects of a shared class (e.g. Table with static variable) named object1 and object2. In case of synchronized method and synchronized block there cannot be interference between t1 and t2 or t3 and t4 because t1 and t2 both refers to a common object that have a single lock. 
* But there can be interference between t1 and t3 or t2 and t4 because t1 acquires another lock and t3 acquires another lock. 
* When we want no interference between t1 and t3 or t2 and t4, Static synchronization can solve this problem.

![synchronized-statement]({{site.cdn}}/java/multi-threading/synchronized-statement.png)

# Which is more preferred – Synchronized method or Synchronized block?
- Synchronized block is more preferred way
- because it doesn’t lock the Object, synchronized methods lock the Object.
- if there are multiple synchronization blocks in the class, even though they are not related, it will stop them from execution and put them in wait state to get the lock on Object.

```java
class Program {
  public synchronized void f() { ......... }
}
// is equivalent to ...
class Program {
  public void f() {
     synchronized(this){ ... }
  }
}
```
```java
public class Program {
  private static Object locker1 = new Object();
  private static Object locker1 = new Object();
  public void doSomething1() {
    synchronized(locker1) {  ......... //do something protected; }
  }
  public void doSomething2() {
    synchronized(locker2) {  ......... //do something protected;  }
  }
}
```