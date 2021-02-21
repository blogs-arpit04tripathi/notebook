---
layout: post
title: Java Enum and Singleton Pattern
permalink: /:collection/java/multithreading/enum-singleton
---


* Below four things ensure that no instances of an enum type exist beyond those defined by the enum constants.
	1. An enum type has no instances other than those defined by its enum constants. 
	2. It is a compile-time error to attempt to explicitly instantiate an enum type. 
	3. The final clone method in Enum ensures that enum constants can never be cloned, and the special treatment by the serialization mechanism ensures that duplicate instances are never created as a result of deserialization. 
	4. Reflective instantiation of enum types is prohibited.

* Enum Singletons are easy to write
* By default, creation of Enum instance is thread safe but any other method on Enum is programmers responsibility.

```java
/*Singleton pattern example using Java Enum*/
public enum EasySingleton {
    INSTANCE("Sunday Funday", true);

    private String daysGreeting;
    private boolean isWeekend;
    WeekDays(String daysGreeting, boolean isW) {
        this(daysGreeting);
        this.isWeekend = isWeekend;
    }
}
```
```java
/*Singleton pattern example with static factory method*/
public class Singleton {
    //initailzed during class loading
    private static final Singleton INSTANCE = new Singleton();
    private Singleton() {} // private constructor, no other instance 
    public static Singleton getSingleton() {
        return INSTANCE;
    }
}
```
```java
/* Singleton pattern example with Double checked Locking*/
public class DoubleCheckedLockingSingleton{
     private volatile DoubleCheckedLockingSingleton INSTANCE;
     private DoubleCheckedLockingSingleton(){}
     public DoubleCheckedLockingSingleton getInstance(){
         if(INSTANCE == null){
            synchronized(DoubleCheckedLockingSingleton.class){  //double checking Singleton instance
                if(INSTANCE == null){ INSTANCE = new DoubleCheckedLockingSingleton(); }
            }
         }
         return INSTANCE;
     }
}
```

* ***Enum Singletons handled Serialization by themselves***
* Another problem with conventional Singletons are that once you implement [serializable interface](https://javarevisited.blogspot.com/2011/04/top-10-java-serialization-interview.html) they are no longer remain Singleton because readObject() method always return a new instance just like constructor in Java. you can avoid that by using readResolve() method and discarding newly created instance by replacing with Singeton as shwon in below example. 
* This can become even more complex if your Singleton Class maintains state, as you need to make them [transient](https://javarevisited.blogspot.com/2012/03/difference-between-transient-and.html), but with **Enum Singleton**, Serialization is guarnateed by JVM. 

```java
//readResolve to prevent another instance of Singleton
private Object readResolve() {
    return INSTANCE;
}
```

* **Creation of Enum instance is thread-safe**
	- Since creation of Enum instance is thread-safe by default you don't need to worry about double checked locking.
	- In summary, given the ***Serialzation and thraead-safety guaranteed*** and with couple of line of code enum Singleton pattern is best way to create Singleton in Java 5 world.
