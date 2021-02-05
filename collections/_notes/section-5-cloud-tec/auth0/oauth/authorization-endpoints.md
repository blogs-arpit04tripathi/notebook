---
layout: post
title: Authorization endpoint
permalink: /:collection/auth0/endpoints/authorization
---

The Authorization endpoint is used to interact with the resource owner and get the authorization to access the protected resource.

The request parameters of the Authorization endpoint are:
- response_type: Tells the authorization server which grant to execute. Refer to the [How Response Type Works paragraph](https://auth0.com/docs/protocols/oauth2#how-response-type-works) for details.
- client_id: The id of the application that asks for authorization.
- redirect_uri: Holds a URL. A successful response from this endpoint results in a redirect to this URL.
- scope: A space-delimited list of permissions that the application requires.
- state: An opaque value, used for security purposes. If this request parameter is set in the request, then it is returned to the application as part of the redirect_uri.

**How response type works**
- This endpoint is used by the Authorization Code and the Implicit grant types. The authorization server needs to know which grant type the application wants to use, since it affects the kind of credential it will issue: for Authorization Code grant it will issue an authorization code (which later can be exchanged with an Access Token), while for Implicit grant it will issue an Access Token.

**Authorization Code vs Access Token**
An authorization code is an opaque string, meant to be exchanged with an Access Token at the token endpoint. An Access Token is an opaque string (or a JWT in Auth0 implementation) that denotes who has authorized which permissions (scopes) to which application.
 
In order to inform the authorization server which grant type to use, the response_type request parameter is used:
- For Authorization Code grant set response_type=code. This way the response will include an authorization code.
- For Implicit grant set response_type=token. This way the response will include an Access Token. An alternative is to set response_type=id_token token. In this case the response will include both an Access Token and an ID Token.

**ID Token**
The ID Token is a JWT that contains information about the logged in user. It was introduced by OpenID Connect (OIDC). For more info, see OpenID Connect and ID Token.
