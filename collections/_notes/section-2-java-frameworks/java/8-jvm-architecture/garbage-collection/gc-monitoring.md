---
layout: post
title: Garbage Collection Monitoring
permalink: /:collection/java/gc-monitoring
---

- TOC
{:toc}

<hr><br>

- We can use Java command line as well as UI tools for monitoring garbage collection activities of an application.

```java
~/Downloads/jdk1.7.0_55/demo/jfc/Java2D$ java -Xmx120m -Xms30m -Xmn10m -XX:PermSize=20m -XX:MaxPermSize=20m -XX:+UseSerialGC -jar Java2Demo.jar
```

# jstat
- We can use **jstat command line tool** to monitor the JVM memory and garbage collection activities. 
- It ships with standard JDK, so you don’t need to do anything else to get it. 
- For executing jstat you need to know the process id of the application, you can get it easily using `ps -eaf | grep java` command.

```java
ps -eaf | grep Java2Demo.jar
501 9582  11579   0  9:48PM ttys000    0:21.66 /usr/bin/java -Xmx120m -Xms30m -Xmn10m -XX:PermSize=20m -XX:MaxPermSize=20m -XX:+UseG1GC -jar Java2Demo.jar
501 14073 14045   0  9:48PM ttys002    0:00.00 grep Java2Demo.jar
```
So the process id for my java application is 9582.
```java
jstat -gc 9582 1000
```

S0C|S1C|S0U|S1U|EC|EU|OC|OU|PC|PU|YGC|YGCT|FGC|FGCT|GCT
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
1024.0|1024.0|0.0 |0.0|8192.0|7933.3|42108.0|23401.3|20480.0|19990.9|157|0.274|40|1.381|1.654
1024.0|1024.0|0.0 |0.0|8192.0|8026.5|42108.0|23401.3|20480.0|19990.9|157|0.274|40|1.381|1.654
1024.0|1024.0|0.0 |0.0|8192.0|8030.0|42108.0|23401.3|20480.0|19990.9|157|0.274|40|1.381|1.654
1024.0|1024.0|0.0 |0.0|8192.0|8122.2|42108.0|23401.3|20480.0|19990.9|157|0.274|40|1.381|1.654
1024.0|1024.0|0.0 |0.0|8192.0|8171.2|42108.0|23401.3|20480.0|19990.9|157|0.274|40|1.381|1.654
1024.0|1024.0|48.7|0.0|8192.0|106.7 |42108.0|23401.3|20480.0|19990.9|158|0.275|40|1.381|1.656
1024.0|1024.0|48.7|0.0|8192.0|145.8 |42108.0|23401.3|20480.0|19990.9|158|0.275|40|1.381|1.656

The last argument for jstat is the time interval between each output, so it will print memory and garbage collection data every 1 second.

Let’s go through each of the columns one by one.
- **S0C and S1C**: current size of the Survivor0 and Survivor1 areas in KB.
- **S0U and S1U**: current usage of the Survivor0 and Survivor1 areas in KB. Notice that one of the survivor areas are empty all the time.
- **EC and EU**: current size and usage of Eden space in KB. Note that EU size is increasing and as soon as it crosses the EC, Minor GC is called and EU size is decreased.
- **OC and OU**: current size and current usage of Old generation in KB.
- **PC and PU**: current size and current usage of Perm Gen in KB.
- **YGC and YGCT**: YGC column displays the number of GC event occurred in young generation. YGCT column displays the accumulated time for GC operations for Young generation. Notice that both of them are increased in the same row where EU value is dropped because of minor GC.
- **FGC and FGCT**: FGC column displays the number of Full GC event occurred. FGCT column displays the accumulated time for Full GC operations. Notice that Full GC time is too high when compared to young generation GC timings.
- **GCT**: This column displays the total accumulated time for GC operations. It’s sum of YGCT and FGCT column values.
- The advantage of **jstat** is that it can be executed in remote servers too where we don’t have GUI. 
- Notice that sum of S0C, S1C and EC is 10m as specified through **-Xmn10m** JVM option.

# Java VisualVM with Visual GC
- If you want to see memory and GC operations in GUI, then you can use **jvisualvm tool**. 
- Java VisualVM is also part of JDK, so you don’t need to download it separately. Just run **jvisualvm** command in the terminal to launch the Java **VisualVM** application. Once launched, you need to install **Visual GC** plugin from Tools --> Plugins option.

# Java Garbage Collection Tuning
- **Java Garbage Collection Tuning** should be the last option you should use for increasing the throughput of your application and only when you see drop in performance because of longer GC timings causing application timeout.
- If you see **java.lang.OutOfMemoryError: PermGen space errors** in logs, then try to monitor and increase the Perm Gen memory space using **-XX:PermGen** and **-XX:MaxPermGen** JVM options. 
- You might also try using **-XX:+CMSClassUnloadingEnabled** and check how it’s performing with CMS Garbage collector.
- If you see a lot of Full GC operations, then you should try increasing Old generation memory space.
- Overall garbage collection tuning takes a lot of effort and time and there is no hard and fast rule for that. You would need to try different options and compare them to find out the best one suitable for your application.

