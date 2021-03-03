---
layout: post
title: HttpMessageConverter
permalink: /:collection/spring/rest/HttpMessageConverter
---

- Message conversion
  - more direct way to transform data produced by a controller into a representation served to a client.
  - data produced by controller, and message converter transforms that data.
- application/json
  - Jackson JSON library on classpath,
  - **MappingJacksonHttpMessageConverter** 
- text/xml
  - **Jaxb2RootElementHttpMessageConverter**
- HttpMessageConverter - 5 are registered by default without additional configuration.

|Message converter|	Description|
|---|---|	
|AtomFeedHttpMessageConverter|	Converts Rome Feed objects to and from Atomfeeds (media type application / atom+xml).|
|BufferedImageHttpMessageConverter|	Registered if the Rome library is present on the classpath. Converts BufferedImage to and from image binary data.|
|ByteArrayHttpMessageConverter|	Reads and writes byte arrays. Reads from all media types (*/*), and writes as application/octet-stream.|
|FormHttpMessageConverter|	Reads content as application/x-www-form-urlencoded into a MultiValueMap\<String,String>. Also writes MultiValueMap\<String,String> as application/x-www-form-urlencoded and MultiValueMap\<String, Object> as multipart/form-data.|
|Jaxb2RootElementHttpMessageConverter|	Reads and writes XML (either text/xml or application/xml) to and from JAXB2-annotated objects. Registered if JAXB v2 libraries are present on the classpath.|
|MappingJacksonHttpMessageConverter|	Reads and writes JSON to and from typed objects or untyped HashMaps. Registered if the Jackson JSON library is present on the classpath.|
|MappingJackson2HttpMessageConverter|	Reads and writes JSON to and from typed objects or untyped HashMaps. Registered if the Jackson 2 JSON library is present on the classpath.|
|MarshallingHttpMessageConverter|	Reads and writes XML using an injected marshaler and unmarshaler. Supported (un)marshalers include Castor, JAXB2, JIBX, XMLBeans, and XStream.|
|ResourceHttpMessageConverter|	Reads and writes org.springframework.core.io.Resource.|
|RssChannelHttpMessageConverter|	Reads and writes RSS feeds to and from Rome Channel objects. Registered if the Rome library is present on the classpath.|
|SourceHttpMessageConverter|	Reads and writes XML to and from javax.xml.transform.Source objects.|
|StringHttpMessageConverter|	Reads all media types (*/*) into a String. Writes String to text/plain.|
|XmlAwareFormHttpMessageConverter|	An extension of FormHttpMessageConverter that adds support for XML-based parts using a SourceHttpMessageConverter.|
