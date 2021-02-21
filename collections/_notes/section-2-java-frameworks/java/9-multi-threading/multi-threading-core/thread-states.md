---
layout: post
title: Thread’s State
permalink: /:collection/java/multithreading/thread-states
---

**Thread.State** - indicates the state of the thread at the time at which the call was made (enumeration defined by Thread) 

```java
Thread.State ts = thrd.getState();
if(ts == Thread.State.RUNNABLE) // ...
```

|Value|State|
---|---
BLOCKED|A thread that has suspended execution because it is waiting to acquire a lock.
NEW |A thread that has not begun execution.
RUNNABLE |A thread that either is currently executing or will execute when it gains access to CPU.
TERMINATED |A thread that has completed execution.
TIMED_WAITING |A thread that has suspended execution for a specified period of time, such as after sleep().<br>This state is also entered when a timeout version of wait() or join() is called.
WAITING 	|A thread that has suspended execution because it is waiting for some action to occur.<br>For example, it is waiting because of a call to a non-timeout version of wait() or join().

* A thread’s state may change after the call to **getState( )**. Thus, getState( ) is not intended to provide a means of synchronizing threads. It’s used for debugging or for profiling a thread’s run-time characteristics.

![thread-states]({{site.cdn}}/java/multi-threading/thread-states.png)

* The key to utilizing Java’s multithreading features effectively is to think concurrently rather than serially. 
* For example, when you have two subsystems within a program that can execute concurrently, make them individual threads. With the careful use of multithreading, you can create very efficient programs. 
* If you create too many threads, more CPU time will be spent in context switching than executing your program!
* Thread scheduler in java is the part of the JVM that decides which thread should run. There is no guarantee that which runnable thread will be chosen to run by the **thread scheduler**. Only one thread at a time can run in a single process. 
* The thread scheduler mainly uses preemptive or time slicing scheduling to schedule the threads.
* **start()** method of Thread class is used to start a newly created thread. It performs following tasks:
	- A new thread starts (with new callstack).
	- The thread moves from New state to the Runnable state.
	- When the thread gets a chance to execute, its target run() method will run.

**Difference between preemptive scheduling and time slicing?**  
- Under **preemptive** scheduling, the highest priority task executes until it enters the waiting or dead states or a higher priority task comes into existence.
- Under **time slicing**, a task executes for a predefined slice of time and then re-enters the pool of ready tasks. The scheduler then determines which task should execute next, based on priority and other factors.

**Can we start a thread twice?**  
- No. After starting a thread, it can never be started again.
- If you does so, an **IllegalThreadStateException** is thrown. In such case, thread will run once but for second time, it will throw exception.

**What if we call run() method directly instead start() method?**  
- Each thread starts in a separate call stack.
- Invoking the run() method from main thread, the run() method goes onto the current call stack rather than at the beginning of a new call stack.

```java
public static void main(String args[]) {
    TestCallRun2 t1 = new TestCallRun2();
    TestCallRun2 t2 = new TestCallRun2();
    t1.run();
    t2.run();
}

class TestCallRun2 extends Thread {
    public void run() {
        for (int i = 1; i < 5; i++) {
            try {
                Thread.sleep(500);
            } catch (InterruptedException e) {
                sysout(e);
            }
            System.out.println(i);
        }
    }
}
```
```
Output:1 2 3 4 5 1 2 3 4 5
```
As you can see that there is no context-switching because here t1 and t2 will be treated as normal object not thread object.
