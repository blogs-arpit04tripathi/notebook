---
layout: post
title: Spring MVC Introduction
permalink: /:collection/spring/mvc/introduction
---

- Developing web-based applications have challenges - state management, workflow, and validation.
  - HTTP protocol’s stateless nature.
  - Spring’s web framework is designed to help you address these concerns. 
- Spring MVC pattern
  - build web-applications that are flexible and as loosely coupled.
  - well known design pattern for designing UI based applications. 
  - decouples business logic from UI, so they can change independently without affecting each other.
- **Model-View-Controller**
  - ***Models*** - responsible for encapsulating application data for views to present. 
  - ***Views***
    - present data, without including any business logic.
    - JSP templates written with Java Standard Tag Library (JSTL)
  - ***Controller***
    - receive requests from users and invoke back-end service (business logic).
    - collect response data and prepare models for views to present.
    - Controller part is played by dispatcher servlet.
- 3-tier architecture
  - data-service-presentation.
  - MVC is actually part of presentation layer.

![mvc-tiers]({{site.cdn}}/spring/spring-mvc/mvc-tiers.png)

- The real controller in Spring MVC is **DispatchServlet** that will use the specific @Controller class to handle the URL request.
- **@Controller** - serves as **C** in MVC.
-	@Service, @Repository and your entity classes will be **M** from MVC.
- **@Service** - serve as service layer. **Here you should put your business logic**.
- **@Repository** - serve for your data access layer. Here you should put CRUD logic: insert, update, delete, select.
- JSP and other view technologies will conform **V** from MVC.
- @Controller --> @Service (through interfaces).
- @Service --> other @Service and @Repository (through interfaces).
