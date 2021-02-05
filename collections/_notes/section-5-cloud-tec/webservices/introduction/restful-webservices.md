---
layout: post
title: RESTful Web Services
permalink: /:collection/webservices/restful
---

- Representational State Transfer
- Stateless client-server architectural style for developing application accessed over the web.
- **RESTful Web services** - When web services use HTTP methods to implement the concept of REST architecture.
- In this architectural style, data and functionality are served as resources and is accessed by URI (Uniform Resource Identifiers).
- **Resource**
  - Fundamental concept having a type and relationship with other resources.
  - In REST architecture, each content is considered as the resource and they are identified by their URIs.
  - Resources are represented with the help of XML, JSON, text etc in RESTful architecture.

RESTful web services enable web services to work best by inducing properties like
* Performance
* Scalability
* Modifiability

HTTP methods supported
- **GET**: Read-only access to the resource.
- **PUT**: Creation of new resource.
- **DELETE**: Removal of a resource.
- **POST**: Update of an existing resource.
- **OPTIONS**: Get supported operations on the resource.
- **HEAD**: Returns HTTP header only, nobody.

**What is the purpose and format of URI in REST architecture?**
Purpose of URI is to locate resources on the server that are hosting web services.
```
<protocol>://<service-name>/<ResourceType>/<ResourceID>
```

**Explain the term statelessness in terms of RESTful web services?**
- **Statelessness** : REST architecture restriction where a REST web service is not allowed to keep a client state on the server.
- In such situation, the client passes its context to the server and in turn, the server stores the context in order to process client’s further requests.
- **Advantages of statelessness**
  - Each and every method requests are treated independently.
  - Application design is simplified as it does not maintain client’s previous interaction.
  - Works with HTTP protocol as it shares the feature of being statelessness.
- **Disadvantage of statelessness**
  - Every time client interaction takes place, web services are to be provided with extra information about each request so that they can interpret the client’s state.

**For designing a secure RESTful web service, what are the best factors that should be followed?**
- Perform validation of all inputs on the server from SQL injection attacks.
- Perform user’s session based authentication whenever a request is made.
- Never use sensitive data like username, session token password, etc through URL. These should be passed via POST method.
- Methods like GET, POST, PUT, DELETE, etc should be executed with proper restrictions.
- HTTP generic error message should be invoked wherever required.

# Core components of HTTP request and HTTP response

|HTTP Requests	|Meaning/work|
|---|---|
|Verb	|Indicate HTTP methods like GET, PUT, POST, etc
URI	|Identifies the resource on server|
|HTTP Version	|Indicates version.|
|Request Header	|Contains metadata like client type, cache settings, message body format, etc for HTTP request message.|
|Request Body	|Represents content of the message.|

|HTTP Response	|Meaning/work|
|---|---|
|Status/Response code|Indicates the status of the server for requested resource.|
|HTTP version	|Represents HTTP version.|
|Response Header	|Consists of metadata like content length, content type, server length, etc for HTTP response message.|
|Response Body	|Represents response message content.|

