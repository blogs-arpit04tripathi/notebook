---
layout: post
title: ContentNegotiationManager Configuration
permalink: /:collection/spring/rest/contentNegotiationManager/configuration
---

- Specify default content type.
  - Specify content type via request parameter.
  - Ignore the request’s Accept header.
- Map request extensions to specific media types.
  - Use the Java Activation Framework (JAF) as a fallback option for looking up media types from extensions.
- Three ways to configure a ContentNegotiationManager:
  - Create bean of type ContentNegotiationManager.
  - Create bean indirectly via ContentNegotiationManagerFactoryBean.
  - Override configureContentNegotiation() method of WebMvcConfigurerAdapter.

For Java configuration
- easiest way to get a ContentNegotiationManager is to extend WebMvcConfigurerAdapter and override configureContentNegotiation().

```java
@Override
public void configureContentNegotiation(ContentNegotiationConfigurer configurer) {
    configurer.defaultContentType(MediaType.APPLICATION_JSON);
}
```

- If logical view name is `spittles`, configured BeanNameViewResolver resolves the View declared in the spittles() method.
- That’s because the bean name matches the logical view name.
- Otherwise, unless there’s another matching View, ContentNegotiatingViewResolver falls back to the default, serving HTML.

```java
@Bean
public ViewResolver cnViewResolver(ContentNegotiationManager cnm) {
    ContentNegotiatingViewResolver cnvr = new ContentNegotiatingViewResolver();
    cnvr.setContentNegotiationManager(cnm);
    return cnvr;
}

@Bean
public ViewResolver beanNameViewResolver() {
    return new BeanNameViewResolver();
}

@Bean
public View spittles() {
    return new MappingJackson2JsonView();
    // method name and logical view name matched and used by BeanNameViewResolver
}

@Override
public void configureContentNegotiation(ContentNegotiationConfigurer configurer) {
    configurer.defaultContentType(MediaType.TEXT_HTML);
}
```
