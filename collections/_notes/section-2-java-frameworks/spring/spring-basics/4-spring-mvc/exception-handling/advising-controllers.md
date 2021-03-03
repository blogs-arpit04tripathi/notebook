---
layout: post
title: Advising controllers
permalink: /:collection/spring/mvc/advising-controllers
---

- ***Centralized Exception Handling***
  - handling exceptions across multiple controllers.
  - applied globally across all @RequestMapping
  - `@ControllerAdvice` annotation is itself annotated with @Component.
    - will be picked up by component-scanning
- @ControllerAdvice class having following kinds of methods:
  - `@ExceptionHandler`
  - `@InitBinder`
  - `@ModelAttribute`
- Any controller method throw DuplicateSpittleException
  - duplicateSpittleHandler() method will be called to handle the exception.

```java
package spitter.web;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;

@ControllerAdvice
public class AppWideExceptionHandler {
    @ExceptionHandler(DuplicateSpittleException.class)
    public String duplicateSpittleHandler() {
        return "error/duplicate";
    }
}
```
