---
layout: post
title: Common Tasks - FAQ Code
permalink: /:collection/java/multithreading/common-tasks-faq-code
---

- TOC
{:toc}

<hr><br>


# Single Task - Multiple Threads
**How to perform single task by multiple threads?**  
If you have to perform single task by many threads, have only one run() method.

```java
class TestMultitasking1 extends Thread {

    public void run() {
        sysout("task one");
    }

    public static void main(String args[]) {
        TestMultitasking1 t1 = new TestMultitasking1();
        TestMultitasking1 t2 = new TestMultitasking1();
        t1.start();
        t2.start();
    }
}
// Output: 
task one task one
```

![multitask-single-thread]({{site.cdn}}/java/multi-threading/multitask-single-thread.png)

# Multiple Task - Multiple Threads
**How to perform multiple tasks by multiple threads?**  
If you have to perform multiple tasks by multiple threads, have multiple run() methods.

```java
class Simple1 extends Thread {
    public void run() {
        System.out.println("task 1");
    }
}
```
```java
class Simple2 extends Thread {
    public void run() {
        System.out.println("task 2");
    }
}
```
```java
class TestMultitasking3 {
    public static void main(String args[]) {
        Simple1 t1 = new Simple1();
        Simple2 t2 = new Simple2();
        t1.start();
        t2.start();
    }
}
```
```
// Output:
task one
task two
```

# Print Odd Even - without wait or synchronized
**Print natural numbers 1 to 20 using two threads without using wait or synchronized where one thread prints only odd number and other thread prints only even number?**  

```java
public class EvenOddPrinterWithoutWait {
    static boolean flag = true;
    
    public static void main(String[] args) {
        Runnable odd = () - > {
            for (int i = 1; i <= 10;) {
                if (EvenOddPrinter.flag) {
                    i = printIt(i);
                }
            }
        };
        Runnable even = () - > {
            for (int i = 2; i <= 10;) {
                if (!EvenOddPrinter.flag) {
                    i = printIt(i);
                }
            }
        };
        Thread t1 = new Thread(odd, "Odd");
        Thread t2 = new Thread(even, "Even");
        t1.start();
        t2.start();
    }
    
    private static int printIt(int i) {
        System.out.println(Thread.currentThread().getName() + "\t : " + i);
        EvenOddPrinter.flag = !EvenOddPrinter.flag;
        return (i + 2);
    }
}
```

# Print Odd Even - using wait or synchronized
**Print natural numbers 1 to 20 using two threads using wait or synchronized where one thread prints only odd number and other thread prints only even number?**  

```java
public class EvenOddPrinterWithWait {

    public static final int limit = 20;
    public static void main(String...args) {

        // Runnable for even printer
        final SharedPrinterWithWait counterObj = new SharedPrinterWithWait(20);
        Runnable evenNoPrinter = () - > {
            int num = 0;
            while (true) {
                if (num >= limit) {
                    break;
                }
                num = counterObj.printNextEven();
            }
        };

        // Runnable for odd printer
        Runnable oddNoPrinter = () - > {
            int num = 0;
            while (true) {
                if (num >= limit) {
                    break;
                }
                num = counterObj.printNextOdd();
            }
        };

        new Thread(oddNoPrinter).start();
        new Thread(evenNoPrinter).start();
    }
}
```
```java
public class SharedPrinterWithWait {
    private int count = 0;
    private boolean isEven = true;
    private int upperLimit;
    SharedPrinterWithWait(int limit) {
        upperLimit = limit;
    }
    public synchronized int printNextOdd() {
        // Wait until odd is available.
        while (isEven) {
            try {
                wait();
            } catch (InterruptedException e) {}
        }
        count++;
        if (count <= upperLimit) {
            printEven(count);
        }
        // Toggle status.
        isEven = true;
        // Notify even printer for status changed.
        notifyAll();
        return count;
    }
    public synchronized int printNextEven() {
        // Wait until even is available.
        while (!isEven) {
            try {
                wait();
            } catch (InterruptedException e) {}
        }
        count++;
        if (count <= upperLimit) {
            printOdd(count);
        }
        // Toggle status.
        isEven = false;
        // Notify odd printer for status changed.
        notifyAll();
        return count;
    }
    public void printOdd(int num) {
        System.out.println("ODD\t # " + num);
    }
    public void printEven(int num) {
        System.out.println("EVEN\t # " + num);
    }
}
```

# Print Odd Even - using semaphore
**Print natural numbers 1 to 20 using two threads using semaphore**  

* A semaphore controls access to a shared resource through the use of a counter. ***If the counter is greater than zero, then access is allowed***. If it is zero, then access is denied.
* Here we have two threads. Both the threads have an object of the SharedPrinter class. **The SharedPrinter class will have two semaphores, semOdd and semEven which will have 1 and 0 permits to start with**. This will ensure that odd number gets printed first.
* To print an odd number, the acquire() method is called on semOdd, and since the initial permit is 1, it acquires the access successfully, prints the odd number and calls release() on semEven.
* Calling **release()** will increment the permit by 1 for semEven, and the even thread can then successfully acquire the access and print the even number.

![semaphores]({{site.cdn}}/java/multi-threading/semaphores.png)

```java
public static void main(String[] args) {
    int max = 15;
    SharedPrinter sp = new SharedPrinter();
    Thread odd = new Thread(new OddRunnable(sp, max), "Odd");
    Thread even = new Thread(new EvenRunnable(sp, max), "Even");
    odd.start();
    even.start();
}
```
```java
public class OddRunnable implements Runnable {
    private SharedPrinter sp;
    private int max;
    OddRunnable(SharedPrinter sp, int max) {
        this.sp = sp;
        this.max = max;
    }
    @Override
    public void run() {
        for (int i = 1; i <= max; i = i + 2) {
            sp.printOddNum(i);
        }
    }
}
```
```java
public class EvenRunnable implements Runnable {
    private SharedPrinter sp;
    private int max;
    EvenRunnable(SharedPrinter sp, int max) {
        this.sp = sp;
        this.max = max;
    }
    @Override
    public void run() {
        for (int i = 2; i <= max; i = i + 2)
            sp.printEvenNum(i);
    }
}
```
```java
public class SharedPrinter {
    private Semaphore semEven = new Semaphore(0);
    private Semaphore semOdd = new Semaphore(1);

    void printEvenNum(int num) {
        try {
            semEven.acquire();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        System.out.println(String.format("%s\t: s", Thread.currentThread().getName(), num));
        semOdd.release();
    }

    void printOddNum(int num) {
        try {
            semOdd.acquire();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        System.out.println(String.format("%s\t: %s", Thread.currentThread().getName(), num));
        semEven.release();
    }
}
```
