---
layout: post
title: GET
permalink: /:collection/spring/rest/get-resources
---

- can throw unchecked exception - `RestClientException`.

```java
public Profile fetchFacebookProfile(String id) {
  RestTemplate rest = new RestTemplate();
  // getForObject
  Profile profile = rest.getForObject("http://graph.facebook.com/{spitter}", Profile.class, id);
  // getForEntity - with response Http Header and status code
  ResponseEntity<Profile> response = rest.getForEntity("http://graph.facebook.com/{spitter}", Profile.class, id);
  return profile;
}
```

# getForObject
```java
<T> T getForObject(URI url, Class<T> responseType) throws RestClientException;
<T> T getForObject(String url, Class<T> responseType, Object... uriVariables) throws RestClientException;
<T> T getForObject(String url, Class<T> responseType, Map<String, ?> uriVariables) throws RestClientException;
```

# getForEntity
```java
<T> ResponseEntity<T> getForEntity(URI url, Class<T> responseType) throws RestClientException;
<T> ResponseEntity<T> getForEntity(String url, Class<T> responseType,  Object... uriVariables) throws RestClientException;
<T> ResponseEntity<T> getForEntity(String url, Class<T> responseType,  Map<String, ?> uriVariables) throws RestClientException;
```

# Extracting response metadata

```java
responseEntity.getStatusCode() == HttpStatus.NOT_MODIFIED) { 304 }
```

- HttpHeaders 
  - `get("header_key")` - list of string values
  - `getFirst("header_key")` - returns first one.

```java
public List<MediaType> getAccept() { ... }
public List<Charset> getAcceptCharset() { ... }
public Set<HttpMethod> getAllow() { ... }
public String getCacheControl() { ... }
public List<String> getConnection() { ... }
public long getContentLength() { ... }
public MediaType getContentType() { ... }
public long getDate() { ... }
public String getETag() { ... }
public long getExpires() { ... }
public long getIfNotModifiedSince() { ... }
public List<String> getIfNoneMatch() { ... }
public long getLastModified() { ... }
public URI getLocation() { ... }
public String getOrigin() { ... }
public String getPragma() { ... }
public String getUpgrade() { ... }
```
