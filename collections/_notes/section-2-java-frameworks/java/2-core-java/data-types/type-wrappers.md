---
layout: post
title: Type Wrappers
permalink: /:collection/java/type-wrappers
---


Type wrappers - encapsulate a primitive type within an object.

|Type Wrapper|  |Get Primitive|
|---        |---|---|
|Boolean    | Boolean(boolean boolValue) , Boolean(String boolString)   |
|Double     |                                                           | double doubleValue( ) |
|Integer    | Integer(int num) , Integer(String str)	                | int intValue( )       |
|Float      |                                                           | float floatValue( )   |
|Short      |                                                           | short shortValue( )   |
|Long       |                                                           | long longValue( )     |
|Byte       |                                                           | byte byteValue( )     |
|Character  | Character(char ch)                                        | char charValue( )     |

* If str is not a valid numeric value, NumberFormatException.
* Byte, Short, Integer, Long, Float, Double - inherit the abstract class Number.
* boxing – primitive to Object
* unboxing – Object to primitive

```java
Integer iOb = new Integer(100);
int i = iOb.intValue();
```

* **Autoboxing** - automatically primitive to Object (wrapper, encapsulated, boxed).
* **Auto-unboxing** - boxed object value is automatically extracted (unboxed). No need to call intValue(), doubleValue() etc.

```java
Integer iOb = 100; 	// autobox an int
int i = iOb;   		// auto-unbox
++iOb;         		// unboxes iOb,performs the increment, and then Reboxes the result back into iOb.
Double a, b, c;    	// A bad use of autoboxing/unboxing!
a = 10.0; b = 4.0; 	// far less efficient than what could be written using double
c = Math.sqrt(a*a + b*b);
```
