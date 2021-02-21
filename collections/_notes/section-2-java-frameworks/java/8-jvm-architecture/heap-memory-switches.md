---
layout: post
title: Java Heap Memory Switches
permalink: /:collection/java/heap-memory-switches
---

- Java provides a lot of memory switches that we can use to set the memory sizes and their ratios. 
- Some of the commonly used memory switches are:

VM SWITCH	|VM SWITCH DESCRIPTION
---|---
-Xms	|initial heap size when JVM starts
-Xmx	|maximum heap size.
-Xmn	|size of the Young Generation, rest of the space goes for Old Generation.
-XX:PermGen	|initial size of the Permanent Generation memory
-XX:MaxPermGen	|maximum size of Perm Gen
-XX:MetaspaceSize| 	 
-XX:MaxMetaspaceSize|	 
-XX:SurvivorRatio	|ratio of Eden space and Survivor Space<br>Young Generation=10m with VM switch -XX:SurvivorRatio=2 then 5m will be reserved for Eden Space and 2.5m each for both the Survivor spaces. The default value is 8.
-XX:NewRatio	|For providing ratio of old/new generation sizes. The default value is 2.
MinMetaspaceFreeRatio<br>MaxMetaspaceFreeRatio	|minimum percentage of class metadata capacity free after **garbage collection**

![heap-memory-switches]({{site.cdn}}/java/jvm-architecture/heap-memory-switches.png)
![heap-memory-switches-generation]({{site.cdn}}/java/jvm-architecture/heap-memory-switches-generation.png)
