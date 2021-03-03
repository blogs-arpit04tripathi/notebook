---
layout: post
title: PropertyPlaceholderConfigurer and ReloadableResourceBundleMessageSource
permalink: /:collection/spring/rest/propertyPlaceholderConfigurer-and-reloadableResourceBundleMessageSource
---

# PropertyPlaceholderConfigurer 
- Used when we load some property files which is used in applicationcontext.xml of spring.
- We can use the properties directly using JSTL expressions.
- for properties files to be used in the application context or inside the code with with `@value`.
- need to restart your application when making changes
- **ResourceBundleMessageSource** uses a JDK class to do its thing.
  - It delegates to it to load the bundle.
  - ResourceBundle does not know how to handle the classpath: prefix and so it fails.

# ReloadableResourceBundleMessageSource 
- Used when property files are used outside the applicationcontext.xml.
- properties loaded are not accessible in applicationcontext.xml.
- for Internationalization & Localization (i18n) of messages.
- capable of refreshing the messages while the application is running.
- more powerful as you are not limited to bundles on the classpath but you can load files from other locations too.
- **ReloadableResourceBundleMessageSource** knows how to load bundles from other places, not just the classpath.
  - works with a Spring class `Resource`
  - knows how to handle the classpath: prefix.
    
- ReloadableResourceBundleMessageSource is more advance than ResourceBundleMessageSource.
   - It is not restricted to read .properties files alone but can read xml property files as well.
   - It is not restricted to reading files from just classpath but from any location.
