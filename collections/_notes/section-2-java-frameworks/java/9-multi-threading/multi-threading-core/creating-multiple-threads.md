---
layout: post
title: Creating Multiple Threads
permalink: /:collection/java/multithreading/creating-multiple-threads
---

```java
class NewThread implements Runnable {
    String name;
    Thread t;
    NewThread(String threadname) {
        name = threadname;
        t = new Thread(this, name);
        System.out.println("New thread: " + t);
        t.start();
    }
    @Override
    public void run() {
        try {
            for (int i = 3; i > 0; i--) {
                System.out.println(name + ": " + i);
                Thread.sleep(1000);
            }
        } catch (InterruptedException e) {
            System.out.println(name + "Interrupted");
        }
        System.out.println(name + " exiting.");
    }
}
```

```java
class MultiThreadDemo {
    public static void main(String args[]) {
        new NewThread("One");
        new NewThread("Two");
        new NewThread("Three");
        try {
            Thread.sleep(10000);
        } catch (InterruptedException e) {
            System.out.println("Main thread Interrupted");
        }
        System.out.println("Main thread exiting.");
    }
}
```

* If main thread finishes before a child thread has completed, then the Java run-time system may “hang”.
