---
layout: post
title: Classification of Applications
permalink: /:collection/auth0/classification-of-applications
---

- Confidential Apps - Can securely hold credentials
- Public Apps

# Confidential Applications
can hold credentials securely, they require a trusted backend server to store the secret(s).

**Grant types**
- Because confidential Applications use a trusted backend server, these Apps can use grant types that require them to authenticate by specifying their client ID and secret when calling the token endpoint.
- Auth0 provides many different authentication and authorization grant types or flows and allows you to indicate which grant types are appropriate based on the grant_types property of your Auth0-registered app.
- The following are considered to be confidential applications:
    - A web application with a secure backend that uses the Authorization Code Flow, Password grant, or Password grant with Realm support
	- A machine-to-machine (M2M) application that uses the Client Credentials Flow

**ID Tokens**
Because confidential applications are capable of holding secrets, you can have ID Tokens issued to them that have been signed in one of two ways:
- Symmetrically, using their client secret (HS256)
- Asymmetrically, using a private key (RS256)

# Public Applications
Public applications cannot hold credentials securely.

**Grant types**
- Public applications can only use grant types that do not require the use of their client secret.
- The following are public applications:
    - A native desktop or mobile application that uses the Authorization Code Flow with PKCE
	- A JavaScript-based client-side web application (such as a single-page app) that uses the Implicit Flow grant

**ID Tokens**
- Because public applications are unable to hold secrets, ID Tokens issued to them must be:
  - Signed asymmetrically using a private key (RS256)
  - Verified using the public key corresponding to the private key used to sign the token
