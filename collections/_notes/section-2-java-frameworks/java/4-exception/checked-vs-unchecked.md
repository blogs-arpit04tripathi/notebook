---
layout: post
title: Checked vs Unchecked Exceptions
permalink: /:collection/java/exceptions/checked-vs-unchecked
---


* **RuntimeExceptions** 
    - Also called ***Unchecked Exceptions***.
    - **Not check by compiler**, no need to mention in throws list.
    - **example** : NullPointerException, ClassCastException, etc.
    - **Custom Unchecked Exceptions - extend RuntimeException**.
* **Checked exceptions**
    - must be included in **throws** list.
    - should be **explicitly catched** (... throws MyException)
    - **example** : IOExceptions, etc.
    - **Custom Checked Exception - extend Exception**. There's no need to extend Throwable.

# java.lang Checked and Unchecked (RuntimeException) Exceptions

|Checked Exceptions             |   |    |
|---                            |---|---|
|ClassNotFoundException 	    |CloneNotSupportedException 	|InterruptedException	|       
|NoSuchFieldException	        |IllegalAccessException         |InstantiationException |
|ReflectiveOperationException   |NoSuchMethodException          |                       | 

|Unchecked RuntimeException |   |   |
|---                        |---|---|
| IndexOutOfBoundsException | ArrayIndexOutOfBoundsException    | StringIndexOutOfBounds            |
| ArithmeticException       | NumberFormatException             |
| NullPointerException      | UnsupportedOperationException     | EnumConstantNotPresentException   |
| SecurityException         | IllegalMonitorStateException      |
| TypeNotPresentException   | ClassCastException                | IllegalArgumentException          |
| IllegalStateException     | IllegalThreadStateException       |
| ArrayStoreException       | NegativeArraySizeException        |
