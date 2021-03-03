---
layout: post
title: HandlerInterceptorAdapter
permalink: /:collection/spring/mvc/handler-interceptor-adapter
---

- **HandlerMapping**, maps controller method to an URL.
- DispatcherServlet uses HandlerAdapter to invoke the method.
- **HandlerInterceptor**
  - perform actions before handling, after handling or after completion (when the view is rendered) of a request.
  - can be used for cross-cutting concerns and to avoid repetitive handler code.
    - like: logging, changing globally used parameters in Spring model etc.

**References**
- Read more about [HandlerInterceptor](https://www.baeldung.com/spring-mvc-handlerinterceptor){:target="_blank"}
- Read more about [HandlerInterceptorAdapter](https://www.journaldev.com/2676/spring-mvc-interceptor-example-handlerinterceptor-handlerinterceptoradapter){:target="_blank"}
