---
layout: post
title: How Web Service Works
permalink: /:collection/webservices/how-webservices-work
---

A web service enables communication among various applications by using open standards such as HTML, XML, WSDL, and SOAP.

A web service takes the help of
* XML to tag the data.
* SOAP to transfer a message.
* WSDL to describe the availability of service.

|Abbrevations|  |
---|---
SOA     |Service Oriented Architecture
SOAP	|Simple Object Access Protocol
WSDL	|Web Services Description Language
WS	    |Web Service
XML	    |Extensible Markup Language
UDDI	|Universal Description, Discovery and Integration

![how-webservices-work]({{site.cdn}}/webservices/webservices/how-webservices-work.png)

- Service Description is published in a directory by all the service providers.
  - Service description is written in a special language called WSDL (Industry accepted).
- Services talk to the directory using SOAP (Industry Standard).
- Consumer service reads the description from the WSDL directory and creates a corresponding request in XML.
