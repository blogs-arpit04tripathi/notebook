---
layout: post
title: Custom Validation Annotation
permalink: /:collection/spring/mvc/custom-validation-annotation
---

```java
@CourseCode
```
```java
@Constraint(validatedBy=CourseCodeConstraintValidator.class)
@Target({ElementType.METHOD, ElementType.FIELD})
@Retention(RetentionPolicy.RUNTIME)
public @interface CourseCode{
  public String value() default "LUV";
  public String message() default "must start with LUV";
  public Class<?>[] groups default {};
  public Class<? extends Payload>[] payload default {};
}
```
```java
public class CourseCodeConstraintValidator implements ConstraintValidator<CourseCode, String>{

  private String coursePrefix;
  
  @Override
  public void initialize(CourseCode courseCode){
    coursePrefix = courseCode.value();
  }

  @Override
  public boolean isValid(String code, ConstraintValidatorContext ctx){
    boolean result = code.startsWith(coursePrefix);
    return result;
  }
}
```
