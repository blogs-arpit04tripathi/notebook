---
layout: post
title: Singleton Pattern
permalink: /:collection/design-patterns/creational/singleton-pattern
---

- TOC
{:toc}

<hr><br>

**Singleton Pattern**
-	Ensures that ***only one instance of the class exists in the java virtual machine*** with a **global** access to ***get the instance*** of the class.
-	Used for logging, drivers objects, caching and thread pool.
-	Used in other design patterns like Abstract Factory , Builder, Prototype, Facade etc. 
-	Used in core java classes also, for example java.lang.Runtime, java.awt.Desktop.

# Java Singleton Pattern
- private constructor.
- private static variable of the same class, the only instance of the class.
- public static method to get the instance.

![creational-singleton.png]({{site.cdn}}/design-patterns/creational-singleton.png)

```java
public class LazyInitializedSingleton {
    private static LazyInitializedSingleton instance;    
    private LazyInitializedSingleton(){}    
    public static LazyInitializedSingleton getInstance(){
        if(instance == null)
            instance = new LazyInitializedSingleton(); 
        return instance;
    }
}
```
- **Performance Drawback**, acquire a potentially unnecessary lock each time we want to get the instance.
- **To fix**, *we could instead start by verifying if we need to create the object in the first place and only in that case, we would acquire the lock.
 This is called **Double Checked Locking**.

> NOTE: This is not 100% singleton.

```java
public class DclSingleton {
    private static volatile DclSingleton instance;
    private DclSingleton(){}    
    public static DclSingleton getInstance() {
        if (instance == null) {
            synchronized (DclSingleton.class) {
                if (instance == null)
                    instance = new DclSingleton();
            }
        }
        return instance;
    }
}
```

# Broken by Reflection
```java
Constructor[] constructors = DclSingleton.class.getDeclaredConstructors();
for (Constructor constructor : constructors) {
   constructor.setAccessible(true);
   instanceTwo = (DclSingleton) constructor.newInstance();
   System.out.println(instanceOne.hashCode());
   System.out.println(instanceTwo.hashCode()); 
}  // Different hashcodes, means Singleton Broken
```
`Solution` : call public getInstance in constructor

# Broken by Serialization
```java
DclSingleton instanceOne = DclSingleton.getInstance();
ObjectOutput out = new ObjectOutputStream(new FileOutputStream("filename.ser"));
out.writeObject(instanceOne);
out.close();
//deserailize from file to object
ObjectInput in = new ObjectInputStream(new FileInputStream("filename.ser"));
DclSingleton instanceTwo = (DclSingleton) in.readObject();
in.close();        
System.out.println("instanceOne hashCode="+instanceOne.hashCode());
System.out.println("instanceTwo hashCode="+instanceTwo.hashCode());
```
`Solution `:
```java
// implement readResolve method 
protected Object readResolve() { 
    return instance; 
}
```
- `readResolve` is used for replacing the object read from the stream.
- `readObject()` is an existing method in `ObjectInputStream` class, while reading object at the time of deserialization readObject method internally check whether the class object which is being deserialized having readResolve method or not if readResolve method exist then it will invoke readResolve method and return the same instance.
- Writing readResolve method is a good practice to achieve pure singleton design pattern where no one can get another instance by serializing/deserializing.

# Close to Singleton
```java
public class DclSingleton { // Close to Singleton
    private static volatile DclSingleton instance;
    // Overcoming new XYZ() 
    private DclSingleton() {}
    // only way to avoid reflection is to have EnumSingleton

    // locking complete method with not be good for performance
    public static DclSingleton getInstance() {
        if (instance == null) {
            synchronized(DclSingleton.class) {
                // Performance, Lock only if need to instantiate
                if (instance == null)
                    instance = new DclSingleton();
            }
        }
        return instance;
    }

    // Fixing clone
    @Override
    protected Object clone() throws CloneNotSupportedException {
        throw new CloneNotSupportedException();
    }

    // Fixing Serialization
    protected Object readResolve() {
        return instance;
    }
}
```

# Enum Singleton
- ***To overcome Reflection, use Enum to implement Singleton.***
- Java ensures that any enum value is instantiated only once.
- Globally accessible.
- Drawback : ***does not allow lazy initialization***.
- ***enums don’t have any constructor*** so it is not possible for Reflection to utilize it.
- Enums have their by-default constructor, we can’t invoke them by ourself.
- **JVM handles the creation and invocation of enum constructors internally**.

```java
public enum EnumSingleton {
    INSTANCE;    
    public static void doSomething(){ //do something }
}
```