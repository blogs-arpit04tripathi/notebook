---
layout: post
title: Runnable vs Callable and Future
permalink: /:collection/java/multithreading/runnable-vs-callable-and-future
---

# Runnable
- run()
- no parameters no return values
- Executors class provide useful methods to execute Callable in a thread pool.

# Callable
- java.util.concurrent.Callable
- call(), returns generic object <V> and it can throw checked exceptions.    
- Returned value from callable is captured into java.util.concurrent.Future Object.

# Future
- Since callable tasks run in parallel, we have to wait for the returned Object. 
- Using Future we can find out the status of the Callable task and get the returned Object. 
- **get()** - can wait for the Callable to finish and then return the result.
- **cancel()** - to cancel the associated Callable task
- **isDone()** and **isCancelled()** - to find out the current status of associated Callable task.
- **get(2, TimeUnit.SECONDS)** - specify time to wait for result, useful to avoid current thread getting blocked for longer time.

```java
public class MyCallable implements Callable < String > {
    @Override
    public String call() throws Exception {
        Thread.sleep(4000);
        return Thread.currentThread().getName();
    }

    public static void main(String args[]) {
        ExecutorService executorService = Executors.newFixedThreadPool(3);
        List < Future < String >> list = new ArrayList < Future < String >> ();
        Callable < String > callable = new MyCallable();
        for (int i = 0; i < 7; i++) {
            Future < String > future = executorService.submit(callable);
            list.add(future);
        }
        for (Future < String > fut: list) {
            try {
                System.out.println(new Date() + "::" + fut.get(2, TimeUnit.SECONDS));
            } catch (InterruptedException | ExecutionException | TimeoutException e) {
                e.printStackTrace();
            }
        }
        executorService.shutdown();
        while (!executorService.isTerminated()) {}
        System.out.println("Finished all threads");
    }
}
```
