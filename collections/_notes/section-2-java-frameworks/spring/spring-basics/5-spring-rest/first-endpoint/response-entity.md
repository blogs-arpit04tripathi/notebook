---
layout: post
title: ResponseEntity
permalink: /:collection/spring/rest/response-entity
---

Communicating errors to the client, Spring offers:
-	@ResponseStatus - Status codes.
-	@ExceptionHandler - deal with error cases, leaving controller methods to focus on the happy path. 
- ResponseEntity - carries more metadata concerning the response.
  - Setting headers in response.
  - No need to annotate the method with @ResponseBody if it returns ResponseEntity.
  - **HttpHeaders** - A special implementation of MultiValueMap<String, String>

```java
@ExceptionHandler(SpittleNotFoundException.class)
public ResponseEntity<Error> spittleNotFound(SpittleNotFoundException e) {
  long spittleId = e.getSpittleId();
  Error error = new Error(4, "Spittle [" + spittleId + "] not found");
  return new ResponseEntity<Error>(error, HttpStatus.NOT_FOUND);
}

@RequestMapping(value="/{id}", method=RequestMethod.GET)
public ResponseEntity<Spittle> spittleById(@PathVariable long id) {
  Spittle spittle = spittleRepository.findOne(id);
  if (spittle == null)
    throw new SpittleNotFoundException(id);
  return new ResponseEntity<Spittle>(spittle, HttpStatus.OK);
}
```

POST operation return 201 CREATED, with resource location.
```java
@RequestMapping(method=RequestMethod.POST, consumes="application/json")
public ResponseEntity<Spittle> saveSpittle(@RequestBody Spittle spittle) {
  Spittle spittle = spittleRepository.save(spittle);
  HttpHeaders headers = new HttpHeaders();
  URI locationUri = URI.create("http://localhost:8080/spittr/spittles/" + spittle.getId());
  headers.setLocation(locationUri);
  ResponseEntity<Spittle> responseEntity = new ResponseEntity<Spittle>(spittle, headers, HttpStatus.CREATED);
  return responseEntity;
}
```
- Rather than construct the URI manually, Spring offers UriComponentsBuilder.
  - UriComponentsBuilder is preconfigured with known information such as the host, port, and servlet content.
  - It obtains this foundational information from the request that the handler method is serving.
  - From there, the code builds up the rest of the UriComponents by setting the path.

```java
@RequestMapping(method=RequestMethod.POST, consumes="application/json")
public ResponseEntity<Spittle> saveSpittle(@RequestBody Spittle spittle, UriComponentsBuilder ucb) {
  Spittle spittle = spittleRepository.save(spittle);
  HttpHeaders headers = new HttpHeaders();
  URI uri = ucb.path("/spittles/").path(String.valueOf(spittle.getId())).build().toUri();
  headers.setLocation(uri);
  ResponseEntity<Spittle> responseEntity = new ResponseEntity<Spittle>(spittle, headers, HttpStatus.CREATED);
  return responseEntity;
}
```
