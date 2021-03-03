---
layout: post
title: Spring Framework
permalink: /:collection/spring/
---

# References
- [Spring Annotations (Quick Reference)](https://springframework.guru/spring-framework-annotations){:target="_blank"}

# Latest in Spring
- [New in Spring](latest) - todo
- [Spring Framework Architecture](architecture)

# Spring Core
- [Introduction to Spring](introduction)
- [POJO vs Java Beans vs EJB](core/pojo-bean-ejb)
- [Spring IOC Container](core/ioc-container)
  - [IOC Container Types](core/ioc-container/types)
    - BeanFactory
    - [Application Context](core/ioc-container/application-context)
      - [Application Context Types](core/ioc-container/application-context-types)
- Spring Beans
  - [Lifecycle of Bean](bean-lifecycle)
  - [Spring Bean Definition Metadata](bean-metadata)
  - [@Bean and @Configuration](annotation/bean)
  - [Bean Scopes](bean-scopes)
    - [Working with request and session scope](bean-scopes/request-and-session-scope)
  - [Mixing configurations - Java and Xml](mixing-configs)
    - @Import
- Dependency Injection - DI
  - [Loose coupling through DI](loose-coupling-via-di)
  - [Types of Dependency Injection](types-dependency-injection)
    - [Constructor vs Setter Injection](constructor-vs-setter-injection)
- [Wiring Beans](wiring-beans)
  - [Automatic Wiring](automatic-wiring) - @ComponentScan
    - [Autowiring Modes](autowiring-modes)
  - [Ambiguity In Autowiring](ambiguity-in-autowiring)
    - [@Primary](annotation/primary)
    - [@Qualifier](annotation/qualifier)
      - [Create custom Qualifier - @Cold](annotation/custom-qualifier)
  - [Wiring Beans with Java](wiring-beans-with-java) - 3rd party classes
- [Conditional Beans](conditional-beans)
  - [Configuring profile beans](configuring-profile-beans)
    - [Activating profiles](activating-profiles)
- [Property value - runtime injection](runtime-value-injection)
  - [Resolving Property Placeholders](resolving-property-placeholders) - @Value
  - [Wiring with the Spring Expression Language](wiring-with-spel)
- [@Order](annotation/order)

# Spring AOP
- [Spring AOP Introduction](aop/introduction)
  - [Key Terminologies](aop/key-terms)
  - [Declarative programming through aspects](aop/declarative-programming-with-aspects)
- [Spring AOP features](aop/aop-features)
  - [Types of Weaving](aop/types-of-weaving)
- Creating annotated aspects
  - [Writing pointcuts](aop/writing-jp)
    - [AspectJ pointcut expression language](aop/pointcut-expression-language)
    - [Types of Advices](aop/types-of-advices)
  - [Defining an aspect](aop/defining-aspects)
    - [Parameters in advice](aop/params-in-advice)
    - [Ordering Aspects](aop/ordering-aspects)
- [AOP Introduction](aop/introductions)
- [Eliminating boilerplate code with aspects](aop/eliminate-bolierplate-with-aspects)
- [Declaring aspects in XML](aop/aspects-in-xml)

# Spring MVC - Model View Controller
- [Spring MVC Introduction](mvc/introduction)
  - [MVC Flow](mvc/flow)
  - [HandlerInterceptorAdapter](mvc/handler-interceptor-adapter)
  - [DispatcherServlet](mvc/dispatcher-servlet)
    - [Enabling Spring MVC](mvc/enabling-mvc)
  - [Application Context vs DispatcherServletContext](mvc/applicationContext-vs-dispatcherServletContext)
  - [Alternate Spring MVC configuration](mvc/alternate-config)
- [Writing a controller](mvc/writing-controller)
  - [Accepting request input](mvc/request-inputs) - @PathVariable, @RequestParam
  - [Carrying data across redirect requests](mvc/data-across-redirect-urls)
  - [Java Validation API](mvc/validations)
    - [Custom Validation Annotation](mvc/custom-validation-annotation)
  - [@Initbinder](mvc/initbinder)
- [Rendering web views](mvc/render-web-views)
  - [View resolver Types](mvc/view-resolver-types)
- [Multipart Requests](mvc/multipart)
  - [StandardServletMultipartResolver](mvc/multipart/StandardServletMultipartResolver)
  - [CommonsMultipartResolver](mvc/multipart/CommonsMultipartResolver)
  - [Handle multipart request](mvc/multipart/handle-request) - @RequestPart
- Exception Handling
  - [Handling exceptions](mvc/handling-mvc-exceptions) - @ExceptionHandler, @ResponseStatus
  - [Advising controllers](mvc/advising-controllers) - @ControllerAdvice
- [Spring MVC - FAQ](mvc/faq)
- [Creating JSP views](mvc/jsp-views)
  - [Spring General Tag Library](mvc/taglib)
  - [Displaying Internationalized Messages](mvc/internationalized-messages)
  - [Creating URLs](mvc/create-url)
  - [Escaping Content](mvc/escape-content)

# Spring REST
- [Spring REST Introduction](rest/introduction)
- [Creating REST endpoint](rest/first-endpoint)
  - [ContentNegotiatingViewResolver](rest/contentNegotiatingViewResolver)
    - [ContentNegotiationManager Configuration](rest/contentNegotiationManager/configuration)
  - [HttpMessageConverters](rest/HttpMessageConverter)
  - [@RestController](rest/rest-controller) - @RequestBody, @ResponseBody
  - [ResponseEntity](rest/response-entity)
  - [Difference - @Component, @Service, @Repository, @Controller](rest/difference-rest-annotations)
  - [POST vs PUT vs PATCH](rest/post-vs-put-vs-patch)
- [Consuming REST resources - RestTemplate](rest/consume-rest-resources)
  - [GET](rest/get-resources)
  - [PUT](rest/put-resources)
  - [DELETE](rest/delete-resources)
  - [POST](rest/post-resources)
  - [Exchange](rest/exchange-resources) - request headers
- [Handler Mapping](rest/handler-mapping)
  - [HandlerInterceptor](rest/handler-interceptor)
- [PropertyPlaceholderConfigurer and ReloadableResourceBundleMessageSource](rest/propertyPlaceholderConfigurer-and-reloadableResourceBundleMessageSource)
- [Singleton Bean to Multiple Request](rest/singleton-bean-to-multiple-request)

# Spring Security
- [Spring Security](security)

# Spring Data
- [Spring Data](data)
- [Difference - @EntityScan vs @ComponentScan](data/entityscan-vs-componentscan) - todo
- [Spring Data Rest](data/rest)

# Spring Boot
- [SpringBoot Introduction](boot/introduction)
  - [Spring vs SpringBoot](boot/spring-vs-springboot)
  - [SpringBoot Setup](boot/setup)
- [Spring Boot Starter Template](boot/starter-template)
  - [Sample pom xml with starter template](boot/starter-template/example)
- [SpringBoot Key Components](boot/key-components)
- Basic Configurations
- [Spring Boot Embedded Containers](boot/embedded-containers)
- [Logging](boot/logging)
- [Spring Boot Spring Data JPA](boot/spring-data-jpa)
- [SpringBoot DevTools](boot/devtools)
- [SpringBoot Spring Security](boot/spring-security)
- [Actuator](boot/actuator)
- [SpringBoot Testing](boot/testing)
  - [Auto-Configured Tests](boot/testing/autoconfigured-tests)
- [zzz](boot/zzz)
- [Spring Boot](boot) - main file
- [ThymeLeaf](boot/thymeleaf)

# Spring Cloud
- [Spring Cloud](cloud)

# Spring WebFlux
- [Spring WebFlux](webflux)