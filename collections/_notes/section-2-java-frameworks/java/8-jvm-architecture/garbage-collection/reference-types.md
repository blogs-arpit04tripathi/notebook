---
layout: post
title: Reference Types
permalink: /:collection/java/reference-types
---

- TOC
{:toc}

<hr><br>

Types of references based on when will the objects on heap become eligible for garbage collection.

# Strong Reference
- Not garbage collected if it has a direct or indirect strong reference pointing to it. (through a chain of strong references)

# Weak Reference
- Object with weak reference is most likely to not survive after the next garbage collection process. 
- A weak reference is created as follows:

```java
WeakReference<StringBuilder> reference = new WeakReference<>(new StringBuilder());
```
- **Use Case** - caching scenarios where you retrieve some data, and you want it to be stored in memory but not sure when, or if, this data will be requested again. So, you can keep a weak reference to it, and in case the garbage collector runs, it could be that it destroys your object on the heap. Therefore, after a while, retrieve may return null value.
- A nice implementation for caching scenarios is the collection **WeakHashMap<K,V>**. 
- Entry<K,V> actually extends the WeakReference class and uses its **ref** field as the map’s key:

```java
// The entries in this hash table extend WeakReference, using its main ref field as the key.
private static class Entry<K,V> extends WeakReference<Object> implements Map.Entry<K,V> {
V value;        final int hash;        Entry<K,V> next;
```
- Once a key from the WeakHashMap is garbage collected, the entire entry is removed from the map.

# Soft Reference
- For more memory-sensitive scenarios, Wll be garbage collected only when application is running low on memory. 
- If no critical need to free up some space, the GC will not touch softly reachable objects.
- Java guarantees that all soft referenced objects are cleaned up before it throws an OutOfMemoryError. 
- Similar to weak references, a soft reference is created as follows:

```java
SoftReference<StringBuilder> reference = new SoftReference<>(new StringBuilder());
```

# Phantom Reference
- Used to schedule post-mortem cleanup actions, since we know for sure that objects are no longer alive. 
- Used only with a **reference queue**, since the **get() method of such references will always return null**.
- Garbage Collector adds a phantom reference to a reference queue **after the finalize method of its referent is executed**. It implies that the instance is still in the memory.
- **Use Cases**
	- **to determine when an object was removed from the memory** which helps to schedule memory-sensitive tasks. For example, we can wait for a large object to be removed before loading another one.
	- **to avoid using the finalize method and improve the finalization process**.

```java
ReferenceQueue < Object > referenceQueue = new ReferenceQueue < > ();
List < LargeObjectFinalizer > references = new ArrayList < > ();
List < Object > largeObjects = new ArrayList < > ();

for (int i = 0; i < 10; ++i) {
    Object largeObject = new Object();
    largeObjects.add(largeObject);
    references.add(new LargeObjectFinalizer(largeObject, referenceQueue));
}
largeObjects = null;
System.gc();
Reference << ? > referenceFromQueue;
for (PhantomReference < Object > reference: references) {
    System.out.println(reference.isEnqueued());
}
while ((referenceFromQueue = referenceQueue.poll()) != null) {
    ((LargeObjectFinalizer) referenceFromQueue).finalizeResources();
    referenceFromQueue.clear();
}
```
```java
public class LargeObjectFinalizer extends PhantomReference < Object > {
    public LargeObjectFinalizer(
        Object referent, ReferenceQueue << ? super Object > q) {
        super(referent, q);
    }
    public void finalizeResources() {
        // free resources
        System.out.println("clearing ...");
    }
}

// referenceQueue – to keep track of enqueued references, references – to perform cleaning work afterward, largeObjects – a large data structure.
```
- *System.gc()* isn’t triggering garbage collection immediately – it’s simply a hint for JVM to trigger the process.
- The for loop demonstrates how to make sure that all references are enqueued – it will print out true for each reference.
- Finally, we used a while loop to poll out the enqueued references and do cleaning work for each of them.
