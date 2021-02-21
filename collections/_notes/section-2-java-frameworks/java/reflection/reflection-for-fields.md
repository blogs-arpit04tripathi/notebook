---
layout: post
title: Reflection for Fields
permalink: /:collection/java/reflection/reflection-for-fields
---

# Get Public Field
* to get specific public field of a class through getField() method. 
* look for the field in the specified class reference and then in the super interfaces and then in the super classes.
* NoSuchFieldException, if no field found.

```java
Field field = Class.forName("com.journaldev.reflection.ConcreteClass").getField("interfaceInt");
```

# getDeclaringClass()
* Field Declaring Class

```java
try {
    Field field = Class.forName("com.journaldev.reflection.ConcreteClass").getField("interfaceInt");
    Class << ? > fieldClass = field.getDeclaringClass();
    System.out.println(fieldClass.getCanonicalName());
    //prints com.journaldev.reflection.BaseInterface
} catch (NoSuchFieldException | SecurityException e) {
    e.printStackTrace();
}
```

# getType()
* Get Field Type
* returns the Class object for the declared field type.
* If field is primitive type, it returns the wrapper class object.

```java
Field field = Class.forName("com.journaldev.reflection.ConcreteClass").getField("publicInt");
Class<?> fieldType = field.getType();
System.out.println(fieldType.getCanonicalName()); //prints int
```

# Get/Set Public Field Value
* We can get and set the value of a field in an Object using reflection.

```java
Field field = Class.forName("com.journaldev.reflection.ConcreteClass").getField("publicInt");
ConcreteClass obj = new ConcreteClass(5);
System.out.println(field.get(obj)); //prints 5
field.setInt(obj, 10); //setting field value to 10 in object
System.out.println(field.get(obj)); //prints 10
```

* get() method return Object, so if field is primitive type, it returns the corresponsing Wrapper Class.
* If the field is static, we can pass Object as null in get() method.
* There are several set*() methods to set Object to the field or set different types of primitive types to the field. 
* We can get the type of field and then invoke correct function to set the field value correctly. 
* If the field is final, the set() methods throw java.lang.IllegalAccessException.

# Get/Set Private Field Value
* We know that private fields and methods can’t be accessible outside of the class but using reflection we can get/set the private field value by turning off the java access check for field modifiers.

```java
Field privateField = Class.forName("com.journaldev.reflection.ConcreteClass").getDeclaredField("privateString");
//turning off access check with below method call
privateField.setAccessible(true);
ConcreteClass objTest = new ConcreteClass(1);
System.out.println(privateField.get(objTest)); // prints "private string"
privateField.set(objTest, "private string updated");
System.out.println(privateField.get(objTest)); //prints "private string updated"
```