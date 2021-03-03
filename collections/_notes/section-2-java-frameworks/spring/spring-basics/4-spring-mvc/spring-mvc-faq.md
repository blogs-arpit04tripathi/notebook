---
layout: post
title: Spring MVC - FAQ
permalink: /:collection/spring/mvc/faq
---

- TOC
{:toc}

<hr><br>

# Can we call servlet destory() from service()?
- destory() is part of servlet life cycle methods
  - it is used to kill the servlet instance.
  - Servlet Engine is used to call destory().
- If you call destroy method from service()
  - it just execute the code written in the destory()
  - but it wont kill the servlet instance.
  - destroy() will be called before killing the servlet instance by servlet engine.

**How to use CSS, JavaScript and Images in Spring MVC Web App**
```xml
<mvc:resources mapping="/resources/**" location="/resources/"></mvc:resources>
<img src="${pageContext.request.contextPath}/resources/images/spring-logo.png"> 
```
```jsp
<head>
   <link rel="stylesheet" type="text/css" href="${pageContext.request.contextPath}/resources/css/my-test.css">
   <script src="${pageContext.request.contextPath}/resources/js/simple-test.js"></script>
</head>
<body>
   <h2>Spring MVC Demo - Home Page</h2>
   <a href="showForm">Plain Hello World</a>
   <br><br>
   <img src="${pageContext.request.contextPath}/resources/images/spring-logo.png" />
   <br><br>
   <input type="button" onclick="doSomeWork()" value="Click Me"/>
</body>
</html>
```

```java
@RequestMapping("/processForm")
public String processForm(
    @Valid @ModelAttribute("customer") Customer theCustomer,
    BindingResult theBindingResult) {
        ...
    }
}
```
The Errors or BindingResult parameters have to follow the model object that is being bound immediately.

**@InitBinder**

Make integer field mandatory and handle string in input field
```java
@NotNull(message="is required")
@Min(value=0, message="must be greater than or equal to zero")
@Max(value=10, message="must be less than or equal to 10")
private Integer freePasses;

//messages.properties
typeMismatch.customer.freePasses=Invalid number

//servlet.xml
<bean id="messageSource" class="org.springframework.context.support.ResourceBundleMessageSource">
    <property name="basenames" value="resources/messages" />
</bean>
```
