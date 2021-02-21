---
layout: post
title: Custom Exceptions
permalink: /:collection/java/exceptions/custom-exceptions
---


* Exception class – adds no new methods, inherit those provided by Throwable. 
* Your subclasses **don’t need to actually implement anything – their existence in the type system makes them exceptions**.

```java
public class MyException extends Exception {
    private static final long serialVersionUID = 4664456874499611218 L;
    private String errorCode = "Unknown_Exception";
    public MyException(String message, String errorCode) {
        super(message);
        this.errorCode = errorCode;
    }
    public String getErrorCode() {
        return this.errorCode;
    }
}
```

|Methods Defined by Throwable|||
|---|---|---|
|**Throwable getCause( )** 	    | **Throwable initCause(Throwable causeExc)**   |
|**String getMessage( )** 	    | String getLocalizedMessage( )                 |
|**void printStackTrace( )**    | void printStackTrace(PrintStream stream)      | void printStackTrace(PrintWriter stream) |
|**String toString( )**         | **StackTraceElement[ ] getStackTrace( )**     |
