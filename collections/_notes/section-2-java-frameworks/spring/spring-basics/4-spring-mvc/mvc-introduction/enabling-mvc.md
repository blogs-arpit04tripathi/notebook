---
layout: post
title: Enabling Spring MVC
permalink: /:collection/spring/mvc/enabling-mvc
---

RootConfig is annotated with @ComponentScan.
```java
@Configuration
@ComponentScan(
    basePackages={"spitter"},
    excludeFilters={ @Filter(type=FilterType.ANNOTATION, value=EnableWebMvc.class) }
    )
public class RootConfig {}
```

```java
@Configuration
@EnableWebMvc
@ComponentScan("com.my.package")
public class WebConfig extends WebMvcConfigurerAdapter {
    
    @Bean
    public ViewResolver viewResolver() {
        InternalResourceViewResolver resolver = new InternalResourceViewResolver();
        resolver.setPrefix("/WEB-INF/views/");
        resolver.setSuffix(".jsp");
        resolver.setExposeContextBeansAsAttributes(true);
        return resolver;
    }
    
    @Override
    public void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer) {
        configurer.enable();
    }
}
```

- `<mvc:annotation-driven>` to enable annotation-driven Spring MVC.
- **WebConfig** annotated with @ComponentScan so that the com.my.package will be scanned for components.
  - @Controller - candidates for component-scanning. 
- **ViewResolver** bean
  - *InternalResourceViewResolver*, configured to look for JSP files by adding prefix and suffix to view names.
  - view name `home` will be resolved as `/WEB-INF/views/home.jsp`.
- WebConfig class extends **WebMvcConfigurerAdapter**
  - override `configureDefaultServletHandling()` method.
  - By calling enable() on the given DefaultServletHandlerConfigurer, you’re asking DispatcherServlet to forward requests for static resources to the servlet container’s default servlet and not to try to handle them itself.

