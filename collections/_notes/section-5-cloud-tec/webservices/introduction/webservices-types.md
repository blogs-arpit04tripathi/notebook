---
layout: post
title: WebServices Types
permalink: /:collection/webservices/types
---

Web Services are the services available over the web.

|SOAP|REST|
---|---
Simple Object Access Protocol (SOAP)|Representational State Transfer (REST)|
|serves as a standard XML-based protocol for web service creation.| An architectural style for web service creation.
Medium – HTTP (POST), even get, delete etc are done via POST|Medium – HTTP (POST, GET, PUT, DELETE)
Data Format – XML|Data Format – HTML,XML, JSON, Plain Text
SOAP can't use REST because it is a protocol.|REST can use SOAP web services because it is a concept and can use any protocol like HTTP, SOAP.
SOAP uses services interfaces to expose the business logic.|REST uses URI to expose business logic.
JAX-WS is the java API for SOAP WS.|JAX-RS is the java API for RESTful WS.
SOAP defines standards to be strictly followed.|REST does not define too much standards like SOAP and is loosely coupled.
SOAP requires more bandwidth and resource than REST.|REST requires less bandwidth and resource than SOAP.
SOAP defines its own security.|RESTful web services inherits security measures from the underlying transport.
SOAP is less preferred than REST.|REST more preferred than SOAP.
W3C recommendation for communication between two applications.||

# Soap Web Services
**Advantages**
* WS Security: SOAP defines its own security.
* Language and Platform independent
* Firewall : SOAP allows you to get around firewalls.
* It allows circulation of messages in distributed and decentralized environment.

**Disadvantages**
* Slow: XML parsing,slow and consumes more bandwidth and resource.
* WSDL dependent: SOAP uses WSDL and doesn't have any other mechanism to discover the service.

### RESTful Web Services
**Advantages**
* Fast: No strict specification like SOAP.
    - It consumes less bandwidth and resource.
* Language and Platform independent
* Can use SOAP: RESTful web services can use SOAP web services as implementation.
* Permits different data format: RESTful web service permits different data format - Plain Text, HTML, XML and JSON.
