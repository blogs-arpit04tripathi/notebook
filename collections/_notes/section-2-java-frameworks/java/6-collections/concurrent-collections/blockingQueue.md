---
layout: post
title: BlockingQueue
permalink: /:collection/java/collections/blockingQueue
---

* Primarily used for implementing producer consumer problem.
* Producer - wait till space is available while adding.
* Consumer – wait till queue becomes non empty while removing.
* Java implementations - **ArrayBlockingQueue, LinkedBlockingQueue, PriorityBlockingQueue, SynchronousQueue** etc.
* BlockingQueue implementations are thread-safe and can also be used in inter-thread communications. 
* null is not allowed. 
