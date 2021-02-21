---
layout: post
title: Inter-Thread Communication
permalink: /:collection/java/multithreading/inter-thread-communication
---

- TOC
{:toc}

<hr><br>

* Multithreading replaces event loop programming by dividing your tasks into discrete, logical units.
* Threads also provide a secondary benefit: they do away with polling. 
* Polling is usually implemented by a loop that is used to check some condition repeatedly. Once the condition is true, appropriate action is taken. This wastes CPU time. 

#  Example - Classic Queuing Problem 

* Here one thread is producing some data and another is consuming it. To make the problem more interesting, suppose that the producer has to wait until the consumer is finished before it generates more data. 
* To avoid polling, Java includes an elegant interprocess communication mechanism via the **wait( ), notify( ), and notifyAll( )** methods. These methods are implemented as **final** methods in **Object**, so all classes have them. 
* All three methods can be called only from within a **synchronized** context.
    - **wait( )** tells the calling thread to give up the monitor and go to sleep until some other thread enters the same monitor and calls **notify( )** or **notifyAll( )**.
    - **notify( )** wakes up a thread that called **wait( )** on the same object.
    - **notifyAll( )** wakes up all the threads that called **wait( )** on the same object. One of the threads will be granted access.

```java
final void wait( ) throws InterruptedException    
final void notify( )    
final void notify All( )
```

* Although **wait( )** normally waits until **notify( ) or notifyAll( )** is called, there is a possibility that in very rare cases the waiting thread could be awakened due to a ***spurious wakeup***. In this case, a waiting thread resumes without notify( ) or notifyAll( ) having been called. (In essence, the thread resumes for no apparent reason.)
* Because of this remote possibility, Oracle recommends that calls to wait( ) should take place within a loop that checks the condition on which the thread is waiting.

# Correct Implementation of a Producer and Consumer problem

```java
class Q {
    int n;
    boolean valueSet = false;

    //syncronized get method on q
    synchronized int get() {
        while (!valueSet) {
            try {
                wait();
            } catch (InterruptedException e) {
                System.out.println("InterruptedException caught");
            }
        }
        System.out.println("Got: " + n);
        valueSet = false;
        notify();
        return n;
    }

    //syncronized put method on q
    synchronized void put(int n) {
        while (valueSet) {
            try {
                wait();
            } catch (InterruptedException e) {
                System.out.println("InterruptedException caught");
            }
        }
        this.n = n;
        valueSet = true;
        System.out.println("Put: " + n);
        notify();
    }
}
```
```java
class Producer implements Runnable {
    Q q;
    Producer(Q q) {
        this.q = q;
        new Thread(this, "Producer").start();
    }
    public void run() {
        int i = 0;
        while (true) {
            q.put(i++);
        }
    }
}
```
```java
class Consumer implements Runnable {
    Q q;
    Consumer(Q q) {
        this.q = q;
        new Thread(this, "Consumer").start();
    }
    public void run() {
        while (true) {
            q.get();
        }
    }
}
```
```java
class PCFixed {
    public static void main(String args[]) {
        Q q = new Q();
        new Producer(q);
        new Consumer(q);
        System.out.println("Press Control-C to stop.");
    }
}
```
