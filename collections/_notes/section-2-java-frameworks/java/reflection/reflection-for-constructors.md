---
layout: post
title: Reflection for Constructors
permalink: /:collection/java/reflection/reflection-for-constructors
---

# getConstructor()
* Get Public Constructor
* to get specific public constructor.

```java
Constructor<?> constructor = Class.forName("com.journaldev.reflection.ConcreteClass").getConstructor(int.class);
//getting constructor parameters
System.out.println(Arrays.toString(constructor.getParameterTypes())); // prints "[int]"
Constructor<?> hashMapConstructor = Class.forName("java.util.HashMap").getConstructor(null);
System.out.println(Arrays.toString(hashMapConstructor.getParameterTypes())); // prints "[]"
```

# newInstance()
* Instantiate Object using Constructor
* use method on the constructor object to instantiate a new instance of the class.

```java
Constructor<?> constructor = Class.forName("com.journaldev.reflection.ConcreteClass").getConstructor(int.class);
//getting constructor parameters
System.out.println(Arrays.toString(constructor.getParameterTypes()));
// prints "[int]"
Object myObj = constructor.newInstance(10);
Method myObjMethod = myObj.getClass().getMethod("method1", null);
myObjMethod.invoke(myObj, null); 
//prints "Method1 impl."
Constructor<?> hashMapConstructor = Class.forName("java.util.HashMap").getConstructor(null);
System.out.println(Arrays.toString(hashMapConstructor.getParameterTypes())); 
// prints "[]"
HashMap<String,String> myMap = (HashMap<String,String>) hashMapConstructor.newInstance(null);
```