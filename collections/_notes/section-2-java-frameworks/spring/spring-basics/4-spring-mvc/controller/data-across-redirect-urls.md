---
layout: post
title: Carrying data across redirect requests
permalink: /:collection/spring/mvc/data-across-redirect-urls
---

- TOC
{:toc}

<hr><br>

- **redirect:**
  - good practice to redirect after POST request.
    - this prevents client from reissuing a dangerous POST request by clicking the Refresh or back-arrow button in their browser.
  - controller returns String with `redirect:` prefix, it is used as a path to redirect the browser to.
    - the original request ends and a new HTTP GET request begins.
  - New request does not have any model data as model data carried in the original request dies with the request.
    - Passing data as path variables and/or query parameters using URL templates
    -	Sending data in flash attributes

![]({{site.cdn}}/spring/spring-mvc/redirect/redirect.png)

![]({{site.cdn}}/spring/spring-mvc/redirect/forward-vs-redirect.png)

# Redirecting with URL templates

```java
@RequestMapping(value="/register", method=POST)
public String processRegistration(
Spitter spitter, Model model) {
  spitterRepository.save(spitter);
  model.addAttribute("username", spitter.getUsername());
  model.addAttribute("spitterId", spitter.getId());
  return "redirect:/spitter/{username}";
}
```
- By using placeholder in URL template, any unsafe characters in username property are escaped.
- If username is habuma and spitterId is 42, resulting redirect path will be `/spitter/habuma?spitterId=42`.
- Sending data across a redirect via path variables and query parameters is easy and straightforward.
  - Limitation - for sending simple values, such as String and numeric values.

# Working with flash attributes

- Put Spitter into the session.
  - A session is long-lasting, spanning multiple requests.
  - put in the session before redirect and retrieve from session after redirect.
    - You’re responsible for cleaning it up from the session after the redirect.
- Spring offers capability of sending the data as flash attributes.
  - Flash attributes, carry data until next request; then they go away.
  - `RedirectAttributes`, sub-interface of Model with additional methods for setting flash attributes.

![]({{site.cdn}}/spring/spring-mvc/redirect/redirect-flash-attributes.png)

```java
@RequestMapping(value = "/register", method = POST)
public String processRegistration(Spitter spitter, RedirectAttributes model) {
    spitterRepository.save(spitter);
    model.addAttribute("username", spitter.getUsername());
    model.addFlashAttribute("spitter", spitter);
    return "redirect:/spitter/{username}";
}
```
```java
@RequestMapping(value = "/{username}", method = GET)
public String showSpitterProfile(@PathVariable String username, Model model) {
    if (!model.containsAttribute("spitter"))
        model.addAttribute(spitterRepository.findByUsername(username));
    return "profile";
}
```
