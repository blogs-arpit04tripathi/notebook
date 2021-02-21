---
layout: post
title: ContextService API
permalink: /:collection/java/multithreading/contextService-api
---


- **Contextual object** - any Java object or instance which will have the particular application component's container context associated with it. 
- **Contextual task** - a task submitted to the managed resource.
- When a task instance is submitted to a managed instance of the ExecutorService then the task becomes a contextual task.
- ContextService API allow applications to create contextual objects without a managed executor.
- It gives you a way to capture that context information, store it, so that you can run it at a later point in time. 
- And how does it do that? It uses these ***dynamic proxy capabilities*** that are provided under the java.lang.reflect package to associate the application component's context with the object instance. So this object now becomes a contextual object and whenever a method on the contextual object runs then the method executes with the thread context of that associated application component instance.
- when you talk about ContextService it helps you to create contextual objects, which means these contextual objects will have the context information. And what is that? That's JNDI naming, class loader information, and security context. 

```java
@Override
public void run() {
    system.out.println("Thread" + Thread.currentThread().getName());
    Subject subject = Subject.getSubject(AccessController.getContext());
    system.out.println("Security information from a normal thread: " + subject);
    // uses stored contextual info here
}
```
```java
Runnable proxy = contextService.createContextualProxy(runnable, Runnable.class); // contextual info captured for future use
Thread thread = new Thread(proxy);
thread.start();
```
