---
layout: post
title: Thread Class Methods
permalink: /java/multithreading/thread-class-methods
---


**Why Thread sleep() and yield() methods are static?**  
- Thread sleep() and yield() work on the currently executing thread, and not invoked on threads in wait state. 
- These methods are made static so that when this method is called statically, it works on the current executing thread and avoid confusion to the programmers who might think that they can invoke these methods on some non-running threads.

|Thread Methods||
|---|---|
public void run() 	                |is used to perform action for a thread.
public void start()                 |starts the execution of the thread. JVM calls the run() method on the thread.
public void sleep(long miliseconds) |Causes the currently executing thread to sleep (temporarily cease execution) for the specified number of milliseconds.
public void join()                  |waits for a thread to die.
public void join(long miliseconds)  |waits for a thread to die for the specified miliseconds.
public int getPriority()            |returns the priority of the thread.
public int setPriority(int priority)|changes the priority of the thread.
public String getName()             |returns the name of the thread.
public void setName(String name)    |changes the name of the thread.
public Thread currentThread()       |returns the reference of currently executing thread.
public int getId()                  |returns the id of the thread.
public Thread.State getState() 	    |returns the state of the thread.
public boolean isAlive() 	        |tests if the thread is alive.
public void yield() 	            |causes the currently executing thread object to temporarily pause and allow other threads to execute.
public void suspend() 	            |is used to suspend the thread(depricated).
public void resume() 	            |is used to resume the suspended thread(depricated).
public void stop() 	                |is used to stop the thread(depricated).
public boolean isDaemon() 	        |tests if the thread is a daemon thread.
public void setDaemon(boolean b) 	|marks the thread as daemon or user thread.
public void interrupt()	            |interrupts the thread.
public boolean isInterrupted()   	|tests if the thread has been interrupted.
public static boolean interrupted() |tests if the current thread has been interrupted.