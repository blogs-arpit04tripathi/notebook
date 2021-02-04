---
layout: post
title: OpenID Connect (OIDC)
permalink: /:collection/auth0/oidc
---

OpenID Connect (OIDC) is an authentication protocol, based on the OAuth 2.0 family of specifications. It uses simple JSON Web Tokens (JWT), which you can obtain using flows conforming to the OAuth 2.0 specifications.

While OAuth 2.0 is about resource access and sharing, OIDC is all about user authentication. Its purpose is to give you one login for multiple sites. Each time you need to log in to a website using OIDC, you are redirected to your OpenID site where you login, and then taken back to the website.

For example, if you chose to sign in to Auth0 using your Google account then you used OIDC. Once you successfully authenticate with Google and authorize Auth0 to access your information, Google will send back to Auth0 information about the user and the authentication performed. This information is returned in a JWT. You'll receive an Access Token and, if requested, an ID Token.

# How the Protocol Works

Let's use the example we mentioned earlier, signing into Auth0 using your Google account, for a high level overview on how the flow works:
1. When you choose to sign in to Auth0 using your Google account, Auth0 sends an Authorization Request to Google.
2. Google authenticates your credentials or asks you to login if you are not already signed in, and asks for your authorization (lists all the permissions that Auth0 wants, for example read your email address, and asks you if you are ok with that).
3. Once you authenticate and authorize the sign in, Google sends an Access Token, and (if requested) an ID Token, back to Auth0.
4. Auth0 can retrieve user information from the ID Token or use the Access Token to invoke a Google API.

# Access Tokens
Access Tokens are credentials that can be used by an application to access an API. Access Tokens can be an opaque string, JWT, or non-JWT token. Its purpose is to inform the API that the bearer of this token has been granted delegated access to the API and request specific actions (as specified by the scopes that have been granted).

# ID Tokens
The ID Token is a JSON Web Token (JWT) that contains identity data. It is consumed by the application and used to get user information like the user's name, email, and so forth, typically used for UI display. ID Tokens conforms to an industry standard (IETF RFC 7519) and contain three parts: a header, a body and a signature.

# Claims
- JWT Tokens contain claims, which are statements (such as name or email address) about an entity (typically, the user) and additional metadata.
- The OpenID Connect specification defines a set of standard claims. The set of standard claims include name, email, gender, birth date, and so on. However, if you want to capture information about a user and there currently isn't a standard claim that best reflects this piece of information, you can create custom claims and add them to your tokens.
