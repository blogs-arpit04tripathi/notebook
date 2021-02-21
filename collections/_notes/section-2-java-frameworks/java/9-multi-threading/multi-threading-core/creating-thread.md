---
layout: post
title: Creating a Thread
permalink: /:collection/java/multithreading/creating-thread
---

- TOC
{:toc}

<hr><br>

# Implementing Runnable
```java
Thread()
Thread(String name)
Thread(Runnable r)
Thread(Runnable threadOb, String threadName)
```
```java
class NewThread implements Runnable {
    Thread t;
    NewThread() {
        t = new Thread(this, "Demo Thread");
        System.out.println("Child thread: " + t);
        t.start();
    }
    // run method implemented as below
}
```
```java
public void run() {
    try {
        for (int i = 5; i > 0; i--) {
            System.out.println("Child Thread: " + i);
            Thread.sleep(500);
        }
    } catch (InterruptedException e) {
        System.out.println("Child interrupted.");
    }
    System.out.println("Exiting child thread.");
}
```

# Extending Thread
```java
class NewThread extends Thread {
    NewThread() {
        super("Demo Thread");
        System.out.println("Child thread: " + this);
        start();
    }
    // run method implemented as above
}
```
* The extending class must override the run( ), which is the entry point for the new thread. 
* It must also call start( ) to begin execution of the new thread. 
* start( ) executes a call to run( ).

```java
class ExtendThread {
    public static void main(String args[]) {
        Thread t = new NewThread();
        try {
            for (int i = 5; i > 0; i--) {
                System.out.println("Main Thread: " + i);
                Thread.sleep(1000);
            }
        } catch (InterruptedException e) {
            System.out.println("Main thread interrupted.");
        }
        System.out.println("Main thread exiting.");
    }
}
```

# Choosing an Approach
* Should be extended only when modified in some way. if not overriding Thread’s methods, implement Runnable. 
* By implementing **Runnable**, your thread class is free to inherit a different class.
