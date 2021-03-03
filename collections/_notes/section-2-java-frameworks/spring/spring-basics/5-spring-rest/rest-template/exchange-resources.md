---
layout: post
title: Exchange
permalink: /:collection/spring/rest/exchange-resources
---

- ***set headers on the request sent.***

```java
<T> ResponseEntity<T> exchange(URI url, HttpMethod method, HttpEntity<?> requestEntity, Class<T> responseType) throws RestClientException;
<T> ResponseEntity<T> exchange(String url, HttpMethod method, HttpEntity<?> requestEntity, Class<T> responseType, Object... uriVariables) throws RestClientException;
<T> ResponseEntity<T> exchange(String url, HttpMethod method, HttpEntity<?> requestEntity, Class<T> responseType, Map<String, ?> uriVariables) throws RestClientException;
```

```java
ResponseEntity<Spitter> response = rest.getForEntity("http://localhost:8080/spittr-api/spitters/{spitter}", Spitter.class, spitterId);
Spitter spitter = response.getBody();

ResponseEntity<Spitter> response = rest.exchange("http://localhost:8080/spittr-api/spitters/{spitter}", HttpMethod.GET, null, Spitter.class, spitterId);
Spitter spitter = response.getBody();

MultiValueMap<String, String> headers = new LinkedMultiValueMap<String, String>();
headers.add("Accept", "application/json");
HttpEntity<Object> requestEntity = new HttpEntity<Object>(headers);
ResponseEntity<Spitter> response = rest.exchange( "http://localhost:8080/spittr-api/spitters/{spitter}", HttpMethod.GET, requestEntity, Spitter.class, spitterId);
Spitter spitter = response.getBody();
```

```
GET /Spitter/spitters/habuma HTTP/1.1
Content-Length: 0
User-Agent: Java/1.6.0_20
Host: localhost:8080
Connection: keep-alive
<!-- Default -->
Accept: application/xml, text/xml, application/*+xml, application/json
<!-- When set explicitly -->
Accept: application/json
```
