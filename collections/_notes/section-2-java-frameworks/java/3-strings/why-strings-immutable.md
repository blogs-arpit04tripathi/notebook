---
layout: post
title: Why String are Immutable?
permalink: /:collection/java/strings/why-strings-immutable
---


1. **Design** - Strings reference in java heap area known as "String Intern pool". If mutable, changes may affect others.
2. **Security** - String used as parameter for network connection, files, DB connection urls, usernames/passwords etc.If mutable, changes in such params can lead to serious security threat.
3. **Efficiency** - String’s hashcode frequently used in Java, like HashMap. Immutable hence can be cached.
4. **Synchronization,concurrency** - Immutabe, thread safe thereby solving the synchronization issues.
5. **Class loading** - String arguments for class loading. mutable could result in wrong class being loaded 

**Note**: *Immutability of String, cannot change it using its public API but can be manipulated using reflection.*
