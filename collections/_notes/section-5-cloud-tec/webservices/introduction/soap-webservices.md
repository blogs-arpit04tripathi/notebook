---
layout: post
title: SOAP Web Services
permalink: /:collection/webservices/soap
---

**SOAP based web services development approaches**
- **Contract-first approach**: The contract is defined first by XML and WSDL and then java classes are derived from the contract. **(Preferred)**
- **Contract-last approach**: Java classes are defined first and then the contract is generated which is usually the WSDL file from the java class.

One of the major hindrance observed by users of SOAP is the ‘Firewall security mechanism’.
- In this case, all the HTTP ports except those which bypass firewall are locked.
- In some cases, a technical issue of mixing specification of message transport with message structure is also observed.


|Elements of a SOAP message||
|---|---|
Envelope	|This element is defined as the mandatory root element. It translates the XML document and determines the start and end of the SOAP message.
Header	|This element contains the optional header attributes of the message that contains specific information of the application. This element can occur multiple times and are intended to add new features and functionalities.
Body	|This element is mandatory and contains the call and response messages. It is also defined as the child element of the envelope containing all the application derived XML data that has been exchanged as a part of SOAP message.
Fault element	|Errors that occur during processing of the messages are handled by the fault element. If the error is present, then this element appears as a child element of the body. However, there can only be one fault block.

# Characterstics of SOAP envelope element
- SOAP envelope is a packaging mechanism.
- Every Soap message has a mandatory root envelope message.
- Only one body element is allowed for each envelope element.
- As the SOAP version changes, envelope changes.
- If the header element is present, it should appear as the first child.
- Prefix ENV and envelope element is used for specification.
- A namespace and an optional encoding style are used for optional SOAP encoding.

# Few syntax rules applicable for SOAP message
- Must be encoded using XML.
- Must use the SOAP envelope namespace.
- Must use the SOAP encoding namespace.
- Must not contain the DTD reference.
- Must not contain XML processing instructions.
