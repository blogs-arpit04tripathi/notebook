---
layout: post
title: JSESSIONID
permalink: /:collection/webservices/jsessionid
---

**When / what are the conditions when a JSESSIOINID is created?**
Is it per a domain? For instance, if I have a Tomcat app server, and I deploy multiple web applications, will a different JSESSIONID be created per context (web application), or is it shared across web applications as long as they are the same domain?

Answer:
- SESSIONID cookie is created/sent when session is created. Session is created when your code calls request.getSession() or request.getSession(true) for the first time. 
- If you just want to get the session, but not create it if it doesn't exist, use request.getSession(false) -- this will return you a session or null. 
- In this case, new session is not created, and JSESSIONID cookie is not sent. 
- (This also means that session isn't necessarily created on first request... you and your code are in control when the session is created)

Sessions are per-context:

SRV.7.3 Session Scope
HttpSession objects must be scoped at the application (or servlet context) level. The underlying mechanism, such as the cookie used to establish the session, can be the same for different contexts, but the object referenced, including the attributes in that object, must never be shared between contexts by the container.(Servlet 2.4 specification)

Update: Every call to JSP page implicitly creates a new session if there is no session yet. 
- This can be turned off with the session='false' page directive, in which case session variable is not available on JSP page at all.
- you can disable the setting of JSESSIONID by a JSP , <%@ page session="false" %>.
