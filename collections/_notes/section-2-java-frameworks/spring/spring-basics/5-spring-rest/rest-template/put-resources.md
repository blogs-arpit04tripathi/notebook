---
layout: post
title: PUT
permalink: /:collection/spring/rest/put-resources
---

```java
void put(URI url, Object request) throws RestClientException;
void put(String url, Object request, Object... uriVariables) throws RestClientException;
void put(String url, Object request, Map<String, ?> uriVariables) throws RestClientException;
```
```java
public void updateSpittle(Spittle spittle) throws SpitterException {
  RestTemplate rest = new RestTemplate();

  String url = "http://localhost:8080/spittr-api/spittles/" + spittle.getId();
  rest.put(URI.create(url), spittle);

  rest.put("http://localhost:8080/spittr-api/spittles/{id}", spittle, spittle.getId());

  Map<String, String> params = new HashMap<String, String>();
  params.put("id", spittle.getId());
  rest.put("http://localhost:8080/spittr-api/spittles/{id}", spittle, params);
}
```
