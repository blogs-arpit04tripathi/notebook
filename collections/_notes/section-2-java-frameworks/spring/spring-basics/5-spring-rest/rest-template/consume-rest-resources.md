---
layout: post
title: Consuming REST resources - RestTemplate
permalink: /:collection/spring/rest/consume-rest-resources
---

- RestTemplate frees you from the tedium of consuming RESTful resources.
- TRACE not covered by RestTemplate.
- total 36 methods
  - 11 unique operations
    - 10 are overloaded into 3 method variants
    - 11th overloaded 6 times
- execute() and exchange() - lower-level and general-purpose methods for using any of the HTTP methods.
- Overloaded into three method forms:
  - java.net.URI with no support for parameterized URLs.
  - String URL with URL parameters as a Map.
  - String URL with URL parameters as variable argument list.

|Method|	Description|
|---|---|	
|exchange()|	Executes a specified HTTP method against a URL, returning a ResponseEntity containing an object mapped from the response body|
|execute()|	Executes a specified HTTP method against a URL, returning an object mapped from the response body.|
|getForEntity()|	Sends an HTTP GET request, returning a ResponseEntity containing an object mapped from the response body.|
|getForObject()|	Sends an HTTP GET request, returning an object mapped from a response body.|
|postForEntity()|	POSTs data to a URL, returning a ResponseEntity containing an object mapped from the response body.|
|postForLocation()|	POSTs data to a URL, returning the URL of the newly created resource.|
|postForObject()|	POSTs data to a URL, returning an object mapped from the response body.|
|headForHeaders()|	Sends an HTTP HEAD request, returning the HTTP headers for the specified resource URL.|
|optionsForAllow()|	Sends an HTTP OPTIONS request, returning the Allow header for the specified URL.|
|delete()|	Performs an HTTP DELETE request on a resource at a specified URL|
|put()|	PUTs resource data to the specified URL.|
