---
layout: post
title: CSRF (Cross Site Request Forgery)
permalink: /:collection/auth0/csrf
---

# State Parameter
Authorization protocols provide a state parameter that allows you to restore the previous state of your application. The state parameter preserves some state object set by the client in the Authorization request and makes it available to the client in the response.

# CSRF attacks
The primary reason for using the state parameter is to mitigate [CSRF attacks](https://en.wikipedia.org/wiki/Cross-site_request_forgery).
When you use state for CSRF mitigation on the redirection endpoint, that means that within the state value there is a unique and non-guessable value associated with each authentication request about to be initiated. It’s that unique and non-guessable value that allows you to prevent the attack by confirming if the value coming from the response matches the one you expect (the one you generated when initiating the request). The state parameter is a string so you can encode any other information in it.

![csrf.png]({{site.cdn}}/auth0/csrf.png)

# Redirect users
You can also use the state parameter to encode an application state that will round-trip to the client application after the transaction completes. In this way, the application can put the user where they were before the authentication process happened.
 
# Limitations
- From a security perspective, neither the request nor the response is integrity-protected so a user can manipulate them. That is true for adding a parameter to the redirect_uri as well.
- The allowed length for state is not unlimited. If you get the error 414 Request-URI Too Large try a smaller value.
