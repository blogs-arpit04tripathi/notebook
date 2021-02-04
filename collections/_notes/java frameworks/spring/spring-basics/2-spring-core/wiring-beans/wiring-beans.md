---
layout: post
title: Wiring Beans
permalink: /:collection/spring/wiring-beans
---

- Objects aren’t responsible for finding or creating the other objects that they need to do their jobs. 
- Container gives them references to the objects that they collaborate with. 
- Act of creating these associations between application objects in DI is called as wiring.
- **Spring container** - responsible to create beans and coordinate relationships between those objects via DI. 
- **Developer** - responsible to tell Spring which beans to create and how to wire them together. 
- Spring offers three primary wiring mechanisms:
  - Explicit configuration in XML
  - Explicit configuration in Java
  - Implicit bean discovery and automatic wiring

Spring’s configuration styles are mix-and-match, so you could choose XML to wire up some beans, use Spring’s JavaConfig for other beans, and let other beans be automatically discovered by Spring.
