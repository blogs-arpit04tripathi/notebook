---
layout: post
title: View resolver Types
permalink: /:collection/spring/mvc/view-resolver-types
---

|View resolver                  |Description|
|---                            |---|
|**ContentNegotiatingViewResolver** |	*Resolves views by considering the content type desired by the client and delegating to another view resolver that can produce that type.*|
|**InternalResourceViewResolver**   |	*Resolves views as resources internal to the web application (typically JSPs).*|
|BeanNameViewResolver           |	Resolves views as beans in the Spring application context whose ID is the same as the view name.|
|FreeMarkerViewResolver         |	Resolves views as FreeMarker templates.|
|JasperReportsViewResolver      |	Resolves views as JasperReports definitions.|
|ResourceBundleViewResolver     |	Resolves views from a resource bundle (typically a proper ties file).|
|TilesViewResolver              |	Resolves views as Apache Tile definitions, where the tile ID is the same as the view name. Note that there are two different TilesViewResolver implementations, one each for Tiles 2.0 and Tiles 3.0.|
|UrlBasedViewResolver           |	Resolves views directly from the view name, where the view name matches the name of a physical view definition.|
|VelocityLayoutViewResolver     |	Resolves views as Velocity layouts to compose pages from different Velocity templates.|
|VelocityViewResolver           |	Resolves views as Velocity templates.|
|XmlViewResolver                |	Resolves views as bean definitions from a specified XML file. Similar to BeanNameViewResolver.|
|XsltViewResolver               |	Resolves views to be rendered as the result of an XSLT transformation.|
