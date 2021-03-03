---
layout: post
title: Handling exceptions
permalink: /:collection/spring/mvc/handling-mvc-exceptions
---

- Spring offers a ways to translate exceptions to responses.
  - Certain Spring exceptions are automatically mapped to specific HTTP status codes.
  - An exception can be annotated with **@ResponseStatus** to map it to an HTTP status code.
  - A method can be annotated with **@ExceptionHandler** to handle the exception.

# @ResponseStatus
- By default, response status code is 500 (Internal Server Error).

```java
@ResponseStatus(value=HttpStatus.NOT_FOUND, reason="Spittle Not Found")
public class SpittleNotFoundException extends RuntimeException { }
```
```java
@RequestMapping(value = "/{spittleId}", method = RequestMethod.GET)
public String spittle(@PathVariable long spittleId, Model model) {
    Spittle spittle = spittleRepository.findOne(spittleId);
    if (spittle == null)
        throw new SpittleNotFoundException();
    model.addAttribute(spittle);
    return "spittle";
}
```

# @ExceptionHandler methods
- @ExceptionHandler methods can handle exceptions thrown from any handler method in the same controller class.

```java
@ExceptionHandler(DuplicateSpittleException.class)
public String handleDuplicateSpittle() {
  return "error/duplicate";
}
```
```java
@RequestMapping(method=RequestMethod.POST)
public String saveSpittle(SpittleForm form, Model model) {
  spittleRepository.save(new Spittle(null, form.getMessage(), new Date(), form.getLongitude(), form.getLatitude()));
  return "redirect:/spittles";
}
```

**Without @ExceptionHandler methods**

```java
@RequestMapping(method = RequestMethod.POST)
public String saveSpittle(SpittleForm form, Model model) {
    try {
        spittleRepository.save(new Spittle(null, form.getMessage(), new Date(), form.getLongitude(), form.getLatitude()));
        return "redirect:/spittles";
    } catch (DuplicateSpittleException e) {
        return "error/duplicate";
    }
}
```

# Exception Handling References
- [exception-handling-in-spring-mvc](https://spring.io/blog/2013/11/01/exception-handling-in-spring-mvc){:target="_blank"}
- [best-practices-exceptions-java](https://stackify.com/best-practices-exceptions-java){:target="_blank"}

# Spring Exceptions - Mapping to HTTP status codes

Exceptions thrown by Spring when something going wrong in DispatcherServlet or while performing validation.

|Spring exception|	HTTP status code|
|---|---|	
|BindException| 400 - Bad Request|
|ConversionNotSupportedException |500 - Internal Server Error|
|HttpMediaTypeNotAcceptableException |406 - Not Acceptable|
|HttpMediaTypeNotSupportedException |415 - Unsupported Media Type|
|HttpMessageNotReadableException |400 - Bad Request|
|HttpMessageNotWritableException |500 - Internal Server Error|
|HttpRequestMethodNotSupportedException |405 - Method Not Allowed|
|MethodArgumentNotValidException |400 - Bad Request|
|MissingServletRequestParameterException |400 - Bad Request|
|MissingServletRequestPartException| 400 - Bad Request|
|NoSuchRequestHandlingMethodException| 404 - Not Found|
|TypeMismatchException |400 - Bad Request|

