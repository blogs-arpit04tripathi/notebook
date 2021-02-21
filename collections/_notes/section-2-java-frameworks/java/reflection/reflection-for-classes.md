---
layout: post
title: Reflection for Classes
permalink: /:collection/java/reflection/reflection-for-classes
---

- TOC
{:toc}

<hr><br>

# java.lang.Class 
* java.lang.Class is the entry point for all the reflection operations. 
* For every type of object, JVM instantiates an immutable instance of java.lang.Class that provides methods to examine the runtime properties of the object and create new objects, invoke its method and get/set object fields.

The java.lang.Class class performs mainly two tasks:
* provides methods to get the metadata of a class at run time.
* provides methods to examine and change the run time behavior of a class.

|Method	| Description|
---|---
String getName()|returns the class name
static Class forName(String className) throws ClassNotFoundException|loads the class and returns the reference of Class.
newInstance() throws InstantiationException ,IllegalAccessException|creates new instance.
boolean isInterface()	|checks if it is interface.
boolean isArray()	    |checks if it is array.
boolean isPrimitive()	|checks if it is primitive.
Class getSuperclass()	|returns the superclass class reference.
Field[] getDeclaredFields() throws SecurityException|returns the total number of fields of this class.
Method[] getDeclaredMethods() throws SecurityException|returns the total number of methods of this class.
Constructor[] getDeclaredConstructors() throws SecurityException|returns total number of constructors of this class.
Method getDeclaredMethod(String name,Class[] parameterTypes) throws NoSuchMethodException,SecurityException	|returns the method class instance.
public void setAccessible(boolean status) throws SecurityException	|sets the accessibility of the method.

**How to get the object of Class class?**
* forName()
    - is used to load the class dynamically, returns the instance of Class class.
    - To be used to know the fully qualified name of class. Cannot be used for primitive types.
    - Class c=Class.forName("com.example.ClassA");
* getClass() of Object class	
    - it can be used with primitives.
	- Class c=obj.getClass()
* .class	
    - It can be used for primitive data type also.
	- MyClass.class boolean.class

# newInstance() 
* newInstance() method of Class  and Constructor are used to create a new instance of the class. 
* newInstance() method of Class can invoke zero-argument constructor.
* newInstance() method of Constructor can invoke any number of arguments. So, Constructor is preferred over Class.
* public Object invoke(Object method, Object... args) throws IllegalAccessException, IllegalArgumentException, InvocationTargetException is used to invoke the method.

# getCanonicalName() 
* returns the canonical name of the underlying class. 
* java.lang.Class uses Generics, helps frameworks in making sure that the Class retrieved is subclass of framework Base Class.

# getSuperclass() 
* returns the super class of the class. 
* If this Class represents either of the Object class, an interface, a primitive type, or void, then null is returned. 
* If this object represents an array class then the Class object representing the Object class is returned.

# getClasses() 
* returns an array containing Class objects representing all the public classes, interfaces and enums that are members of the class represented by this Class object. This includes public class and interface members inherited from superclasses and public class and interface members declared by the class. This method returns an array of length 0 if this Class object has no public member classes or interfaces or if this Class object represents a primitive type, an array class, or void. 
* `Class<?>[] classes = concreteClass.getClasses();`

# How to call private method from another class in java

```java
class A {
    private void message() {
        System.out.println("hello java");
    }
    private void cube(int n) {
        System.out.println(n * n * n);
    }
}
class M {
    public static void main(String args[]) throws Exception {
        Class c = A.class;
        Object obj = c.newInstance();
        Method m1 = c.getDeclaredMethod("message", null);
        Method m = c.getDeclaredMethod("cube", new Class[] {
            int.class
        });
        m1.setAccessible(true);
        m.setAccessible(true);
        m1.invoke(o, null);
        m.invoke(obj, 4);
    }
}
```

# Example in eWMS

```java
Class - PullSeqDateGeneratorImpl
Method - buildPullSeqDate
public void buildPullSeqDate(String detailCode, String formulaeValue, Map < Integer, String > pullSeq, String receivingYear) throws CodeDateServiceException {
    try {
        // load the PullSeqFormulaeMethod at runtime
        Class << ? > pullSeqFormulaeMethod = Class.forName("com.service.PullSeqFormulaeMethod");
        Object pullSeqFormulaeMethodObj = pullSeqFormulaeMethod.newInstance();
        Method pullSeqMap = pullSeqFormulaeMethod.getDeclaredMethod("setValueOfFormulaeCode" + detailCode, String.class, Map.class, String.class);
        pullSeqMap.invoke(pullSeqFormulaeMethodObj, formulaeValue, pullSeq, receivingYear);
    }
}
```

# javap tool
* The **javap command** disassembles a class file. The javap command displays information about the fields, constructors and methods present in a class file.
* **javap fully_class_name**
* examples
    - javap java.lang.Object
	- javap -c Simple

|Option	    | Description |
---|---
-help	    | prints the help message.
-l	        | prints line number and local variable
-c	        | disassembles the code, relects bytecode.
-s	        | prints internal type signature
-sysinfo	| shows system info (path, size, date, MD5 hash)
-constants	| shows static final constants
-version	| shows version information

# getDeclaredClasses()

```java
//getting all of the classes, interfaces, and enums that are explicitly declared in ConcreteClass
Class<?>[] explicitClasses = Class.forName("com.a04t.ConcreteClass").getDeclaredClasses();
System.out.println(Arrays.toString(explicitClasses));
```

# getDeclaringClass()
* returns the Class object representing the class in which it was declared.

```java
Class<?> innerClass = Class.forName("com.a04t.ConcreteClass$ConcreteClassDefaultClass");
System.out.println(innerClass.getDeclaringClass().getCanonicalName());
System.out.println(innerClass.getEnclosingClass().getCanonicalName());
```

# getPackage() 
* returns the package for this class. The class loader of this class is used to find the package. 

```java
System.out.println(Class.forName("com.a04t.BaseInterface").getPackage().getName());
```

# getModifiers() 
* returns the int representation of the class modifiers, 
* can use java.lang.reflect.Modifier.toString() method to get it in the string format as used in source code.

```java
System.out.println(Modifier.toString(concreteClass.getModifiers()));
System.out.println(Modifier.toString(Class.forName("com.journaldev.reflection.BaseInterface").getModifiers()));
```

# getTypeParameters()
* returns the array of TypeVariable if there are any Type parameters associated with the class. 
* The type parameters are returned in the same order as declared.

```java
TypeVariable<?>[] typeParameters = Class.forName("java.util.HashMap").getTypeParameters();
for(TypeVariable<?> t : typeParameters)
	System.out.print(t.getName()+",");
```

# getGenericInterfaces()
* Get Implemented Interfaces
* returns array of interfaces implemented by the class with generic type information. 
* can also use getInterfaces() to get the class representation of all the implemented interfaces.

```java
Type[] interfaces = Class.forName("java.util.HashMap").getGenericInterfaces();
//prints "[java.util.Map<K, V>, interface java.lang.Cloneable, interface java.io.Serializable]"
System.out.println(Arrays.toString(interfaces));
//prints [interface java.util.Map,interface java.lang.Cloneable,interface java.io.Serializable]
System.out.println(Arrays.toString(Class.forName("java.util.HashMap").getInterfaces()));
```

# getMethods()
* Get All Public Methods
* returns the array of public methods of the Class including public methods of it’s superclasses and super interfaces.

```java
Method[] publicMethods = Class.forName("com.journaldev.reflection.ConcreteClass").getMethods();
//prints public methods of ConcreteClass, BaseClass, Object
System.out.println(Arrays.toString(publicMethods));
```

# getConstructors()
* Get All Public Constructors 
* method returns the list of public constructors of the class reference of object.

```java
//Get All public constructors
Constructor<?>[] publicConstructors = Class.forName("com.journaldev.reflection.ConcreteClass").getConstructors();
//prints public constructors of ConcreteClass
System.out.println(Arrays.toString(publicConstructors));
```

# getFields()
* Get All Public Fields
* returns the array of public fields of the class including public fields of it’s super classes and super interfaces.

```java
//Get All public fields
Field[] publicFields = Class.forName("com.journaldev.reflection.ConcreteClass").getFields();
//prints public fields of ConcreteClass, it's superclass and super interfaces
System.out.println(Arrays.toString(publicFields));
```

# getAnnotations()
* Get All Annotations
* returns all the annotations for the element, we can use it with class, fields and methods also.
* only annotations available with reflection are with retention policy of RUNTIME.

```java
java.lang.annotation.Annotation[] annotations = Class.forName("com.journaldev.reflection.ConcreteClass").getAnnotations();
//prints [@java.lang.Deprecated()]
System.out.println(Arrays.toString(annotations));
```
