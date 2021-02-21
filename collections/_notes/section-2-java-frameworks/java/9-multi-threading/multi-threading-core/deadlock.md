---
layout: post
title: Deadlock
permalink: /:collection/java/multithreading/deadlock
---

* **Deadlock** occurs when two threads have a circular dependency on a pair of synchronized objects.
* For example, suppose one thread enters the monitor on object X and another thread enters the monitor on object Y. If the thread in X tries to call any synchronized method on Y, it will block as expected. However, if the thread in Y, in turn, tries to call any synchronized method on X, the thread waits forever, because to access X, it would have to release its own lock on Y so that the first thread could complete.
* Deadlock is a difficult error to debug for two reasons:
	- In general, it occurs only rarely, when the two threads time-slice in just the right way.
	- It may involve more than two threads and two synchronized objects.

![deadlock]({{site.cdn}}/java/multi-threading/deadlock.png)

```java
// An example of deadlock.
class A {
    synchronized void foo(B b) {
        String name = Thread.currentThread().getName();
        System.out.println(name + " entered A.foo");
        try {
            Thread.sleep(1000);
        } catch (Exception e) {
            System.out.println("A Interrupted");
        }
        System.out.println(name + " trying to call B.last()");
        b.last();
    }
    synchronized void last() {
        Sysout("Inside A.last");
    }
}
```
```java
class B {
    synchronized void bar(A a) {
        String name = Thread.currentThread().getName();
        System.out.println(name + " entered B.bar");
        try {
            Thread.sleep(1000);
        } catch (Exception e) {
            Sysout("B Interrupted");
        }
        System.out.println(name + " trying to call A.last()");
        a.last();
    }
    synchronized void last() {
        Sysout("Inside B.last");
    }
}
```
```java
class Deadlock implements Runnable {
    A a = new A();
    B b = new B();
    Deadlock() {
        Thread.currentThread().setName("MainThread");
        Thread t = new Thread(this, "RacingThread");
        t.start();
        a.foo(b); // get lock on A in this thread.
        System.out.println("Back in main thread");
    }
    public void run() {
        b.bar(a); // get lock on B in other thread.
        System.out.println("Back in other thread");
    }
    public static void main(String args[]) {
        new Deadlock();
    }
}
```
```java
// Output
MainThread entered A.foo
RacingThread entered B.bar
MainThread trying to call B.last()
RacingThread trying to call A.last()
```

Because the program has deadlocked, you need to press ctrl-c to end the program. You can see a full thread and monitor cache dump by pressing ctrl-break on a PC. You will see that ***RacingThread*** owns the monitor on b, while it is waiting for the monitor on a. At the same time, ***MainThread*** owns a and is waiting to get b. This program will never complete. As this example illustrates, if your multithreaded program locks up occasionally, deadlock is one of the first conditions that you should check for.
