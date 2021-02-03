---
layout: post
title: Spring Framework
permalink: /spring
---

# Latest in Spring
- [New in Spring](/spring/latest) - todo
- [Spring Framework Architecture](/spring/architecture)
- [Spring Annotations Quick Reference](https://springframework.guru/spring-framework-annotations){:target="_blank"}

# Spring Core
- [Introduction to Spring](/spring/core/introduction)
- [POJO vs Java Beans vs EJB](/spring/pojo-bean-ejb)
- [Spring IOC Container](/spring/ioc-container)
  - [IOC Container Types](/spring/ioc-container/types)
    - BeanFactory
    - [Application Context](/spring/ioc-container/application-context)
      - [Application Context Types](/spring/ioc-container/application-context-types)
- Spring Beans
  - [Lifecycle of Bean](/spring/bean-lifecycle)
  - [Spring Bean Definition Metadata](/spring/bean-metadata)
  - [@Bean and @Configuration](/spring/annotation/bean)
  - [Bean Scopes](/spring/bean-scopes)
    - [Working with request and session scope](/spring/bean-scopes/request-and-session-scope)
  - [Mixing configurations - Java and Xml](/spring/mixing-configs)
    - @Import
- Dependency Injection - DI
  - [Loose coupling through DI](/spring/loose-coupling-via-di)
  - [Types of Dependency Injection](/spring/types-dependency-injection)
    - [Constructor vs Setter Injection](/spring/constructor-vs-setter-injection)
- [Wiring Beans](/spring/wiring-beans)
  - [Automatic Wiring](/spring/automatic-wiring) - @ComponentScan
    - [Autowiring Modes](/spring/autowiring-modes)
  - [Ambiguity In Autowiring](/spring/ambiguity-in-autowiring)
    - [@Primary](/spring/annotation/primary)
    - [@Qualifier](/spring/annotation/qualifier)
      - [Create custom Qualifier - @Cold](/spring/annotation/custom-qualifier)
  - [Wiring Beans with Java](/spring/wiring-beans-with-java) - 3rd party classes
- [Conditional Beans](/spring/conditional-beans)
  - [Configuring profile beans](/spring/configuring-profile-beans)
    - [Activating profiles](/spring/activating-profiles)
- [Property value - runtime injection](/spring/runtime-value-injection)
  - [Resolving Property Placeholders](/spring/resolving-property-placeholders) - @Value
  - [Wiring with the Spring Expression Language](wiring-with-spel)
- [@Order](/spring/annotation/order)

# Spring AOP
- [Spring AOP Introduction](/spring/aop/introduction)
  - [Key Terminologies](/spring/aop/key-terms)
  - [Declarative programming through aspects](/spring/aop/declarative-programming-with-aspects)
- [Spring AOP features](/spring/aop/aop-features)
  - [Types of Weaving](/spring/aop/types-of-weaving)
- Creating annotated aspects
  - [Writing pointcuts](/spring/aop/writing-jp)
    - [AspectJ pointcut expression language](/spring-aop/pointcut-expression-language)
    - [Types of Advices](/spring/aop/types-of-advices)
  - [Defining an aspect](/spring/aop/defining-aspects)
    - [Parameters in advice](/spring/aop/params-in-advice)
    - [Ordering Aspects](/spring/aop/ordering-aspects)
- [AOP Introduction](/spring-aop/introductions)
- [Eliminating boilerplate code with aspects](/spring/aop/eliminate-bolierplate-with-aspects)
- [Declaring aspects in XML](/spring/aop/aspects-in-xml)

# Spring MVC - Model View Controller
- [Spring MVC Introduction](/spring/mvc/introduction)
  - [MVC Flow](/spring/mvc/flow)
  - [HandlerInterceptorAdapter](/spring/mvc/handler-interceptor-adapter)
  - [DispatcherServlet](/spring/mvc/dispatcher-servlet)
    - [Enabling Spring MVC](/spring/mvc/enabling-mvc)
  - [Application Context vs DispatcherServletContext](/spring/mvc/applicationContext-vs-dispatcherServletContext)
  - [Alternate Spring MVC configuration](/spring/mvc/alternate-config)
- [Writing a controller](/spring-mvc/writing-controller)
  - [Accepting request input](/spring/mvc/request-inputs) - @PathVariable, @RequestParam
  - [Carrying data across redirect requests](/spring/mvc/data-across-redirect-urls)
  - [Java Validation API](/spring-mvc/validations)
    - [Custom Validation Annotation](/spring-mvc/custom-validation-annotation)
  - [@Initbinder](/spring-mvc/initbinder)
- [Rendering web views](/spring/mvc/render-web-views)
  - [View resolver Types](/spring-mvc/view-resolver-types)
- [Multipart Requests](/spring-mvc/multipart)
  - [StandardServletMultipartResolver](/spring-mvc/multipart/StandardServletMultipartResolver)
  - [CommonsMultipartResolver](/spring-mvc/multipart/CommonsMultipartResolver)
  - [Handle multipart request](/spring-mvc/multipart/handle-request) - @RequestPart
- Exception Handling
  - [Handling exceptions](/spring/mvc/handling-mvc-exceptions) - @ExceptionHandler, @ResponseStatus
  - [Advising controllers](/spring/mvc/advising-controllers) - @ControllerAdvice
- [Spring MVC - FAQ](/spring/mvc/faq)
- [Creating JSP views](/spring/mvc/jsp-views)
  - [Spring General Tag Library](/spring/mvc/taglib)
  - [Displaying Internationalized Messages](/spring/mvc/internationalized-messages)
  - [Creating URLs](/spring/mvc/create-url)
  - [Escaping Content](/spring/mvc/escape-content)

# Spring REST
- [Spring REST Introduction](/spring/rest/introduction)
- [Creating REST endpoint](/spring-rest/first-endpoint)
  - [ContentNegotiatingViewResolver](/spring-rest/contentNegotiatingViewResolver)
    - [ContentNegotiationManager Configuration](/spring-rest/contentNegotiationManager/configuration)
  - [HttpMessageConverters](/spring-rest/HttpMessageConverter)
  - [@RestController](/spring-rest/rest-controller) - @RequestBody, @ResponseBody
  - [ResponseEntity](/spring-rest/response-entity)
  - [Difference - @Component, @Service, @Repository, @Controller](/spring/rest/difference-rest-annotations)
  - [POST vs PUT vs PATCH](/spring/rest/post-vs-put-vs-patch)
- [Consuming REST resources - RestTemplate](/spring/rest/consume-rest-resources)
  - [GET](/spring/rest/get-resources)
  - [PUT](/spring/rest/put-resources)
  - [DELETE](/spring/rest/delete-resources)
  - [POST](/spring/rest/post-resources)
  - [Exchange](/spring/rest/exchange-resources) - request headers
- [Handler Mapping](/spring/rest/handler-mapping)
  - [HandlerInterceptor](/spring/rest/handler-interceptor)
- [PropertyPlaceholderConfigurer and ReloadableResourceBundleMessageSource](/spring/rest/propertyPlaceholderConfigurer-and-reloadableResourceBundleMessageSource)
- [Singleton Bean to Multiple Request](/spring/rest/singleton-bean-to-multiple-request)

# Spring Security
- [Spring Security](/spring/security)

# Spring Data
- [Spring Data](/spring/data)
- [Difference - @EntityScan vs @ComponentScan](/spring/data/entityscan-vs-componentscan) - todo
- [Spring Data Rest](/spring/data/rest)

# Spring Boot
- [SpringBoot Introduction](/spring/boot/introduction)
  - [Spring vs SpringBoot](/spring/boot/spring-vs-springboot)
  - [SpringBoot Setup](/spring-boot/setup)
- [Spring Boot Starter Template](/spring-boot/starter-template)
  - [Sample pom xml with starter template](/spring-boot/starter-template/example)
- [SpringBoot Key Components](/spring-boot/key-components)
- Basic Configurations
- [Spring Boot Embedded Containers](/spring-boot/embedded-containers)
- [Logging](/spring-boot/logging)
- [Spring Boot Spring Data JPA](/spring-boot/spring-data-jpa)
- [SpringBoot DevTools](/spring-boot/devtools)
- [SpringBoot Spring Security](/spring-boot/spring-security)
- [Actuator](/spring-boot/actuator)
- [SpringBoot Testing](/spring-boot/testing)
  - [Auto-Configured Tests](/spring-boot/testing/autoconfigured-tests)
- [zzz](/spring-boot/zzz)
- [Spring Boot](/spring/boot) - main file
- [ThymeLeaf](/spring-boot/thymeleaf)

# Spring Cloud
- [Spring Cloud](/spring/cloud)

# Spring WebFlux
- [Spring WebFlux](/spring-webflux)