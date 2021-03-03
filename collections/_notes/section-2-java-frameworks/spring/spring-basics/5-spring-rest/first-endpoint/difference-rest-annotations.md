---
layout: post
title: Difference - @Component, @Service, @Repository, @Controller
permalink: /:collection/spring/rest/difference-rest-annotations
---

- @Component
  - specializations - @Service, @Repository, @Controller - stereotype annotations
  - used for automatic bean detection using component-scan.
- used for different classification.
- ***Difference in preprocessor and post processor of each annotation.***
- In a Multitier application, we have layers - presentation, service, business, data access etc.
	- **@Component** – generic and can be used across application.
	- **@Service** – service layer.
	- **@Controller** – presentation layer.
	- **@Repository** – persistence layer.
- @Repository
  - postprocessor automatically looks for all exception translators
    - implementations of the PersistenceExceptionTranslator interface
  - advises all beans marked with the @Repository annotation so that the discovered translators can intercept and apply the appropriate translation on the thrown exceptions.
- Similar to above, in future Spring may choose to add value for @Service, @Controller and @Repository based on their layering conventions.
- To that additional feature advantage its better to respect the convention and use them in line with layers.
- To modify auto-detected behavior, use **include-filter** or **exclude-filter**.
