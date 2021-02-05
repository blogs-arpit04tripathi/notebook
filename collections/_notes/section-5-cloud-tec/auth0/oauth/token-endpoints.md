---
layout: post
title: Token endpoint
permalink: /:collection/auth0/endpoints/token
---

- The Token endpoint is used by the application in order to get an Access Token or a Refresh Token. It is used by all flows, except for the Implicit Flow (since an Access Token is issued directly).
- In the Authorization Code Flow, the application exchanges the authorization code it got from the Authorization endpoint for an Access Token.
- In the Client Credentials Flow and Resource Owner Password Credentials Grant, the application authenticates using a set of credentials and then gets an Access Token.

**How response mode works**

The OAuth 2.0 Multiple Response Type Encoding Practices specification, added a new parameter that specifies how the result of the authorization request is formatted. This parameter is called response_mode, it's optional, and it can take the following values:
- query: This is the default for Authorization Code grant. A successful response is 302 Found, which triggers a redirect to the redirect_uri. The response parameters are embedded in the query component (the part after ?) of the redirect_uri in the Location header.
- fragment: This is the default for Implicit grant. A successful response is 302 Found, which triggers a redirect to the redirect_uri (which is a request parameter). The response parameters are embedded in the fragment component (the part after #) of the redirect_uri in the Location header.
- form_post: This response mode is defined by the OAuth 2.0 Form Post Response Mode specification. A successful response is 200 OK and the response parameters are embedded in an HTML form as hidden params. The action of the form is the redirect_uri and the onload attribute is configured to submit the form. Hence, after the HTML is loaded by the browser, a redirection to the redirect_uri is done.
- web_message: This response mode is defined by the OAuth 2.0 Web Message Response Mode specification. It uses HTML5 Web Messaging instead of the redirect for the Authorization Response from the Authorization Endpoint. This is particularly useful when using Silent Authentication. To use this response mode you have to register your app's URL at the Allowed Web Origins field of your Application's settings.

```xml
HTTP/1.1 200 OK
<html>
 <head><title>Submit</title></head>
 <body onload="javascript:document.forms[0].submit()">
  <form method="post" action="https://my-redirect-uri.com/callback">
    <input type="hidden" name="state" value="klsdfY78FVN3sl6DWSjsdhfsd8r67832nb"/>
    <input type="hidden" name="access_token" value="eyJ...plD"/>
  </form>
 </body>
</html>
```
