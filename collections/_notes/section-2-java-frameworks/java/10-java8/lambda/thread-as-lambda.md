---
layout: post
title: Thread as Lambda
permalink: /:collection/java/java8/thread-as-lambda
---

```java
// new Thread - anonymous class (inline class)
Thread th = new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("Running new thread");
    }
});

// new Thread as Lambda, Runnable is also Functional Interface
th = new Thread(() - > System.out.println("Running in new thread"));
th.start();
System.out.println("Main thread running");
```
