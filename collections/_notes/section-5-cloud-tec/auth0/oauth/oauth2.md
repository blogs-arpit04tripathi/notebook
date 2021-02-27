---
layout: post
title: OAuth 2.0 Protocol
permalink: /:collection/auth0/oauth2
---

- OAuth 2.0 is the industry-standard protocol for authorization.
- OAuth protocol (also called framework) allows third-party applications to grant limited access to an HTTP service, either on behalf of a resource owner or by allowing the third-party application to obtain access on its own behalf. Access is requested by a client; it can be a website or a mobile application for example.
- OAuth 2.0 is a protocol that allows a user to grant limited access to their resources on one site, to another site, without having to expose their credentials.

To get access to the protected resources OAuth 2.0 uses Access Tokens. An Access Token is a string representing the granted permissions.
By default, Auth0 generates Access Tokens, for API Authorization scenarios, in JSON Web Token (JWT) format. JWTs contain three parts: a header, a payload, and a signature:
- The header contains metadata about the type of token and the cryptographic algorithms used to secure its contents.
- The payload contains a set of claims, which are statements about the permissions that should be allowed, and other information like the intended audience and the expiration time.
- The signature is used to validate that the token is trustworthy and has not been tampered with.

The permissions represented by the Access Token, in OAuth 2.0 terms are known as scopes. When an application authenticates with Auth0, it specifies the scopes it wants. If those scopes are authorized by the user, then the Access Token will represent these authorized scopes.

|OAuth roles||
|---|---|
|Resource Owner|the entity that can grant access to a protected resource. Typically this is the end-user.|
|Resource Server|the server hosting the protected resources. This is the API you want to access.|
|Client|the app requesting access to a protected resource on behalf of the Resource Owner.|
|Authorization Server|the server that authenticates the Resource Owner, and issues Access Tokens after getting proper authorization. In this case, Auth0.|
|User Agent|the agent used by the Resource Owner to interact with the Application, for example a browser or a native application.|

![auth0-basic-flow.png]({{site.cdn}}/auth0/auth0-basic-flow.png)

1. The Application (Client) asks for authorization from the Resource Owner in order to access the resources.
2. Provided that the Resource Owner authorizes this access, the Application receives an Authorization Grant. This is a credential representing the Resource Owner's authorization.
3. The Application requests an Access Token by authenticating with the Authorization Server and giving the Authorization Grant.
4. Provided that the Application is successfully authenticated and the Authorization Grant is valid, the Authorization Server issues an Access Token and sends it to the Application.
5. The Application requests access to the protected resource by the Resource Server, and authenticates by presenting the Access Token.
6. Provided that the Access Token is valid, the Resource Server serves the Application's request.

![authenticate.png]({{site.cdn}}/auth0/authenticate.png)
![oauth-vs-openid.png]({{site.cdn}}/auth0/oauth-vs-openid.png)
