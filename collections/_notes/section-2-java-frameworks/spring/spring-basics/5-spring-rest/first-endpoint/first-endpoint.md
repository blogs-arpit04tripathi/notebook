---
layout: post
title: Creating REST endpoint
permalink: /:collection/spring/rest/first-endpoint
---

- Controllers deal with resources in terms of the Java objects.
- Spring offers two options to transform a resource into the required representation by client: 
  - **Content negotiation** - A view is selected that can render the model into a representation to be served to the client.
  - **Message conversion** - A message converter transforms response object into a representation required by the client.

```
/spittles/456?max=100&count=10
```
```java
@Controller
@RequestMapping("/spittles")
public class SpittleController {

    private static final String MAX_LONG_AS_STRING = "9223372036854775807";
    
    @Autowired
    private SpittleRepository spittleRepository;

    @RequestMapping(
        value={"/{id}","/{id}/show"},
        method={RequestMethod.POST, RequestMethod.GET},
        produces={"application/json", "application/xml"},
        consumes="text/html"
      )
    @ResponseBody
    public List<Spittle> spittles(
        @PathVariable("id") int id,
        @RequestParam(value = "max", defaultValue = MAX_LONG_AS_STRING, required=false) long max,
        @RequestParam(value = "count", defaultValue = "20") int count) {
        return spittleRepository.findSpittles(max, count);
    }
}
```

- Annotations
  - @RequestMapping
  - @PathVariable
  - @RequestParam
  - @RequestBody
  - @ResponseBody

