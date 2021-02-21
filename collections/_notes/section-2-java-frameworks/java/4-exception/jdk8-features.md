---
layout: post
title: JDK8 Exception Features
permalink: /:collection/java/exceptions/jdk8-features
---

- TOC
{:toc}

<hr><br>

# try-with-resources
automates the process of releasing a resource, such as a file, when it is no longer needed.
```java
try (BufferedReader br = new BufferedReader(new FileReader(path))) {
   System.out.println("MyResource created in try-with-resources");
} catch (Exception e) {
    e.printStackTrace();
}
```

# multi-catch
* `catch(ArithmeticException | ArrayIndexOutOfBoundsException e)`
    - 2 or more exceptions in single catch.
    - Each multi-catch parameter is implicitly **final**.
* final rethrow or more precise rethrow
    - restricts the type of exceptions that can be rethrown to only those checked exceptions that the associated **try** block throws, that are not handled by a preceding **catch** clause, and that are a subtype or supertype of the parameter.
