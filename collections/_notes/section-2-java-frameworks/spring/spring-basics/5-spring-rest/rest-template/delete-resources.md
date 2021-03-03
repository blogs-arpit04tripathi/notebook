---
layout: post
title: DELETE
permalink: /:collection/spring/rest/delete-resources
---

```java
void delete(String url, Object... uriVariables) throws RestClientException;
void delete(String url, Map<String, ?> uriVariables) throws RestClientException;
void delete(URI url) throws RestClientException;
```

```java
public void deleteSpittle(long id) {
  RestTemplate rest = new RestTemplate();
  rest.delete(URI.create("http://localhost:8080/spittr-api/spittles/" + id));
  rest.delete("http://localhost:8080/spittr-api/spittles/{id}", id));
}
```
