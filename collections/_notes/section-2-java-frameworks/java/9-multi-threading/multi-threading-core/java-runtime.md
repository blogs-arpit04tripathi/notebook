---
layout: post
title: Java Runtime
permalink: /:collection/java/multithreading/java-runtime
---

* Java **Runtime** class is used to interact with java runtime environment. 
* Java Runtime class provides methods to execute a process, invoke GC, get total and free memory etc. 
* There is only one instance of java.lang.Runtime class available for one java application. 
* The **Runtime.getRuntime()** method returns the singleton instance of Runtime class.

```java
public class ShutdownCommand {
    public static void main(String[] args) {
        Runtime r = Runtime.getRuntime();
        System.out.println("Total Memory: " + r.totalMemory());
        System.out.println("Free Memory: " + r.freeMemory());
        for (int i = 0; i < 10000; i++) {
            new ShutdownCommand();
        }
        System.out.println("After 10000 instance, Free Memory: " + r.freeMemory());
        System.gc();
        System.out.println("After gc(), Free Memory: " + r.freeMemory());
        System.out.println(r.availableProcessors()); // Number Of Processors
        // will open a new notepad
        try {
            r.exec("notepad");
        } catch (IOException e) {
            e.printStackTrace();
        }
        r.exec("shutdown -s -t 0");
        // -s to shutdown, -r to restart system and -t switch to specify time delay.
    }
}
```

|Method|Description|
---|---
public static Runtime getRuntime()	|returns the instance of Runtime class.
public void exit(int status)	|terminates the current virtual machine.
public void addShutdownHook(Thread hook)	|registers new hook thread.
public Process exec(String command) throws IOException	|executes given command in a separate process.
public int availableProcessors()	|returns no. of available processors.
public long freeMemory()	|returns amount of free memory in JVM.
public long totalMemory()	|returns amount of total memory in JVM.
