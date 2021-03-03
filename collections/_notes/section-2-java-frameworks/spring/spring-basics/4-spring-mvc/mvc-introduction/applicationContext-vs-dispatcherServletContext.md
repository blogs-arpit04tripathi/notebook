---
layout: post
title: ApplicationContext vs DispatcherServletContext
permalink: /:collection/spring/mvc/applicationContext-vs-dispatcherServletContext
---
 
- Spring lets you define multiple contexts in a parent-child hierarchy.
- **applicationContext.xml**
  - defines beans for "root webapp context", i.e. the context associated with the webapp.
  - used to contain beans that are shared between all servlets in a webapp.
- **spring-servlet.xml** defines beans for one servlet's app context.
  - There can be many servlets in a webapp.
  - spring1-servlet.xml , spring2-servlet.xml.
- ***Beans in spring-servlet.xml can reference beans in applicationContext.xml, but not vice versa***.
- ***All Spring MVC controllers must go in the spring-servlet.xml context***.

