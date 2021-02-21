---
layout: post
title: static Keyword
permalink: /:collection/java/static
---

* static (methods and variable), are **class level** and **can be accessed without reference to any object**. ex. main()
* **main()** is declared as **static** because it **must be called before any objects exist**.
* static variables are **shared among all instances of the class**.
* When objects of its class are declared, **no copy of a static variable is made**.

**static methods restrictions**
* Can call only other static methods.
* Can only access static data. 
* cannot refer to this or super in any way.

**static block**
> Read full article on [static block](https://docs.oracle.com/javase/tutorial/java/javaOO/initial.html){:target="_blank"}.

* executed before the main() at class load time, 
* used to do computation for initializing your static variables.
* **Static initialization blocks** are executed when the class is loaded, and you can initialize static variables in those blocks.
* A class can have any number of static initialization blocks, and they can appear anywhere in the class body.  
* The runtime system guarantees that static initialization blocks are called in the order that they appear in the source code.

```java
static {
    // whatever code is needed for initialization goes here
}
```

Alternative to static blocks
- you can write a **private static method**.
- **Advantage** : can be reused later if you need to reinitialize the class variable.

```java
class Whatever {
    public static varType myVar = initializeClassVariable();
    private static varType initializeClassVariable() {
        // initialization code goes here
    }
}
```

**Static class**
* can use only with inner class. 
* nested class which is a static member of the outer class.
* Accessed as OuterClass.*
* static nested class does not have access to the instance variables and methods of the outer class.