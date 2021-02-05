---
layout: post
title: WebServices FAQ
permalink: /:collection/webservices/faq
---

- TOC
{:toc}

<hr><br>

# Do we require any special application to access web service?
- No need of installing any application for accessing web services.
- Only requirement for accessing web services from any application is that it must support XML-based request and response. 

# What tools are used to test web services?
- SoapUI tool for testing SOAP and RESTful web services
- Poster for firefox browser
- Postman extension for Chrome
- REST client
- JMeter

**SOAPUI**
SOAPUI is an open-source, free and cross-platform functional testing solution. Mentioned below are some actions performed by SOAPUI
- It can help create functional, security and load testing test suites.
- Data driven testing and scenario based testing is also performed.
- It has the ability to impersonate web services as well as has got built-in reporting abilities.

# Explain the loosely coupled architecture of web services.
- A consumer of a web service is not tied to that web service directly.
- The web service interface can change over time without compromising the client's ability to interact with the service.
- A tightly coupled system implies that the client and server logic are closely tied to one another, implying that if one interface changes, the other must be updated.
- Adopting a loosely coupled architecture tends to make software systems more manageable and facilitates simpler integration between different systems.

# What are the advantages of having XML based Web services?
- Using XML eliminates any networking, operating system, or platform binding.
- Web Services based applications are highly interoperable application at their core level.

# What do you mean by synchronicity?
- Synchronicity is used to bind the client to the execution of the service.
- In synchronous invocations, the client blocks and waits for the service to complete its operation before continuing.
- On the other hand, synchronous operations facilitate a client to invoke a service and then execute other functions.
