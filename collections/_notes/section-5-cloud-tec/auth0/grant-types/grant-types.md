---
layout: post
title: Authorization Grant Types
permalink: /:collection/auth0/grant-types
---

The OAuth 2.0 Authorization Framework specification defines four flows to get an Access Token. These flows are called grant types. Deciding which one is suited for your case depends mostly on the type of your application.
- Authorization Code: used by Web Apps executing on a server. This is also used by mobile apps, using the Proof Key for Code Exchange (PKCE) technique.
- Implicit: used by JavaScript-centric apps (Single-Page Applications) executing on the user's browser.
- Resource Owner Password Credentials: used by trusted apps.
- Client Credentials: used for machine-to-machine communication.

The specification also provides an extensibility mechanism for defining additional types.

![grant-types.png]({{site.cdn}}/auth0/grant-types.png)
