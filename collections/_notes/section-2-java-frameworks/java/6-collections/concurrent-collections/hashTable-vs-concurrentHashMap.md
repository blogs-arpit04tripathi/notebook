---
layout: post
title: HashTable vs ConcurrentHashMap
permalink: /:collection/java/collections/hashTable-vs-concurrentHashMap
---


|	|HashTable	|ConcurrentHashMap|
|---|---|---|
|Lock	|Object Level|Bucket Level Lock for write
|Concurrent Reads	|No, get() method is synchronized	|Allowed, by using volatile keyword

**Why does Java provide default value of partition count as 16 instead of very high value?**  
* Ideally, you should choose a value to accommodate as many threads as will ever concurrently modify the table.
* Using a significantly higher value than you need can waste space and time
* a significantly lower value can lead to thread contention.

**Write the simple example which proves ConcurrentHashMap class behaves like fail safe iterator?**  
```java
import java.util.concurrent.ConcurrentHashMap;
public class ConcurrentHashMapExample{
   public static void main(String[] args) {
        ConcurrentHashMap<String,String> premiumPhone = new ConcurrentHashMap<>();
        premiumPhone.put("Apple", "iPhone6");
        Iterator iterator = premiumPhone.keySet().iterator();
        while (iterator.hasNext()) {
            System.out.println(premiumPhone.get(iterator.next()));
            premiumPhone.put("Sony", "Xperia Z");
        }
    }
}
Output : iPhone6
```

**When is ConcurrentHashMap a better choice?**  
* ConcurrentHashMap is a better choice when there are ***more reads than writes***.
* If there are more writes and that too many threads operating on the same segment then the threads will block which will deteriorate the performance.
