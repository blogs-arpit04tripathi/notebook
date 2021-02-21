---
layout: post
title: Understanding the process
permalink: /:collection/java/multithreading/understanding-the-process
---


![thread-states-flow]({{site.cdn}}/java/multi-threading/thread-states-flow.png)

* The point to point explanation of the above diagram is as follows:
	- Threads enter to acquire lock.
	- Lock is acquired by on thread.
	- Now thread goes to waiting state if you call wait() on the object. Otherwise it releases the lock and exits.
	- If you call notify() or notifyAll() method, thread moves to the notified state (runnable state).
	- Now thread is available to acquire lock.
	- After completion of the task, thread releases the lock and exits the monitor state of the object.

|wait()	|sleep()|
---|---
wait() method releases the lock |sleep() method doesn't release the lock.
method of Object class	|method of Thread class
non-static method	|static method
Should be notified by notify() or notifyAll() methods |After the specified amount of time, sleep is completed.

**Why wait(), notify() and notifyAll() methods are defined in Object class not Thread class?**  
- In Java every Object has a monitor
- wait, notify methods are used to wait for the Object monitor or to notify other threads that Object monitor is free now. 
- There is no monitor on threads in java and synchronization can be used with any Object, that’s why it’s part of Object class so that every class in java has these essential methods for inter thread communication.

**Why wait(), notify() and notifyAll() methods have to be called from synchronized method or block?**  
To call these methods monitor on the Object must be acquired, that can be achieved only by synchronization, they need to be called from synchronized method or block.
