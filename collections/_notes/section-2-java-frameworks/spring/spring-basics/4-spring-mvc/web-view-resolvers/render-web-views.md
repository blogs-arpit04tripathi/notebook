---
layout: post
title: Rendering web views
permalink: /:collection/spring/mvc/render-web-views
---

- Spring MVC decouples controller logic and view-rendering of a view.
  - controller and view should agree on the contents of the model at max.
- InternalResourceViewResolver
  - apply prefix `/WEB-INF/views/` and suffix `.jsp` to view name.
  - this gives physical location of the JSP that would render the model.

```java
public interface ViewResolver {
    View resolveViewName(String viewName, Locale locale) throws Exception;
}
```
```java
public interface View {
    String getContentType();
    void render(Map<String, ?> model, HttpServletRequest request, HttpServletResponse response) throws Exception;
}
```
