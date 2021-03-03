---
layout: post
title: MVC Flow
permalink: /:collection/spring/mvc/flow
---

![]({{site.cdn}}/spring/spring-mvc/mvc-flow.png)

- **Dispatcher Servlet (Spring Conrtoller)** implements **front controller design pattern**
  - every web request must go through it so that it can manage the entire request life cycle.
  - configure in a Java web deployment descriptor - web.xml file.
  - DispatcherServlet consults handler mappings to find out which controller to be called. 
- **HandlerMapping**
  - an interface that defines a mapping between requests and handler objects based on request URL.
  - Controller handler mappings based on **@RequestMapping**.
- **Model** - After handler method processing, results need to be carried back.
- **View** - response given to a view, JavaServer Page (JSP) to be shown in user-friendly format. 
- Controller packages **ModelAndView** (logical view name) to render the output.
  - It then sends the request, along with the model and view name back to the DispatcherServlet.
  - logical view - without any file extension.
  - logical views mapped based on applicationContext file
    - so that you can easily change your view layer code without even touching request handler class code.
* **DispatcherServlet** consults a view resolver to map the logical view name to a specific view implementation, which may or may not be a JSP.
* Now, DispatcherServlet’s final stop is at the view implementation, typically a JSP, where it delivers the model data.
* The view will use the model data to render output.
