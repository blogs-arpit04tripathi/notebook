---
layout: post
title: Singleton Bean to Multiple Request
permalink: /:collection/spring/rest/singleton-bean-to-multiple-request
---

**How spring serves singleton bean to multiple request at the same time**
- *For Spring, what if I have two requests that access the singleton bean at the same time? Does one request have to wait until the other to finish?*
- web requests will be served using single instance of the controller/service classes.
- There is no problem (i.e., there will not be any waits in between) even if two requests access the singleton bean as they will be served in two separate threads.
- All you need to ensure is that your **controller and service classes (i.e., singleton scoped beans) do not carry/hold any state (i.e., they are stateless) and are thread-safe.**

**How does Spring container find the singleton bean instance for my requests?**  
- Spring container creates and then injects the singleton bean instances based upon the configurations
  - provided **using the xml or through annotations.**

**For servlets, if I have two requests that access a normal class's normal method (no static no other complex things) at the same time? Does one request have to wait until the other to finish to avoid concurrency (at the same time two request are trying to access the object of the same class) ?**
- No, **each request will be handled in a separate thread**
  - so one request will not wait for the other request to be served/completed i.e. the requests will be served/processed parallelly.
  - This is achieved by the Web containers by using/managing the Thread pools.

**How does web container find the instance for my requests?**  
- **Web container (like Tomcat, etc..) creates and loads all of the servlet classes** and then once the web request comes from the client (like Browser), it will be handled to the servlet according to the url-pattern configured in the web.xml or through annotations.
