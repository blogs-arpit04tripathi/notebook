---
layout: post
title: Using isAlive( ) and join( )
permalink: /:collection/java/multithreading/isAlive-join
---


* Two ways exist to determine whether a thread has finished. 
	- **isAlive()** on thread, **true** if still running. but it is occasionally useful. 
	- **join()** - Currently running threads stop executing until the thread it joins with completes its task.

```java
final void join( ) throws InterruptedException
final public void join(long milliseconds) throws InterruptedException
```
```java
class DemoJoin {
 public static void main(String args[]) { 
    NewThread ob1 = new NewThread("One");
    NewThread ob2 = new NewThread("Two");
    NewThread ob3 = new NewThread("Three");
    System.out.println("Thread One is alive: "+ ob1.t.isAlive());
    System.out.println("Thread Two is alive: "+ ob2.t.isAlive());
    System.out.println("Thread Three is alive: "+ ob3.t.isAlive());
    try {
           System.out.println("Waiting for threads to finish.");
           ob1.t.join(); ob2.t.join(); ob3.t.join();
     } catch (InterruptedException e) {
           System.out.println("Main thread Interrupted");
     }
     System.out.println("Thread One is alive: "+ ob1.t.isAlive());
     System.out.println("Thread Two is alive: "+ ob2.t.isAlive());
     System.out.println("Thread Three is alive: "+ ob3.t.isAlive());
     System.out.println("Main thread exiting.");
  }
}
```
```
// Output
New thread: Thread[One,5,main]
New thread: Thread[Two,5,main]
New thread: Thread[Three,5,main]
Thread One is alive: true
Thread Two is alive: true
Thread Three is alive: true
Waiting for threads to finish.
One: 2
Two: 2
Three: 2
One: 1
Two: 1
Three: 1
Two exiting.
Three exiting. 
One exiting.
Thread One is alive: false
Thread Two is alive: false
Thread Three is alive: false
Main thread exiting
```
