---
layout: post
title: Java Validation API
permalink: /:collection/spring/mvc/validations
---

- Java Validation API, such as Hibernate Validator, is in the project’s classpath.
- you can put annotations on properties to place constraints on their values.
- `javax.validation.constraints package`.

|Annotation   |Description|
|---          |---|
|@AssertFalse |	must be a Boolean type and be false.|
|@AssertTrue  |	must be a Boolean type and be true.|
|@DecimalMax  |	must be a number whose value is less than or equal to a given BigDecimalString value.|
|@DecimalMin  |	must be a number whose value is greater than or equal to a given BigDecimalString value.|
|@Digits      |	must be a number whose value has a specified number of digits.|
|@Future      |	must be a date in the future.|
|@Max         |	must be a number whose value is less than or equal to a given value.|
|@Min         |	must be a number whose value is greater than or equal to a given value.|
|@NotNull     |	must not be null.|
|@Null        |	must be null.|
|@Past        |	must be a date in the past.|
|@Pattern     |	must match a given regular expression.|
|@Size        |	must be either a String or a collection, or an array whose length fits within the given range.|

```java
public class Spitter {
 private Long id;
 @NotNull
 @Size(min=5, max=16)
 private String username;
 @NotNull
 @Size(min=5, max=25)
 private String password;
 @NotNull
 @Size(min=2, max=30)
 private String name; 
 ...
}
```
```java
@RequestMapping(value = "/register", method = POST)
public String processRegistration(@Valid Spitter spitter, Errors errors) {
    if (errors.hasErrors())
        return "registerForm";
    spitterRepository.save(spitter);
    return "redirect:/spitter/" + spitter.getUsername();
}
```

- If errors.hasErrors(), return registerForm to correct the input problems by user.
