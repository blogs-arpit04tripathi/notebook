---
layout: post
title: ContentNegotiatingViewResolver
permalink: /:collection/spring/rest/contentNegotiatingViewResolver
---

- Controller handler method response is generally a logical view name.
  - If method doesn’t return a logical view name, logical view name is derived from the request’s URL.
  - DispatcherServlet passes view name to view resolver to render the results of the request.
- **ContentNegotiatingViewResolver**
  - view resolver that takes the content type that the client wants into consideration.
- Content-negotiation two-step:
  - Determine the requested media type(s).
  - Find the best view for the requested media type(s).

```java
@Bean
public ViewResolver cnViewResolver(){
    return new ContentNegotiatingViewResolver();
}
```

# ContentNegotiatingViewResolver Limitation
- can only determine how a resource (controller response) is rendered to a client.
- has no say in what representations a controller can consume.
- The View chosen renders the model—not the resource—to the client.
  - client requests list of Spittle objects in JSON, But model is a map of key-value pairs.
- ***Instead, Use Spring message converters for producing resource representations.***

# Identify Requested Media Type

- **ContentNegotiatingViewResolver**
  - first looks at the URL’s file extension.
  - then, considers Accept header is considered as MIME type(s).
  - Accept header can’t always be deemed reliable.
  - Eventually, falls back to `/` as default content type, client has to take whatever representation the server sends it.
- ContentNegotiatingViewResolver delegates to other view resolvers.
  - Every view resolved is added to a list of candidate views.
  - It cycles through all requested media types, trying to find from candidate views that produces a matching content type.
  - The first match found is the one that’s used to render the model.

```
.json -> application/json
.xml -> application/xml
.html -> text/html
```