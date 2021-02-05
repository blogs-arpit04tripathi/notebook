---
layout: post
title: Storage Scalability Introduction
permalink: /:collection/distributed-systems/storage-scalability
---

- no design is correct or wrong, there are just good designs and bad designs which heavily depend on the use case.
- Hence, it is extremely important to clarify the requirements for the problem asked.

**Pre Requisites**

Have some experience working with a relational DB ( like MySQL ).
- Have a basic idea about NoSQL DBs.
- Understand the basics of the following : 
    -  **Concurrency** : Do you understand threads, deadlock, and starvation? What happens when multiple processes / threads are trying to modify the same data? A basic understanding of read and write locks.
    -  **Networking** : Do you roughly understand basic networking protocols like TCP and UDP? Do you understand the role of switches and routers?
    -  **File systems** : You should understand the systems you’re building upon. Do you know roughly how an OS, file system, and database work? Do you know about the various levels of caching in a modern OS?
