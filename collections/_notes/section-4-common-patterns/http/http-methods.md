---
layout: post
title: Http Methods
permalink: /:collection/http/methods
---

**Safety**
- If it does not change the state of a resource when invoked.
  - GET, HEAD

**Idempotent**
- If it can be called multiple times and the end result is the same.
  - GET, HEAD, PUT, DELETE 
- DELETE is idempotent because there are no side-effects to the resource.
  - subsequent calls can result in an error message dependent on your implementation.

**Http Methods**

|HTTP VERB|Description|Response Code|Note|Idempotent|Safe|Feature|
|---|---|---|---|
|POST   |Create         |201 : CREATED|Create a new entity, optionally return URI also.||||
|PUT    |Update         |200 : OK,<br>202 : ACCEPTED,<br>204 : NO_CONTENT|Update an existing entity entirely|Y|||
|PATCH  |Patch          |200 : OK,<br>202 : ACCEPTED,<br>204 : NO_CONTENT|Partial updates|Y|
|GET    |Retrieve       |200 : OK|Read a list of entities or single entity|Y|Y|linkable, cacheable|
|DELETE |Delete         |200 : OK,<br>202 : ACCEPTED,<br>204 : NO_CONTENT|delete an existing entity|Y|||
|HEAD   |Retrieve       |200 : OK|identical to GET, except that only the HTTP header is returned.|Y|Safe||
|OPTIONS|API description|200 : OK|request information about the communication options available|
|TRACE  |Trace          |200 : OK|invoke a remote, application-layer loop-back of the request message.<br>Used for testing.|
|CONNECT|               |        |reserves the method name CONNECT for use with a proxy that can dynamically switch to being a tunnel (e.g. SSL tunneling)|

- **TRACE**: Provides a way to test what server receives. It simply returns what was sent.
- **CONNECT**: Used by browser when it knows it talks to a proxy and the final URI begins with https://. The intent of CONNECT is to allow end-to-end encrypted TLS session, so the data is unreadable to a proxy.

# POST vs PUT
- "POST /books" with a bunch of book information might create a new book, and respond with the new URL identifying that book: "/books/5".
- "PUT /books/5" would have to either create a new book with the id of 5, or replace the existing book with ID 5.
    - In non-resource style, POST can be used for just about anything that has a side effect.
- PUT is idempotent - multiple PUTs of the same data to the same URL should be fine
- POST is not idempotent - multiple POSTs creates multiple objects.
- PUT is meant as a a method for "uploading" stuff to a particular URI, or overwriting what is already in that URI.