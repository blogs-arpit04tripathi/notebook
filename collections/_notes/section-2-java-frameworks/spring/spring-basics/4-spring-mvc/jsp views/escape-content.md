---
layout: post
title: Escaping Content
permalink: /:collection/spring/mvc/escape-content
---


The \<s:escapeBody> tag is a general-purpose escaping tag. It renders any content nested in its body, escaping as necessary. For example, suppose you want to display a snippet of HTML code on a page. In order for it to be displayed properly, the < and > characters need to be replaced with < and > or the browser will interpret the HTML as any other HTML in the page.

```xml
<s:escapeBody htmlEscape="true">
  <h1>Hello</h1>
</s:escapeBody>
```

This renders the following to the body of the response:
&lt;h1&gt; Hello&lt;/h1&gt;
The \<s:escapeBody> tag also supports JavaScript escaping with the javaScriptEscape attribute:

```xml
<s:escapeBody javaScriptEscape="true">
  <h1>Hello</h1>
</s:escapeBody>
```

\<s:escapeBody> does one job and does it well. Unlike <s:url>, it only renders content and doesn’t let you assign that content to a variable.
