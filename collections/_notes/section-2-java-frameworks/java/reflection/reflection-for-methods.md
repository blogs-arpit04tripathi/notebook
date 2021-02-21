---
layout: post
title: Reflection for Methods
permalink: /:collection/java/reflection/reflection-for-methods
---

# getMethod()
* Get Public Method 
* need to pass the method name and parameter types of the method. 
* If the method is not found in the class, reflection API looks for the method in superclass.

```java
Method method = Class.forName("java.util.HashMap").getMethod("put", Object.class, Object.class);
//get method parameter types, prints "[class java.lang.Object, class java.lang.Object]"
System.out.println(Arrays.toString(method.getParameterTypes()));
//get method return type, return "class java.lang.Object", class reference for void
System.out.println(method.getReturnType());
//get method modifiers
System.out.println(Modifier.toString(method.getModifiers())); //prints "public"
```

# invoke()
* Invoking Public Method
* If the method is static, we can pass NULL as object argument.

```java
Method method = Class.forName("java.util.HashMap").getMethod("put", Object.class, Object.class);
Map<String, String> hm = new HashMap<>();
method.invoke(hm, "key", "value");
System.out.println(hm); // prints {key=value}
```

# getDeclaredMethod()
* Invoking Private Methods
* can use to get the private method and then turn off the access check to invoke it.

```java
//invoking private method
Method method = Class.forName(com.journaldev.reflection.BaseClass.getDeclaredMethod("method3", null);
method.setAccessible(true);
method.invoke(null, null); // prints "Method3"
```
