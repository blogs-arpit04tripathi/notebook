---
layout: post
title: Java Shutdown Hook
permalink: /java/multithreading/shutdown-hook
---


* The shutdown hook can be used to perform cleanup resource or save the state when JVM shuts down normally or abruptly. 
* Performing clean resource means closing log file, sending some alerts or something else. 
* So, if you want to execute some code before JVM shuts down, use shutdown hook.

**When does the JVM shut down?**  
* user presses ctrl+c on the command prompt
* System.exit(int) method is invoked
* user logoff
* user shutdown etc.

The addShutdownHook() method of Runtime class is used to register the thread with the Virtual Machine.

```java
public void addShutdownHook(Thread hook){}
```

The object of Runtime class can be obtained by calling the static factory method getRuntime(). The method that returns the instance of a class is known as factory method.

```java
Runtime r = Runtime.getRuntime();
 
class MyThread extends Thread{ 
    public void run(){ System.out.println("shut down hook task completed.."); }  
}  
 
public class TestShutdown1{  
  public static void main(String[] args)throws Exception {  
     Runtime r = Runtime.getRuntime();  
     r.addShutdownHook(new MyThread());  
     System.out.println("Now main sleeping... press ctrl+c to exit");  
     try{Thread.sleep(3000);}catch (Exception e) {}  
  }  
}
// Output:
Now main sleeping... press ctrl+c to exit
shut down hook task completed..
```
***Note***: The shutdown sequence can be stopped by invoking the halt(int) method of Runtime class.