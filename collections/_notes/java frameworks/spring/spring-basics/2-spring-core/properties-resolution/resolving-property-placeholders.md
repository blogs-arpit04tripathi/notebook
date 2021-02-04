---
layout: post
title: Resolving Property Placeholders
permalink: /:collection/spring/resolving-property-placeholders
---

-	@Value annotation in much the same way as you might use the @Autowired annotation. 

```java
public BlankDisc(@Value("${disc.title}") String title,  @Value("${disc.artist}") String artist){
	this.title = title;
  this.artist = artist;
}
```
```xml
<context:property-placeholder />
<bean id="sgtPeppers" class="soundsystem.BlankDisc" c:_title="${disc.title}" c:_artist="${disc.artist}" />
```
-	You must configure either a **PropertyPlaceholderConfigurer** or **PropertySourcesPlaceholderConfigurer** bean in order to use placeholder values. 
-	PropertySourcesPlaceholderConfigurer is preferred because it resolves placeholders against the Spring Environment and its set of property sources.
-	Resolving external properties is one way to defer value resolution until runtime, but its focus is finely tuned on resolving properties, by name, from Spring’s Environment and property sources.

# Issue with  Spring 4.2 (propertySourcesPlaceHolderConfigurer) 
I am running the code for Java Configuration and injecting values from props file. However, I'm getting:
```java
${foo.email}
${foo.team}
```
**Instead of the actual property values. How can I resolve this?**
This is an issue with Spring versions. If you are using Spring 4.2 and lower, you will need to add
```java
// add support to resolve ${...} properties
@Bean
public static PropertySourcesPlaceholderConfigurer propertySourcesPlaceHolderConfigurer() {
  return new PropertySourcesPlaceholderConfigurer();
}
```