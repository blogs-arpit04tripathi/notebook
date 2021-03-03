---
layout: post
title: Password
permalink: /:collection/auth0/grant-types/password
---

![img]({{site.cdn}}/auth0/grant-password.png)

With the resource owner password credentials grant type, the user provides their service credentials (username and password) directly to the application, which uses the credentials to obtain an access token from the service. This grant type should only be enabled on the authorization server if other flows are not viable. Also, it should only be used if the application is trusted by the user (e.g. it is owned by the service, or the user's desktop OS).
