---
layout: post
title: JWT (JSON Web Tokens)
permalink: /:collection/auth0/jwt
---

JWT is a self-contained authentication token that can contain information such as a user identifier, roles and permissions of a user, and anything else you might want to store in it. It can be easily read and parsed by anyone and can be verified as authentic with a secret key. 
 
# Advantages of JWT with Microservices
- We can set it up so that it already contains any authorities that the user has. This means that each service does not need to reach out to our authorization service in order to authorize the user.
- They are serializable and small enough to fit inside a request header.
 
# How It Works
- Firstly, request is a POST to an unprotected authentication endpoint with a username and password.
- On successful authentication, the response contains a JWT. 
- All further requests come with an HTTP header that contains this JWT token in the form of Authorization: xxxxx.yyyyy.zzzzz.
- Any service-to-service requests will pass this header along so that any of the services can apply authorization along the way.

```java
// signature algorithm
data = base64urlEncode( header ) + “.” + base64urlEncode( payload )
hashedData = hash( data, secret )
signature = base64urlEncode( hashedData )
```

The data string is hashed with the secret key using the hashing algorithm specified in the JWT header. The resulting hashed data is assigned to hashedData. This hashed data is then base64url encoded to produce the JWT signature.

```
header.payload.signature
```

# How does JWT protect our data?

It is important to understand that the purpose of using JWT is NOT to hide or obscure data in any way. The reason why JWT are used is to prove that the sent data was actually created by an authentic source.

As demonstrated in the previous steps, the data inside a JWT is encoded and signed, not encrypted. The purpose of encoding data is to transform the data’s structure. Signing data allows the data receiver to verify the authenticity of the source of the data. So encoding and signing data does NOT secure the data. On the other hand, the main purpose of encryption is to secure the data and to prevent unauthorized access.

Since JWT are signed and encoded only, and since JWT are not encrypted, JWT do not guarantee any security for sensitive data.

The application server receives the secret key from the authentication server when the application sets up its authentication process. Since the application knows the secret key, when the user makes a JWT-attached API call to the application, the application can perform the same signature algorithm as in Step 3 on the JWT. The application can then verify that the signature obtained from it’s own hashing operation matches the signature on the JWT itself (i.e. it matches the JWT signature created by the authentication server). If the signatures match, then that means the JWT is valid which indicates that the API call is coming from an authentic source. Otherwise, if the signatures don’t match, then it means that the received JWT is invalid, which may be an indicator of a potential attack on the application. So by verifying the JWT, the application adds a layer of trust between itself and the user.
