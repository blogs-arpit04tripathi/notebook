---
layout: post
title: Web Service Protocols Layers
permalink: /:collection/webservices/protocol-layers
---

1. **Service transport**
- First layer which helps in transporting XML messages between various client applications.
- This layer commonly uses the below-mentioned protocols:
	- HTTP(Hypertext Transport Protocol)
	- SMTP(Simple Mail Transport Protocol)
	- FTP(File Transfer Protocol)
	- BEEP(Block Extensible Exchange Protocol)

2. **XML messaging**
- This layer is based on the XML model where messages are encoded in common XML format which is easily understood by others.
- This layer includes
	- XML-RPC
	- SOAP(Simple Object Access Protocol)

3. **Service description**
- This layer contains description like location, available functions, and data types for XML messaging which describes the public interface to a specific web service.
- This layer includes:
    - WSDL(Web Service Description Language)

4. **Service discovery**
- This layer is responsible for providing a way to publish and find web services over the web.
- It is used for centralizing services into a common registry and providing easy publish/find functionality.
- This layer includes:
    - UDDI(Universal Description, Discovery, and Integration)

# Explain BEEP
- Blocks Extensible Exchange Protocol.
- BEEP is determined as Building new protocols for the variety of applications such as instant messaging, network management, file transfer etc.
- It is termed as new Internet Engineering Task Force (IETF) which is layered directly over TCP. 

It has some built-in features like
- Authentication
- Security
- Error handling
- Handshake Protocol
