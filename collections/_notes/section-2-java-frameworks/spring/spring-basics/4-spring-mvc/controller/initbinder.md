---
layout: post
title: Annotation @Initbinder
permalink: /:collection/spring/mvc/initbinder
---

- @Initbinder to customize the request being sent to the controller.
  - defined in controller, helps in controlling and formatting each and every request that comes to it.
  - used with the methods which initializes WebDataBinder
  - works as a preprocessor for each request coming to the controller.

![]({{site.cdn}}/spring/spring-mvc/init-binder.png)

```java
@InitBinder
public void initBinder(WebDataBinder dataBinder) {
    StringTrimmerEditor stringTrimmerEditor = new StringTrimmerEditor(true);
    dataBinder.registerCustomEditor(String.class, stringTrimmerEditor);
}
```
```java
public class Student {
    private String Id;
    private String firstName;

    @NotNull(message = "is required")
    @Size(min = 1, message = "is required")
    private String lastName; // validation done to check if lastname is NULL

    @Max(value = 10, message = "Value should between 0 and 10")
    @Min(value = 0, message = "Value should between 0 and 10")
    private String standard;
    private String Age;
}
```

- WebDataBinder extends DataBinder.
- It can be used to register custom formatter, validators and PropertyEditors.

```java
WebDataBinder.addCustomFormatter(..);
WebDataBinder.addValidators(..);
WebDataBinder.registerCustomEditor(..);
```