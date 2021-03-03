---
layout: post
title: Origin Policies
permalink: /:collection/aws/api-gateway/origin-policies
---

# Same Origin Policy
- In Computing, same-origin-policy is important concept in the web application security model.
- Under this policy, a web browser permits scripts contained in a first web page to access data in a second web page, but only if both web pages have the same origin.
- This is done to prevent Cross-Site Scripting (XSS) attacks.
    - Enforced by web browsers.
    - Ignored by tools like PostMan and Curl.

# Cross Origin Resource Sharing (CORS)
- CORS is one way the server at the other end (not the client code in browser) can relax the same-origin-policy.
- CORS is a mechanism that allows restricted resources (eg. fonts) on the webpage to be requested from another domain outside the domain from which the first resource was served.
- Browser makes an HTTP OPTIONS call for a URL.
    - OPTIONS is HTTP methods like GET, POST, PUT
- Server returns a response saying "These other domains are approved to GET this URL"
- Error - "Origin policy cannot be read at the remote resource? You need to enable CORS on API Gateway."
