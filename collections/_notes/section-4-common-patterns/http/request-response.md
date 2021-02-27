---
layout: post
title: Http Request and Response Message
permalink: /:collection/http/request-response
---

- The request line and headers must all end with `<CR><LF>` 
  - `<CR>` - carriage return character
  - `<LF>` - line feed character `\r\n`
- The empty line must consist of only `<CR><LF>` and no other whitespace.
- In the HTTP/1.1 protocol, all headers except Host are optional.

![req-res.png]({{site.cdn}}/webservices/http/req-res.png)

# MIME Types (Multipurpose Internet Mail-Extension)
- Internet media type.
- referred as Content-types
- two-part identifier for file formats on the Internet.
  - `type/subtype` - text/html, text/plain
- Generally present after the name of a header in several protocols.

# Cookies
- HTTP cookie / web cookie / browser cookie.
- small piece of data sent from a website and stored in a user's web browser while browsing.
  - When user revisits, cookies can be retrieved to notify the website about the user's previous activity.
  - This can include clicking particular buttons, logging in, or a record of which pages were visited by the user even months or years ago.
- Cookies were designed to be a reliable mechanism for websites to remember the state of the website or activity the user had taken in the past.

# Avoiding caching
- web server response contains `Cache-Control: no-cache`.
  - web browser or other caching system must check with the originating server first for subsequent requests.

# HTTP Conditional GET
- returns HTTP 304 response rather than HTTP 200.
- indicates that the resource has not been modified since the previous GET request and the resource will not be returned to the requesting client as part of the response.
