---
layout: post
title: Jersey JAXB
permalink: /:collection/webservices/jaxb
---

- Jersey Framework is a development toolkit for client-server communication with standard implementations as Java APIs.
- Example - JSR 311 & JSR 339

# Java Architecture for XML Binding (JAXB)
- Java standard that defines how Java objects are converted from and to XML.
- It uses a standard set of mappings.
- JAXB defines an API for reading and writing Java objects to and from XML documents.
- As JAXB is defined via a specification, it is possible to use different implementations for this standard.
- JAXB defines a service provider which allows the selection of the JAXB implementation.

# JAX-WS
- Meant for XML based web services such as SOAP.
- eared towards server to server interactions with well defined contracts (WSDLs) and usually when the service and client side are from separate groups.
- It is very resource intensive so it isn’t feasible for client-to-server interactions where the network or client device capability is less than optimal.

# JAX-RS
- JAX-RS is geared towards client to server interactions, although server-to-server is okay.
- As it has little service obligations, it can be tuned to whatever the client needs are.
- JAX-RS supports the automatic creation of XML and JSON via JAXB.

