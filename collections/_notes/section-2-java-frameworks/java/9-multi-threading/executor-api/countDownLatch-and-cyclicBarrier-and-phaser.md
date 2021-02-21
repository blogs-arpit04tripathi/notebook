---
layout: post
title: CountDownLatch and CyclicBarrier and Phaser
permalink: /:collection/java/multithreading/countDownLatch-and-cyclicBarrier-and-phaser
---

- TOC
{:toc}

<hr><br>


![mutual-exclusion]({{site.cdn}}/java/multi-threading/mutual-exclusion.png)

![countdownLatch-cyclicBarrier-phaser]({{site.cdn}}/java/multi-threading/countdownLatch-cyclicBarrier-phaser.png)

# CountDown Latch

- Latch that is released only after the given number of events occur; count given on initialization. 
- Each time one of those events occur count is decremented, for that **countdown()** method is used. 
- Thread(s) that are waiting for the latch to release (count zero) are blocked using **await()** method.
- It is useful in the scenario when you want one or more threads to wait until one or more events being performed in other threads complete.

**For, new CountDownLatch(N). Do we need to have 3 threads madatorily?**  
No, thread can wait until N threads complete some action, or that action has been completed N times.

![countdown-latch]({{site.cdn}}/java/multi-threading/countdownLatch.png)

```java
public class CountdownlatchDemo {
    public static void main(String[] args) {
        CountDownLatch cdl = new CountDownLatch(3);
        // Initializing three threads to read 3 different files.
        Thread t1 = new Thread(new FileReader("thread-1", "file-1", cdl));
        Thread t2 = new Thread(new FileReader("thread-2", "file-2", cdl));
        Thread t3 = new Thread(new FileReader("thread-3", "file-3", cdl));
        t1.start();
        t2.start();
        t3.start();
        try {
            // main thread waiting till all the files are read
            cdl.await();
        } catch (InterruptedException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
        System.out.println("Files are read ... Start further processing");
    }
}
```
```java
class FileReader implements Runnable {
    private String threadName;
    private String fileName;
    private CountDownLatch cdl;
    FileReader(String threadName, String fileName, CountDownLatch cdl){
        this.threadName = threadName;
        this.fileName = fileName;
        this.cdl = cdl;        
    }
    @Override
    public void run() {
        System.out.println("Reading file " + fileName + " thread " + threadName);
        // do countdown here
        cdl.countDown();
    } 
}
```

# Cyclic Barrier

- Used when you need threads to wait for each other to reach a common barrier point.
- After reaching barrier point, thread calls await() on the CyclicBarrier object and gets itself suspended.
- Once all specified threads have called await(), it will trip the barrier and all threads can resume operation.
- The barrier is called cyclic because it can be re-used after the waiting threads are released.

```java
public int await(long timeout, TimeUnit unit)
```
- lies dormant until one of the following things happens:
	- The last thread arrives; or
	- The specified timeout elapses; (In case of second form) or
	- Some other thread interrupts the current thread; or
	- Some other thread interrupts one of the other waiting threads; or
	- Some other thread times out while waiting for barrier; or
	- Some other thread invokes reset() on this barrier.
- await() method returns int which is the arrival index of the current thread, where index (Number of specified threads - 1) indicates the first to arrive and zero indicates the last to arrive.

### BrokenBarrierException
- **reset()** - resets barrier to initial state. If any parties are currently waiting at the barrier, they will return with a ***BrokenBarrierException***.
- CyclicBarrier uses all-or-none breakage model, If any thread leaves a barrier point prematurely due to interruption, failure, or timeout, all other threads waiting at that barrier point will also leave abnormally via BrokenBarrierException (orInterruptedException if they too were interrupted at about the same time).

![cyclic-barrier]({{site.cdn}}/java/multi-threading/cyclic-barrier.png)

|CountDownLatch	|CyclicBarrier|
---|---
Main thread waits for other threads to be executed.	| Each worker thread waits for each other to be executed.
Cannot be reused. | Can be reused by resetting barrier, once barrier is broken.
No such action is available. | Can provide barrierAction, to be executed once all threads reached barrier point, but before any thread is released.

```java
public class CyclicBarrierDemo {
    public static void main(String[] args) {
        CyclicBarrier cb = new CyclicBarrier(3, new AfterAction());
        // Initializing three threads to read 3 different files.
        Thread t1 = new Thread(new TxtReader("thread-1", "file-1", cb));
        Thread t2 = new Thread(new TxtReader("thread-2", "file-2", cb));
        Thread t3 = new Thread(new TxtReader("thread-3", "file-3", cb));
        t1.start();
		t2.start();
		t3.start();        
        System.out.println("Done ");
    }
}
```
```java
class AfterAction implements Runnable {
    @Override
    public void run() {
        System.out.println("In after action class, start further processing as all files are read");
    }
}
```
```java
class TxtReader implements Runnable {
    private String threadName;
    private String fileName;
    private CyclicBarrier cb;
    TxtReader(String threadName,String filename,CyclicBarrier cb){
        this.threadName = threadName;
        this.fileName = fileName;
        this.cb = cb;        
    }
    @Override
    public void run() {
        System.out.println("Reading file "+fileName+" thread "+threadName);    
        try{
            // calling await so the current thread suspends
            cb.await();           
        } catch (InterruptedException e) {
            System.out.println(e);
        } catch (BrokenBarrierException e) {
            System.out.println(e);
        }
    }
}
```

# Phaser
- suitable for use where it is required to synchronize threads over one or more phases of activity. 
- Can be used to synchronize a single phase also, in that case it acts more like a CyclicBarrier.
- Phaser is reusable (like CyclicBarrier) and more flexible in usage.
- Tasks may register(), bulkRegister(int), arriveAndDeregister() themselves hence number of parties can vary.
- phaser is a synchronization barrier so we have to make phaser wait until all registered parties finish a phase. That waiting can be done using **arrive()**.
- number of arrivals is equal to the parties which are registered that phase is considered completed and it advances to next phase (if there is any), or terminate.
- each generation of a phaser has an associated phase number starting from 0 which wraps around to 0 after Integer.MAX_VALUE.

|Methods|	|
|---	|---|
resgister()|Adds a new unarrived party to phaser. returns the arrival phase number for registration.
arrive()| Arrives at this phaser, without waiting for others to arrive. Note that arrive() method does not suspend execution of the calling thread. Returns the arrival phase number, or a negative value if terminated. Note that this method should not be called by an unregistered party.
arriveAndDeregister()| Arrives at this phaser and deregisters from it without waiting for others to arrive. Returns the arrival phase number, or a negative value if terminated.
arriveAndAwaitAdvance()| This method awaits other threads to arrives at this phaser. Returns the arrival phase number, or the (negative) current phase if terminated. If you want to wait for all the other registered parties to complete a given phase then use this method.
bulkRegister(int parties)| Used to register perties in bulk. Given number of new unarrived parties will be registered to this phaser.
onAdvance(int phase, int registeredParties)| If you want to perform some action before the phase is advanced you can override this method. Also used to control termination.
