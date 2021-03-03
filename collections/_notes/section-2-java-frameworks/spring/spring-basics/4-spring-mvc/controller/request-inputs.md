---
layout: post
title: Accepting request input
permalink: /:collection/spring/mvc/request-inputs
---

- TOC
{:toc}

<hr><br>

- Query parameters
- Path variables
- Form parameters

# @PathVariable and @RequestParam

```
/spittles/54321?count=30&max=100
```
```java
private static final String MAX_LONG_AS_STRING = Long.toString(Long.MAX_VALUE);

@RequestMapping(value="/{spittleId}", method=RequestMethod.GET)
public List < Spittle > spittles(
    @PathVariable("spittleId") long spittleId,
    @RequestParam(value = "max", defaultValue = MAX_LONG_AS_STRING) long max,
    @RequestParam(value = "count", defaultValue = "20") int count) {
    return spittleRepository.findSpittles(max, count);
}
```

- As a general rule
  - query parameters should not be used to identify a resource.
  - `GET /spittles/12345` is better than `/spittles/show?spittle_id=12345`.
  - `GET /spittles/12345` identifies a resource to be retrieved.
  - `/spittles/show?spittle_id=12345` describes an operation with a parameter - essentially RPC over HTTP.

# Processing forms

```java
@Controller
@RequestMapping("/spitter")
public class SpitterController {

    @Autowired
    private SpitterRepository spitterRepository;

    @RequestMapping(value = "/register", method = GET)
    public String showRegistrationForm() {
        return "registerForm";
    }

    @RequestMapping(value = "/register", method = POST)
    public String processRegistration(Spitter spitter) {
        spitterRepository.save(spitter);
        return "redirect:/spitter/" + spitter.getUsername();
    }
}
```

- InternalResourceViewResolver identifies `redirect:` prefix and interpret it as a redirect specification instead of as a view name.
  - It will redirect to the path for a user’s profile page.
- InternalResourceViewResolver recognizes prefix - `redirect:` and `forward:`.
