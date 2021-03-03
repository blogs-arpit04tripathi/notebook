---
layout: post
title: Spring IOC Container Types
permalink: /:collection/spring/core/ioc-container/types
---

1. Bean factories (org.springframework.beans.factory.BeanFactory)
    - Simplest of containers, providing basic support for DI. 
2. Application contexts  (o.s.context.ApplicationContext) 
    - Build on the top of a bean factory.
    - Extra functionality
      - simple integration with Spring's AOP, application-framework services, such as the ability to resolve text messages from a properties file (for I18N) 
      - ability to publish application events to interested event listeners and application layer specific context (e.g. WebApplicationContext) for web application. 

|BeanFactory|ApplicationContext|
|---|---|
|It is an interface defined in org.springframework.beans.factory.BeanFactory	|It is an interface defined in org.springframework.context.ApplicationContext|
|It uses Lazy initialization	|It uses Eager/ Aggressive initialization|
|It explicitly provides a resource object using the syntax	|It creates and manages resource objects on its own|
|It doesn’t supports internationalization	|It supports internationalization |
|It doesn’t supports annotation based dependency | It supports annotation based dependency|

```java
// IOC Containers
/* Bean Factory */
Resource resource=new ClassPathResource("applicationContext.xml");
BeanFactory factory=new XmlBeanFactory(resource);

/* ApplicationContext */
ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
ApplicationContext context = new FileSystemXmlApplicationContext("c:/knight.xml");
ApplicationContext context = new AnnotationConfigApplicationContext(com.KnightConfig.class);
```
```java
// Context methods
context.getBean(Knight.class);              // Type Safe
context.getBean(Knight.class, "knight");
context.getBeansOfType(Knight.class)        // No Type Safety, Map is not parameterized
(Knight) context.getBean("knight");
```