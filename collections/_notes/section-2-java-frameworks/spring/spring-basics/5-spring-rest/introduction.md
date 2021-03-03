---
layout: post
title: Spring REST Introduction
permalink: /:collection/spring/rest/introduction
---


- SOAP (Simple Object Access Protocol)
  - typically focus on actions and processing
  - Envelop - Header + Body
  - xml based
- **Representational State Transfer (REST)**
  - concern is with the data being handled.
  - **Representational**
    - REST resources can be represented in virtually any form
    - XML, JSON (JavaScript Object Notation), or HTML
  - **State** - concerned with the state of a resource.
  - **Transfer** - transferring resource data from one application to another.
- HttpMethods
  - Create - POST - non-idempotent
  - Read - GET
  - Update - PUT or PATCH
  - Delete - DELETE
- representation best suited for the client can be chosen using **ContentNegotiatingViewResolver**.
- **@RequestBody** along with HttpMethodConverter implementations
  - can convert inbound HTTP data into Java objects passed into controller handler methods.
- **@ResponseBody** along with HttpMethodConverter implementations.
  - bypass view-based rendering
  - resturn response as json.
- Spring applications can consume REST resources using RestTemplate.

![spring-rest-diagram-2]({{site.cdn}}/spring/spring-rest/spring-rest-diagram-2.png){:target="_blank"}

