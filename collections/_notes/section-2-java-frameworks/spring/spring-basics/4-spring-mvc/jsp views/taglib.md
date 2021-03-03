---
layout: post
title: Spring General Tag Library
permalink: /:collection/spring/mvc/taglib
---


To use Spring’s general tag library, you must declare it in the pages that will use it:
```xml
<%@ taglib uri="http://www.springframework.org/tags" prefix="s" %>
```
As with any JSP tag library, the prefix can be anything you want. Commonly, spring is given as the prefix for this tag library. But I prefer to use s because it’s much more succinct and easier to type and read. With the tag library declared, you can now use the 10 JSP tags listed in table. Several of the tags in table 6.3 have been made obsolete by Spring’s form-binding tag library. The \<s:bind> tag, for instance, was Spring’s original form-binding tag, and it was much more complex than the tags covered in the previous section.
