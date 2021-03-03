---
layout: post
title: Writing a Controller
permalink: /:collection/spring/mvc/writing-controller
---

- **@Controller** - stereotype annotation, to enable for component-scanning and declared as a bean.
  - could have annotated with @Component.
- @RequestMapping **value** attribute accepts an array of String.
  - `@RequestMapping({"/", "/homepage"})`

```java
@Controller
@RequestMapping(method=GET, value="/spittles")
public class SpittleController {

  @Autowired 
  private SpittleRepository spittleRepository;
  
  @RequestMapping(method=RequestMethod.GET)
  public String spittles(Model model) {
    model.addAttribute("spittleList",spittleRepository.findSpittles(Long.MAX_VALUE, 20));
    // model.addAttribute(spittleRepository.findSpittles(Long.MAX_VALUE, 20));
    return "home";
  }
}
```
```java
@RequestMapping(method=RequestMethod.GET)
public List<Spittle> spittles() {return spittleRepository.findSpittles(Long.MAX_VALUE, 20));}
```

- **Model** is a map that will be handed to the view to be rendered.
  - When addAttribute() is called without specifying a key, the key is inferred from the type of object.
    - In this case, because it’s a `List<Spittle>`, the key will be inferred as spittleList.
  - When handler method returns an object or a collection
    - value returned is put into the model
    - model key is inferred from its type.
    - logical view name inferred from the request path
      - GET /spittles, view name is spittles (chopping off the leading slash).

```xml
<c:forEach items="${spittleList}" var="spittle" >
  <li id="spittle_<c:out value='spittle.id'/>">
    <div class="spittleMessage"><c:out value="${spittle.message}"/></div>
  </li>
</c:forEach>
```
