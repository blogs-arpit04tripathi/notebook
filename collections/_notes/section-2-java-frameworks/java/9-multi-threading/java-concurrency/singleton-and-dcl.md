---
layout: post
title: Singleton and DCL
permalink: /:collection/java/multithreading/singleton-and-dcl
---


> [Double Checked Locking on Singleton Class in Java]((https://javarevisited.blogspot.com/2014/05/double-checked-locking-on-singleton-in-java.html))

* One of the key challenge faced is how to keep Singleton class as Singleton i.e. how to prevent multiple instances of a Singleton due to whatever reasons.
* ***Double checked locking of Singleton*** is a way to ensure only one instance of Singleton class is created through application life cycle. As name suggests, in double checked locking, code checks for an existing instance of [Singleton class](https://javarevisited.blogspot.com/2013/03/difference-between-singleton-pattern-vs-static-class-java.html) twice with and without locking to double ensure that no more than one instance of singleton gets created. By the way, it was broken before Java fixed its memory models issues in JDK 1.5. 

![singleton]({{site.cdn}}/java/multi-threading/singleton.png)

```java
class Singleton {
    private volatile static Singleton _instance;
    private Singleton() {} // private constructor

    /*1st version: creates multiple instance if two thread access*/
    public static Singleton getInstance() {
        if (_instance == null) {
            _instance = new Singleton();
        }
        return _instance;
    }

    /*
    * 2nd version : only creates one instance of Singleton on concurrent environment
    * but unnecessarily expensive due to cost of synchronization at every call.
    */
    public static synchronized Singleton getInstanceTS() {
        if (_instance == null) {
            _instance = new Singleton();
        }
        return _instance;
    }

    /*
    * 3rd version : An implementation of double checked locking of Singleton.
    * Intention is to minimize cost of synchronization and improve performance,
    * by only locking critical section of code, the code which creates instance of Singleton class.
    * By the way this is still broken, if we don't make _instance volatile, as another thread can
    * see a half initialized instance of Singleton.
    */
    public static Singleton getInstanceDC() {
        if (_instance == null) { // Single Checked
            synchronized(Singleton.class) {
                if (_instance == null) { // Double checked
                    _instance = new Singleton();
                }
            }
        }
        return _instance;
    }
}
```

**Why you need Double checked Locking of Singleton Class?**  
* Though synchronized version is thread-safe and solves issue of multiple instance, it's not very efficient.
* cost of synchronization is there every time you call this method, but synchronization is only needed on first class, when Singleton instance is created.

**DCL was broken before Java 5**
* Prior to Java 5 double checked locking was broken due to memory model, but its fixed. 
* Now, with **happens-before guarantee**, all the write will happen on volatile _instance before any read of _instance variable, you can safely assume that this will work. 
* By the way this is not the best way to create thread-safe Singleton, you can use Enum as Singleton, which provides in-built thread-safety during instance creation. Another way is to use ***static holder pattern***.
* The DCL idiom was designed to support lazy initialization, which occurs when a class defers initialization of an owned object until it is actually needed.

**Why would you want to defer initialization?**  
* Perhaps creating a Resource is an expensive operation, and users of SomeClass might not actually call getResource() in any given run. In that case, you can avoid creating the Resource entirely. 
* Delaying some initialization operations until a user actually needs their results can help programs start up faster. 
* Unfortunately, synchronized methods run much slower -- as much as 100 times slower -- than ordinary unsynchronized methods. One of the motivations for lazy initialization is efficiency, but it appears that in order to achieve faster program startup, you have to accept slower execution time once the program starts. That doesn't sound like a great trade-off.
