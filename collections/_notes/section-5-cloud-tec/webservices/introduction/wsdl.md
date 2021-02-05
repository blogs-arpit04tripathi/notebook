---
layout: post
title: WSDL (Web service Description Language)
permalink: /:collection/webservices/wsdl
---

- Simple XML document under Service Description layer of Web Service Protocol Stack.
- Describes the technical details or locates the user interface to web service.
- Few of the important information present in WSDL document are
  * Method name
  * Port types
  * Service end point
  * Method parameters
  * Header information
  * Origin, etc

# WSDL operation response types
- **One-way**: Receives a message but does not return response.
- **Request-Response**: Receives a request and return a response. (most common)
- **Solicit-Response**: Sends a request and wait for a response.
- **Notification**: Sends a message but does not wait for a response.

# Different elements of WSDL documents?
* **Types**: message data types in form of XML schema, used by the web services.
* **Message**: data elements for each operation where messages could be the entire document or an argument that is to be mapped.
* **Port Type**: There are multiple services present in WSDL. Port type defines the collection of operations that can be performed for binding.
* **Binding**: Determines and defines the protocol and data format for each port type.
* **Operations**: defines the operations performed for a message to process the message.

# `<message>` element
- Describes the data that has been exchanged between the consumer and the web service providers.
- Every web service consists of two messages and each message has zero or more `<part>` parameters.
  - Input: Describes the parameter for the web service.
  - Output: Describes the return data from the web service.

# `<definition>` element
root of WSDL document which defines the name of the web service as well as act as a container for all the other elements.

# `<Port>` element
Every port element is related to a specific binding by defining an individual endpoint. Attributes are :
- **Name**:provides the unique name within the WSDL document.
- **Binding**: refers to the process of binding which has to be performed as per the linking rules defined by WSDL.

**What are the points that should be considered by ports while binding?**  
- WSDL allows extensibility elements which are used to specify binding information.
- A port must not
  - Specify more than one address.
  - Specify any binding information other than address information.

**Is binding between SOAP and WSDL possible?**  
- Yes, it is possible to bind WSDL to SOAP by basically two attributes
  - **Name**: Defines the name of the binding.
  - **Type**: Defines the port for the binding.
- For SOAP binding, two attributes need to be declared
  - **Transport**: Defines the SOAP protocol to be used i.e. HTTP.
  - **Style**: This attribute can be ‘rpc’ or ‘document’.

[WSDL Tutorial: Web Services Description Language with Example](https://www.guru99.com/wsdl-web-services-description-language.html)