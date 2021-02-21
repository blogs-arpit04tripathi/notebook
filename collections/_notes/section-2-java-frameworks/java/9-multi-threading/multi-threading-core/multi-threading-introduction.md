---
layout: post
title: Introduction to MultiThreading
permalink: /:collection/java/multithreading/introduction
---


* Process
	- heavyweight tasks that require their own separate address spaces.
	- Interprocess communication and Context switching are costly.
* Thread
	- Lightweight tasks that share the same address space in a process.
	- Interthread communication and Context switching are costly.
* **Multiprogramming** – A computer running more than one program at a time (like running Excel and Firefox simultaneously).
* **Multiprocessing** – A computer using more than one CPU at a time.
* **Multitasking** – Tasks sharing a common resource (like 1 CPU).
* **Multithreading** is an extension of multitasking. Thread is used to achieve multitasking.

|Process-based multitasking|Thread-based multitasking|
|---|---|
|allows your computer to run two or more programs concurrently.|thread is the smallest unit of dispatchable code.
A program is the smallest unit of code that can be dispatched by the scheduler.|a single program can perform two or more tasks simultaneously.|
|deals with the “big picture”.|handles the details.|
||Ex. text editor can format text at the same time word suggestions can be made.|

* Multithreading helps you reduce this idle time because another thread can run when one is waiting.

# Java Thread Model
* Threads enable the entire environment to be asynchronous ie. increase efficiency by using idle CPU cycles.
* Benefit - loop/polling mechanism is eliminated. 
* One thread can pause without stopping other parts of your program. 
* Idle time - when a thread reads data from network or waits for user input.

# Single vs Multi Core
* Single core system, concurrently executing threads share the CPU, with each thread receiving a slice of CPU time.
	- two or more threads do not actually run at the same time, but idle CPU time is utilized.
* Multi-core systems, two or more threads actually execute simultaneously.
