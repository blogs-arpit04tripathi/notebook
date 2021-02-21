---
layout: post
title: Fork Join Framework
permalink: /:collection/java/multithreading/fork-join-framework
---


- fork-join framework allows to break a certain task on several workers and then wait for the result to combine them.
- Used to leverage multi-processor machine's capacity
- fork/join framework uses a pool of threads called the ***ForkJoinPool***, which manages worker threads of type ***ForkJoinWorkerThread***.

|||
|---|---|
Fork | process where task splits itself into smaller and independent sub-tasks that can be executed concurrently.
Join | process where task join results from all sub-tasks after their execution, otherwise it keeps waiting.
ForkJoinPool | special thread pool designed to work with fork-and-join task splitting, implementation of the ExecutorService.
RecursiveAction | a task which does not return any value, extends ForkJoinTask. 
RecursiveTask | a task which returns a value, extends ForkJoinTask.

- Worker threads execute 1 task at the time, but **ForkJoinPool** doesn’t create a separate thread for every single subtask.
- Each thread in pool has its own double-ended queue (or [deque](https://en.wikipedia.org/wiki/Double-ended_queue), pronounced deck) which stores tasks.
- This architecture is vital for balancing the thread’s workload with the help of the ***work-stealing algorithm***.
- ***free threads try to “steal” work from deques of busy threads hence minimizes the possibility that threads will compete for tasks***.

```java
// pool will use 2 processor cores, degree of parallelism.
public static ForkJoinPool forkJoinPool = new ForkJoinPool(2);
```

![fork-join-pool]({{site.cdn}}/java/multi-threading/fork-join-pool.png)

```java
class Writer extends RecursiveAction {
   @Override
   protected void compute() { }
}
```
```java
class Sum extends RecursiveTask<Long> {
   @Override
   protected Long compute() { return null; }
}
```
```java
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ForkJoinPool;
import java.util.concurrent.RecursiveTask;
public class TestThread {
   public static void main(final String[] arguments) throws InterruptedException, ExecutionException {
      int nThreads = Runtime.getRuntime().availableProcessors();
      System.out.println(nThreads);      
      int[] numbers = 1 to 1000;
      ForkJoinPool forkJoinPool = new ForkJoinPool(nThreads);
      Long result = forkJoinPool.invoke(new Sum(numbers,0,numbers.length));
      System.out.println(result);
   }  

   static class Sum extends RecursiveTask<Long> {
      int low;
      int high;
      int[] array;
      Sum(int[] array, int low, int high) {         
		  this.array = array;
		  this.low   = low;
		  this.high  = high;
		}
      protected Long compute() {         
         if(high - low <= 10) {
            long sum = 0;            
            for(int i = low; i < high; ++i) 
               sum += array[i];
             return sum;
         } else {            
            int mid = low + (high - low) / 2;
            Sum left  = new Sum(array, low, mid);
            Sum right = new Sum(array, mid, high);
            left.fork();
            long rightResult = right.compute();
            long leftResult  = left.join();
            return leftResult + rightResult;
         }
      }
   }
}
```
```java 
forkJoinPool.execute(customRecursiveTask);
int result = customRecursiveTask.join();
int result = forkJoinPool.invoke(customRecursiveTask);
```

* **invokeAll()** - submit a sequence of ForkJoinTasks to the ForkJoinPool. forks them returns a collection of Future objects in the order in which they were produced.

```java
ForkJoinTask.invokeAll(createSubtasks());
```

* The *fork()* method submits a task to a pool, but it doesn’t trigger its execution. The *join()* method is be used for this purpose.

Using the fork/join framework can speed up processing of large tasks, but there are guidelines should be followed:
- ***Use as few thread pools as possible*** – in most cases, it is best to use one thread pool per application or system
- ***Use the default common thread pool***, if no specific tuning is needed
- ***Use a reasonable threshold*** for splitting *ForkJoingTask* into subtasks
- ***Avoid any blocking in your ForkJoingTasks***
