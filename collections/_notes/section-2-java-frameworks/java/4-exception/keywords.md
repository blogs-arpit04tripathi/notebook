---
layout: post
title: Exception Handling Keywords
permalink: /:collection/java/exceptions/keywords
---

- TOC
{:toc}

<hr><br>

# throw
to throw explicitly.
```java
throw new NullPointerException("demo");
```

# throws
unhandled checked exception thrown by a method.
```java
type method-name(parameter-list) throws exception-list{
  ... body of method ...
}
```

# try-catch
- multiple **catch** 
- **catch exception subclasses should be before catch for any of their superclasses**, else ***unreachable code*** compile-time-error.
- **No matching catch, JRE system will handle the exception**.
- Unhandled method exception must be declared in ***throws*** clause, so caller can guard themselves against that exception.

```java
try{
    ...
} catch (ExceptionType1 exOb) {
    ...
} catch (ExceptionType2 exOb) {
    ...
} finally {
    ...
}
```

# finally 
* execute **irrespective of an exception** after try block.
* exception thrown, **finally executes even for no matching catch**.
* useful for **closing resources allocated in the method**. 
* finally clause is **optional**. 
* minimum **try-catch** or **try-finally**.

# Returning value from method having try-catch-finally blocks

* **Case 1**:  return after try-catch-finally blocks ie. just before end of method.
* **Case 2**:  return inside both try block & catch block.
* **Case 3**:  return as last statement in finally block only.
	- **Reason**: finally block always be executed except when ***System.exit(0);*** is invoked explicitly.
	- **Error**: any statement after finally block will result in compile-time error stating “Unreachable code”
* **Case 4.A**:  return inside try block & at the end of method
* **Case 4.B**: return inside both try block & finally block; but no statement after finally block
* **Case 5.A**: return inside catch block & at the end of method.
* **Case 5.B**: return inside both catch block & finally block; but no statement after finally block.
* **Case 6**: return inside try, catch & finally ; but return value will be overridden by return statement in the finally block

```java
public static int divide() {
    try {
        int d = 10 / 5;
        d = 10 / 0;
        System.out.println("want to return 0");
        return 0;
    } catch (Exception e) {
        System.out.println("Exception Caught.");
        return -1;
    } finally {
        // return value is always overridden
        System.out.println("finally Block");
        return 100;
    }
}
```
```
Hello World
Exception Caught.
finally Block
Divide Result : 100
```

|superclass method|subclass method|
|---|---|
|no exception        | No exception or unchecked exceptions *(but strictly no checked exception)*|
|unchecked exception | No exception or unchecked exceptions *(but strictly no checked exception)*|
|checked exception   | No exception or unchecked exceptions or same/subclass of checked exception|

These hold true, even if combination of both checked & unchecked exception is declared in parent class method.
