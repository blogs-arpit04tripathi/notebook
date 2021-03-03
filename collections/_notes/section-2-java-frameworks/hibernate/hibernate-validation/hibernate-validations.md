---
layout: post
title: Hibernate Validations
permalink: /:collection/hibernate/validations
---

**What is Hibernate Validator Framework?**  
-	Data validation is integral part of any application. You will find data validation at presentation layer with the use of Javascript, then at the server side code before processing it. Also data validation occurs before persisting it, to make sure it follows the correct format.
-	Validation is a cross cutting task, so we should try to keep it apart from our business logic. That’s why JSR303 and JSR349 provides specification for validating a bean by using annotations. Hibernate Validator provides the reference implementation of both these bean validation specs. 

```xml
<!-- Java bean validation API - Spec -->
<dependency>
    <groupId>javax.validation</groupId>
    <artifactId>validation-api</artifactId>
    <version>2.0.1.Final</version>
</dependency>
 
<!-- Hibernate validator - Bean validation API Implementation -->
<dependency>
    <groupId>org.hibernate</groupId>
    <artifactId>hibernate-validator</artifactId>
    <version>6.0.11.Final</version>
</dependency>
 
<!-- Verify validation annotations usage at compile time -->
<dependency>
  <groupId>org.hibernate</groupId>
  <artifactId>hibernate-validator-annotation-processor</artifactId>
  <version>6.0.11.Final</version>
</dependency>
 
<!-- Unified Expression Language - Spec -->
<dependency>
    <groupId>javax.el</groupId>
    <artifactId>javax.el-api</artifactId>
    <version>3.0.1-b06</version>
</dependency>
 
<!-- Unified Expression Language - Implementation -->
<dependency>
    <groupId>org.glassfish.web</groupId>
    <artifactId>javax.el</artifactId>
    <version>2.2.6</version>
</dependency>
```

```java
    @NotNull(message = "Please enter id")
    private Long id;
 
    @Size(max = 20, min = 3, message = "{user.name.invalid}")
    @NotEmpty(message = "Please enter name")
    private String name;
 
    @Email(message = "{user.email.invalid}")
    @NotEmpty(message = "Please enter email")
    private String email;
```
