---
layout: post
title: Atomic Variables in Action
permalink: /:collection/java/multithreading/atomic-variables-in-action
---


* The most commonly used atomic variable classes in Java are AtomicInteger, AtomicLong, AtomicBoolean, and AtomicReference. 
* These classes represent an int, long, boolean and object reference respectively which can be atomically updated.

|||
---|---
get()				| gets the value from the memory, so that changes made by other threads are visible; equivalent to reading a volatile variable
set()				| writes the value to memory, so that the change is visible to other threads; equivalent to writing a volatile variable
lazySet() 			| eventually writes the value to memory, may be reordered with subsequent relevant memory operations. One use case is nullifying references, for the sake of garbage collection, which is never going to be accessed again. In this case, better performance is achieved by delaying the null *volatile* write.
compareAndSet() 	| same as described in above section, returns true when it succeeds, else false
weakCompareAndSet()	| same as compareAndSet, but weaker in the sense, that it does not create happens-before orderings. This means that it may not necessarily see updates made to other variables
incrementAndGet()	|
decrementAndGet()	|
getAndDecrement()	| The setters operations are implemented using compareAndSet.
getAndIncrement()	|
getAndAdd(int i)	|
addAndGet()	 		|

```java
public class SafeCounterWithoutLock {
    private final AtomicInteger counter = new AtomicInteger(0);
    public int getValue() {
        return counter.get();
    }
    public void increment() {
        while (true) {
            int existingValue = getValue();
            int newValue = existingValue + 1;
            if (counter.compareAndSet(existingValue, newValue)) { 
                return;
            }
        }
    }
}
```

* We retry the ***compareAndSet*** operation and again on failure, since we want to guarantee that the call to the *increment* method always increases the value by 1.
* When data (typically a variable) can be accessed by several threads, you must synchronize the access to the data to ensure visibility and correctness.
* This version is faster than the synchronized one and is also thread safe.
* This seems to be complicated, but this is the cost of non-blocking algorithms. When we detect collision, we retry until the operation succeeded. This is the common schema for non-blocking algorithms.

```java
public class Stack {
    private final AtomicReference < Element > head = new AtomicReference < Element > (null);
    public void push(String value) {
        Element newElement = new Element(value);
        while (true) {
            Element oldHead = head.get();
            newElement.next = oldHead;
            //Trying to set the new element as the head
            if (head.compareAndSet(oldHead, newElement)) {
                return;
            }
        }
    }
    public String pop() {
        while (true) {
            Element oldHead = head.get();
            if (oldHead == null) {
                return null;
            } //The stack is empty
            Element newHead = oldHead.next;
            //Trying to set the new element as the head
            if (head.compareAndSet(oldHead, newHead)) {
                return oldHead.value;
            }
        }
    }
    private static final class Element {
        private final String value;
        private Element next;
        private Element(String value) {
            this.value = value;
        }
    }
}
```

* To conclude, [atomic variables](https://dzone.com/articles/java-concurrency-%E2%80%93-part-6) classes are a really good way to implement non-blocking algorithms and are also a very good alternative to volatile variables, because they can provide atomicity and visibility.
* The main purpose behind building atomic classes is to implement nonblocking data structures and their related infrastructure classes. Atomic classes do not serve as replacements for java.lang.Integer and related classes. 
* Most java.util.concurrent package classes use atomic variables instead of synchronization, either directly or indirectly. 
Atomic variables also are used to achieve higher throughput, which means higher application server performance.
