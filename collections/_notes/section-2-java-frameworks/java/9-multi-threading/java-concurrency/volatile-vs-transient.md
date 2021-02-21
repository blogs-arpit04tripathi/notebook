---
layout: post
title: volatile vs transient
permalink: /:collection/java/multithreading/volatile-vs-transient
---


transient	| volatile
---			| ---
used along with instance variables to exclude them from serialization process. if a field is transient its value will not be persisted.	|used to indicate compiler and JVM that always read its value from main memory and follow happens-before relationship on visibility of volatile variable among multiple thread.
can not be used along with static keyword	|can be used along with static.
transient variables are initialized with default value during de-serialization and their assignment or restoration of value has to be handled by application code.||
