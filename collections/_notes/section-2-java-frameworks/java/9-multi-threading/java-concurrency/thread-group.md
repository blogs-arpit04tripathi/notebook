---
layout: post
title: ThreadGroup
permalink: /:collection/java/multithreading/thread-group
---


* Java provides a convenient way to group multiple threads in a single object. 
* In such way, we can suspend, resume or interrupt group of threads by a single method call. 
* For example, imagine a program in which one set of threads is used for printing a document, another set is used to display the document on the screen, and another set saves the document to a disk file. If printing is aborted, you will want an easy way to stop all threads related to printing. Thread groups offer this convenience.

| 							|Methods of ThreadGroup
---							|---
ThreadGroup(String name)	|creates a thread group with given name.
ThreadGroup(ThreadGroup parent,String name)	|creates a thread group with given parent group and name.
int activeCount()			|returns no. of threads running in current group.
int activeGroupCount()		|returns a no. of active group in this thread group.
void destroy()				|destroys this thread group and all its sub groups.
String getName()			|returns the name of this group.
ThreadGroup getParent()		|returns the parent of this group.
void interrupt()			|interrupts all threads of this group.
void list()					|prints information of this group to standard console.

* Java thread group is implemented by `java.lang.ThreadGroup` class.

```java
ThreadGroup tg1 = new ThreadGroup("Group A");
Thread t1 = new Thread(tg1, new MyRunnable(), "one");
Thread t2 = new Thread(tg1, new MyRunnable(), "two"); //MyRunnable implements Runnable interface
```
Now we can interrupt all threads by a single line of code only.  
`Thread.currentThread().getThreadGroup().interrupt();`

```java
public class ThreadGroupDemo implements Runnable {
    public void run() {
        System.out.println(Thread.currentThread().getName());
    }
    public static void main(String[] args) {
        ThreadGroupDemo runnable = new ThreadGroupDemo();
        ThreadGroup tg1 = new ThreadGroup("Parent ThreadGroup");
        Thread t1 = new Thread(tg1, runnable, "one");
        t1.start();
        Thread t2 = new Thread(tg1, runnable, "two");
        t2.start();
        Thread t3 = new Thread(tg1, runnable, "three");
        t3.start();
        System.out.println("Thread Group Name: " + tg1.getName());
        tg1.list();
    }
}

// Output :  
one two three Thread Group Name: Parent ThreadGroup
java.lang.ThreadGroup[name = Parent ThreadGroup, maxpri = 10]
Thread[one, 5, Parent ThreadGroup]
Thread[two, 5, Parent ThreadGroup]
Thread[three, 5, Parent ThreadGroup]
```

**What is Thread Group? Why it’s advised not to use it?**  
* ThreadGroup is a class which was intended to provide information about a thread group. ThreadGroup API is weak and it doesn’t have any functionality that is not provided by Thread. Two of the major feature it had are to get the list of active threads in a thread group and to set the uncaught exception handler for the thread. But Java 1.5 has added ***setUncaughtExceptionHandler*** (UncaughtExceptionHandler eh) method using which we can add uncaught exception handler to the thread. So ThreadGroup is obsolete and hence not advised to use anymore.

```java
t1.setUncaughtExceptionHandler(new UncaughtExceptionHandler() {
    @Override
    public void uncaughtException(Thread t, Throwable e) {
        System.out.println("exception occured:" + e.getMessage());
    }
});
```
