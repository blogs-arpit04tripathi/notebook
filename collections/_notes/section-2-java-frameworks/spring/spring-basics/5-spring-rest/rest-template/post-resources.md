---
layout: post
title: POST
permalink: /:collection/spring/rest/post-resources
---

```java
public String postSpitterForObject(Spitter spitter) {
  RestTemplate rest = new RestTemplate();

  Spitter spitter = rest.postForObject("http://localhost:8080/spittr-api/spitters", spitter, Spitter.class);

  ResponseEntity<Spitter> response = rest.postForEntity("http://localhost:8080/spittr-api/spitters", spitter, Spitter.class);
  Spitter spitter = response.getBody();
  URI url = response.getHeaders().getLocation();
  
  return rest.postForLocation("http://localhost:8080/spittr-api/spitters",spitter).toString();
}
```

# postForObject
```java
<T> T postForObject(URI url, Object request, Class<T> responseType) throws RestClientException;
<T> T postForObject(String url, Object request, Class<T> responseType, Object... uriVariables) throws RestClientException;
<T> T postForObject(String url, Object request, Class<T> responseType, Map<String, ?> uriVariables) throws RestClientException;
```

# postForEntity
```java
<T> ResponseEntity<T> postForEntity(URI url, Object request, Class<T> responseType) throws RestClientException;
<T> ResponseEntity<T> postForEntity(String url, Object request, Class<T> responseType, Object... uriVariables) throws RestClientException;
<T> ResponseEntity<T> postForEntity(String url, Object request, Class<T> responseType, Map<String, ?> uriVariables) throws RestClientException;
```

# postForLocation
```java
URI postForLocation(String url, Object request, Object... uriVariables) throws RestClientException;
URI postForLocation(String url, Object request, Map<String, ?> uriVariables) throws RestClientException;
URI postForLocation(URI url, Object request) throws RestClientException;
```
