---
layout: post
title: Creating URLs
permalink: /:collection/spring/mvc/create-url
---


The \<s:url> tag is a modest little tag. Its main job is to create a URL and either assign it to a variable or render it in the response. It’s a drop-in replacement for JSTL’s \<c:url> tag, but with a few new tricks up its sleeve. In its simplest form, \<s:url> takes a servlet-context-relative URL and renders it with the servlet context path prepended.
```xml
<a href="<s:url href='/spitter/register'/>">Register</a>
```
If the application’s servlet context is named spittr, then the following HTML will be rendered in the response:
```xml
<a href="/spittr/spitter/register">Register</a>
```
This enables you to create URLs without worrying about what the servlet context path will be. The \<s:url> tag takes care of it for you. Optionally, you can have \<s:url> construct the URL and assign it to a variable to be used later in the template:
```xml
<s:url href="/spitter/register" var="registerUrl" />
<a href="${registerUrl}">Register</a>
```
By default, URL variables are created in page scope. But you can have <s:url> create them in application, session, or request scope instead by setting the scope attribute:
```xml
<s:url href="/spitter/register" var="registerUrl" scope="request" />
```
```xml
<!-- With Request params -->
<s:url href="/spittles" var="spittlesUrl">
  <s:param name="max" value="60" />
  <s:param name="count" value="20" />
</s:url>
<!-- With path variables -->
<s:url href="/spitter/{username}" var="spitterUrl">
  <s:param name="username" value="jbauer" />
</s:url>
```

When the href value is a placeholder that matches a parameter specified by \<s:param>, the parameter is inserted into the placeholder’s spot. If the \<s:param> parameter doesn’t match any placeholders in href, then the parameter is used as a query parameter.

The \<s:url> tag can also address any escaping needs for the URL. For example, if you intend to render the URL to be displayed as part of the content on a web page (as opposed to being used as a hypertext link), you may want to ask \<s:url> to do HTML escaping on the URL by setting the htmlEscape attribute to true. For example, the following \<s:url> tag renders an HTML-escaped URL:
```xml
<s:url value="/spittles" htmlEscape="true">
<s:param name="max" value="60" />
<s:param name="count" value="20" />
</s:url>
```
This results in the URL being rendered like this: `/spitter/spittles?max=60&count=20`

On the other hand, if you intend to use the URL in JavaScript code, you may want to set the javaScriptEscape attribute to true:
```xml
<s:url value="/spittles" var="spittlesJSUrl" javaScriptEscape="true">
<s:param name="max" value="60" />
<s:param name="count" value="20" />
</s:url>

<script>
var spittlesUrl = "${spittlesJSUrl}"
</script>
```
This renders the following to the response:
```xml
<script>
var spittlesUrl = "\/spitter\/spittles?max=60&count=20"
</script>
```
