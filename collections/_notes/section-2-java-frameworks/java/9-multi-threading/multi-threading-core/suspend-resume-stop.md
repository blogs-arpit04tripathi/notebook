---
layout: post
title: Suspending, Resuming, and Stopping Threads
permalink: /:collection/java/multithreading/suspend-resume-stop
---


* Sometimes, suspending execution of a thread is useful. 
* For example, a separate thread can be used to display the time of day, when not required, then its thread can be suspended.
* Prior to Java 2, a program used **suspend( )**, **resume( )**, and **stop( )**, which are methods defined by **Thread**, to pause, restart, and stop the execution of a thread. These are **deprecated** now.
	- **suspend( )** can sometimes cause serious system failures as locks are not relinquished.
	- **resume( )** method is also deprecated. As it cannot be used without the **suspend( )**.
	- **stop( )** can sometimes cause serious system failures. Assume that a thread is writing to a critically important data structure and has completed only part of its changes. If that thread is stopped at that point, that data structure might be left in a corrupted state. The trouble is that **stop( )** causes any lock the calling thread holds to be released. Thus, the corrupted data might be used by another thread that is waiting on the same lock.
* A thread must be designed so that the **run( )** method periodically checks to determine whether that thread should suspend, resume, or stop its own execution. Typically, this is accomplished by establishing a flag variable that indicates the execution state of the thread. As long as this flag is set to “running,” the **run( )** method must continue to let the thread execute. If this variable is set to “suspend,” the thread must pause. If it is set to “***stop***”, the thread must terminate.

```java
// Suspending and resuming a thread 
class NewThread implements Runnable {
    String name; // name of thread
    Thread t;
    boolean flag;

    NewThread(String threadname) {
        name = threadname;
        t = new Thread(this, name);
        System.out.println("New thread: " + t);
        flag = false;
        t.start(); // Start the thread
    }

    public void run() {
        try {
            for (int i = 15; i > 0; i--) {
                System.out.println(name + ": " + i);
                Thread.sleep(200);
                synchronized(this) {
                    while (suspendFlag) {
                        wait();
                    }
                }
            }
        } catch (InterruptedException e) {
            System.out.println(name + " interrupted.");
        }
        System.out.println(name + " exiting.");
    }
    synchronized void mysuspend() {
        flag = true;
    }
    synchronized void myresume() {
        flag = false;
        notify();
    }
}
```
```java
class SuspendResume {
    public static void main(String args[]) {
        NewThread ob1 = new NewThread("One");
        NewThread ob2 = new NewThread("Two");
        try {
            Thread.sleep(1000);
            ob1.mysuspend();
            System.out.println("Suspending thread One");
            Thread.sleep(1000);
            ob1.myresume();
            System.out.println("Resuming thread One");
            ob2.mysuspend();
            System.out.println("Suspending thread Two");
            Thread.sleep(1000);
            ob2.myresume();
            System.out.println("Resuming thread Two");
        } catch (InterruptedException e) {
            System.out.println("Main thread Interrupted");
        }

        try { // wait for threads to finish
            System.out.println("Waiting for threads to finish.");
            ob1.t.join();
            ob2.t.join();
        } catch (InterruptedException e) {
            System.out.println("Main thread Interrupted");
        }
        System.out.println("Main thread exiting.");
    }
}
```
