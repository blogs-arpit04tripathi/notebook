---
layout: post
title: Annotation @RestController
permalink: /:collection/spring/rest/rest-controller
---

# @RestController
- @RestController instead of @Controller
  - Spring applies message conversion to all handler methods in the controller.
  - You don’t need to annotate each method with @ResponseBody.
- Defaulting Controllers For Message Conversion
- Available from Spring 4.0

# @RequestBody and @ResponseBody

- @RequestBody - tells Spring message converter to convert request a resource representation coming from a client into an object.
- @ResponseBody - tells Spring message converter to convert response in client required format.

```java
@RequestMapping(
    method=RequestMethod.POST,
    consumes="application/json",
    produces="application/json"
  )
@ResponseBody
public Spittle saveSpittle(@RequestBody Spittle spittle) {
  return spittleRepository.save(spittle);
}
```

- **Content-Type** header set to application/json.
  - client sent the Spittle data in a JSON representation.
  - DispatcherServlet looks for a message converter to convert JSON into Java objects.
    - If Jackson2 library is on the classpath, then **MappingJackson2HttpMessageConverter** is used.
- **Accept** header includes application/json.
  - If Jackson JSON library is on the classpath, then either **MappingJacksonHttpMessageConverter** or **MappingJackson2HttpMessageConverter** will be used.
- By default, Jackson JSON libraries use reflection.
