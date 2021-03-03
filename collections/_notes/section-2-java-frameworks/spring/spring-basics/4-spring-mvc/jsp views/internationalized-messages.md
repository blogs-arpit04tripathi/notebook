---
layout: post
title: Displaying Internationalized Messages
permalink: /:collection/spring/mvc/internationalized-messages
---

```xml
<h1><s:message code="spittr.welcome"/></h1>
```

As used here, \<s:message> will render the text available from a message source where the key is spittr.welcome. Therefore, you’ll need to configure such a message source if you expect \<s:message> to be able to do its job.

Spring has a handful of message-source classes, all implementing the MessageSource interface. One of the more common and useful implementations is ResourceBundleMessageSource. It loads messages from a properties file whose name is derived from a base name. The following @Bean method configures `ResourceBundleMessageSource`:

|JSP tag            |Description|
|---                |---|	
|\<s:bind>          |	Exports a bound property status to a page-scoped status property. Used along with \<s:path> to obtain a bound property value.|
|\<s:escapeBody>    |	HTML and/or JavaScript escapes the content in the body of the tag.|
|\<s:hasBindErrors> |	Conditionally renders content if a specified model object (in a request attribute) has bind errors.|
|\<s:htmlEscape>    |	Sets the default HTML escape value for the current page.|
|\<s:message>       |	Retrieves the message with the given code and either renders it (default) or assigns it to a page-, request-, session-, or application-scoped variable (when using the var and scope attributes).|
|\<s:nestedPath>    |	Sets a nested path to be used by \<s:bind>.|
|\<s:theme>         |	Retrieves a theme message with the given code and either renders it(default) or assigns it to a page-, request-, session-, or application-scoped variable (when using the var and scope attributes).|
|\<s:transform>     |	Transforms properties not contained in a command object using a com mand object’s property editors.|
|\<s:url>           |	Creates context-relative URLs with support for URI template variables and HTML/XML/JavaScript escaping. Can either render the URL (default) or assign it to a page-, request-, session-, or application-scoped variable (when using the var and scope attributes).|
|\<s:eval>          |	Evaluates Spring Expression Language (SpEL) expressions, rendering the result (default) or assigning it to a page-, request-, session-, or application scoped variable (when using the var and scope attributes).|

```java
@Bean
public MessageSource messageSource() {
  ResourceBundleMessageSource ms = new  ResourceBundleMessageSource();
  ms.setBasename("messages");
  return ms;
}
```

The key thing in this bean declaration is the setting of the basename property. You can set it to any value you’d like, but here I’ve chosen to set it to messages. By setting it to messages, you can expect **ResourceBundleMessageResolver** to resolve messages from properties files at the root of the classpath whose names are derived from that base name.

Optionally, you may choose **ReloadableResourceBundleMessageSource**, which works much like ResourceBundleMessageSource, but it has the ability to reload message properties without recompiling or restarting the application. Here’s a sample configuration for ReloadableResourceBundleMessageSource:

```java
@Bean
public MessageSource messageSource() {
    ReloadableResourceBundleMessageSource msgSource = new ReloadableResourceBundleMessageSource();
    messageSource.setBasename("file:///etc/spittr/messages");
    messageSource.setCacheSeconds(10);
    return msgSource;
}
```

The key difference here is that the basename property is configured to look outside of the application (not in the classpath, like ResourceBundleMessageSource). The basename property can be set to look for messages in the classpath (with a classpath: prefix), in the filesystem (with a file: prefix), or at the root of the web application (with no prefix). Here, it’s configured to look for messages in properties files in the /etc/spittr directory of the server’s filesystem and with a base filename of “messages”.
