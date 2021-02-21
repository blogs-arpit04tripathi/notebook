---
layout: post
title: Ways to create Object
permalink: /:collection/java/ways-to-create-object
---


1. Using the new keyword
2. Using Class.newInstance() from class Class, It calls the no-arg constructor to create the object.
3. newInstance() method of Constructor class
4. Using clone() method
5. Using deserialization

```java
Employee.class.newInstance(); OR
(Employee) Class.forName("org.package.Emp").newInstance();
```

```java
Constructor<Emp> constructor = Emp.class.getConstructor(); 
Emp emp3 = constructor.newInstance();
```

```java
(Employee) emp3.clone();
```

```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("data.obj")); 
Employee emp5 = (Employee) in.readObject();
```

In above bytecodes all 4 methods call get converted to invokevirtual (object creation is directly handled by these methods) except the first one which got converted to two calls one is new and other is invokespecial (call to the constructor).

|Class.newInstance()|java.lang.reflect.Constructor.newInstance()|
|---|---|
|can only invoke the no-arg constructor|Can invoke any constructor, regardless of the number of parameters.|
|requires that the constructor should be visible|Can also invoke private constructors under certain circumstances.|
|throws any exception (checked or unchecked) thrown by the constructor|Always wraps the thrown exception with an InvocationTargetException.|

* Due to above reasons **Constructor.newInstance() is preferred over Class.newInstance()**, that’s why used by various frameworks and APIs like Spring, Hibernate, Struts, Guava, Zookeeper, Jackson, Servlet etc.
  * Both newInstance() methods are known as reflective ways to create objects.
  * In fact newInstance() method of Class class internally uses newInstance() method of Constructor class.
* Whenever we call clone() on any object JVM actually creates a new object for us and copy all content of the previous object into it. 
  * Creating an object using clone method does not invoke any constructor.
  * To use clone() method on an object we need to implements Cloneable and define clone() method in it.
* Whenever we serialize and then deserialize an object JVM creates a separate object for us.
  * In deserialization, JVM doesn’t use any constructor to create the object.
  * To deserialize an object we need to implement the Serializable interface in our class.

