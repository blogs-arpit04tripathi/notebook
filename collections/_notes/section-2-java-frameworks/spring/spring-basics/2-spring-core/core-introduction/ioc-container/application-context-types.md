---
layout: post
title: ApplicationContext Types
permalink: /:collection/spring/core/ioc-container/application-context-types
---

|ApplicationContext Types||
|---|---|
|AnnotationConfigApplicationContext|	Loads Spring application context from one or more Java-based configuration classes rather than xml.|
|ClassPathXmlApplicationContext|	Loads a context definition from one or more XML files located in the classpath (including JAR files), treating context-definition files as classpath resources.|
|FileSystemXmlApplicationContext|	Loads a context definition from one or more XML files in the filesystem (specific location).|
|AnnotationConfigWebApplicationContext|	Loads a Spring web application context from one or more Java-based configuration classes.|
|XmlWebApplicationContext (Default)|	Loads context definitions from one or more XML files contained in a web application. |

- In a Spring application, an **application context** loads bean definitions and wires them together.
- Spring application context is fully responsible for the creation of and wiring of the objects that make up the application.
- With an application context in hand, you can retrieve beans from the Spring container by calling the context’s getBean() method.

`BeanFactory 	<--   ApplicationContext	<--   WebApplicationContext`

- ***ApplicationContext***
  - **AnnotationConfigApplicationContext** – For Java-based configurations, Spring offers.
  - **ClassPathXmlApplicationContext**
    - This Spring context implementation loads the Spring context from one or more XML files located in the application’s classpath.
    - Used when the beans are declared in xml.
  - **FileSystemXmlApplicationContext**
- ***WebApplicationContext***
  - AnnotationConfigWebApplicationContext
  - XmlWebApplicationContext (Default)

```java
org.springframework.context.support.ClassPathXmlApplicationContext;
public class KnightMain {
    public static void main(String[] args) throws Exception {
        ClassPathXmlApplicationContext ctx =
            new ClassPathXmlApplicationContext("META-INF/spring/knight.xml");
        Knight knight = ctx.getBean(Knight.class);
        knight.embarkOnQuest();
        ctx.close();
    }
}
```

**If i instantiate two ApplicationContext in one java application (both in main body), are these two interfaces to one central container?**  
```java
ApplicationContext context1 = new ClassPathXmlApplicationContext("Beans.xml");
ApplicationContext context2 = new ClassPathXmlApplicationContext("Beans.xml");
```
you can have multiple instances of ApplicationContexts, in that case, they will be completely isolated, each with its own configuration.
