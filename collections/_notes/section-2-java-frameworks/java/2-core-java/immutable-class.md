---
layout: post
title: Immutable Class
permalink: /:collection/java/immutable-class
---

# Create Immutable
* Declare the class as **final** so it can’t be extended.
* Make all **fields private** so that direct access is not allowed.
* **Don’t provide setter** methods for variables
* Make **all mutable fields final** so that it’s value can be assigned only once.
* **Initialize all the fields via a constructor performing deep copy**.
* Perform **cloning** of objects **in the getter methods to return a copy** rather than returning the actual object reference.

# Types of Immutabilty

- **Technically Immutable**
  * state doesn't change after construction, includes primitive wrapper classes.
  * only inlined compile time constants are effectively immutable in true sense.
  * ***even this immutable object can be changed using reflection, however that is usually ignored for the purposes of discussing immutability***.

```java
public class Integer {
    private final int value;
}
```

- **Logically Immutable**
  * A class is logically immutable provided the exposed interface never changes.
  * internal state can change to cache calculated values but does not change the result of any combination of methods (though the timing of those methods could change).
  * **field hash** - can change, but the class is logically immutable as the only change is to cache a derived result and there is no way the caller can tell the difference using normal methods calls.

```java
public final class FinalClassExample {
    private final int id;
    private final String name;
    private final HashMap<String,String> testMap;

    public int getId() {
        return id;
    }
    public String getName() {
        return name;
    }
    /*Accessor function for mutable objects*/
    public HashMap<String,String> getTestMap() {
        return (HashMap<String,String>) testMap.clone();
    }
    /*Constructor performing Deep Copy*/
    public FinalClassExample(int i, String n, HashMap<String,String> hm) {
        System.out.println("Performing Deep Copy");
        this.id = i;
        this.name = n;
        /* Shallow Copy */
        this.testMap = hm;
        /* Deep Copy */
        this.testMap = deepcopy(hm);
    }

    private HashMap<String,String> deepcopy(HashMap<String,String> hm){
        HashMap<String,String> tempMap = new HashMap<String,String>();
        String key;
        Iterator<String> it = hm.keySet().iterator();
        while (it.hasNext()) {
            key = it.next();
            tempMap.put(key, hm.get(key));
        }
        return tempMap;
    }
}
```
For a Date Field,
```java
public Date getDate() {
    return this.date;                       // This will make your class mutable.
    return new Date(this.date.getTime());   // date field cannot be changed.
}
```

# String Class (final)
```java
public final class String {
    /*Cache the hash code for the string */
    private int hash;          // Default to 0
    public int hashCode() {
        int h = hash;
        int len = count;
        if (h == 0 && len > 0) {
            int off = offset;
            char val[] = value;
            for (int i = 0; i < len; i++)
                h = 31*h + val[off++];
            hash = h;
        }
        return h;
    }
}
```
