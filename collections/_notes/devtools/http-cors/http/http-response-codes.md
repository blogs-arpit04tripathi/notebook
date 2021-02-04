---
layout: post
title: HTTP Response Codes
permalink: /:collection/http/response-codes
---


|GROUP|Type|DESCRIPTION|
|---|---|---|
|1xx|Informational|further action needs to be taken by the user agent in order to fulfill the request.|
|2xx|Successful   |the client's request was successfully received, understood, and accepted.|
|3xx|Redirection  |further action needs to be taken by the user agent in order to fulfill the request.|
|4xx|Client Error |intended for cases in which the client seems to have erred.|
|5xx|Server Error |server is aware that it has erred or is incapable of performing the request.|

|2xx|Description|
|---|---|
|200 : OK         |Successfully executed
|201 : CREATED    |- New resources has been created<br>- response body is either empty or contains URI(s) of the created resource<br>- The location header should should also contain the new URI|
|202 : ACCEPTED   |- request was valid and has been accepted but has not yet been processed.<br>- response should include a URI to poll for status updates on the request.<br>- Allows for asynchronous request|
|204 : NO_CONTENT |request was successful but the server did not have a response|

|3xx|Description|
|---|---|
|301 : MOVED_PERMANENTLY      |new location should be returned in the response|
|304 : Not Modified           |
|307 : Temporary Redirect     |

|4xx|Description|
|---|---|
|400 : BAD_REQUEST            |Malformed or invalid request|
|401 : UNAUTHORIZED           |Invalid authorization credentials|
|403 : FORBIDDEN              |Disallowed request. Security error|
|404 : NOT_FOUND              |Resource not found|
|405 : METHOD_NOT_ALLOWED     |Method (verb) not allowed for requested resource.<br>Response will provide an “Allow” header to indicate what is allowed|
|408 :                        |Request Time-out|
|414 :                        |Request-URI Too Large|
|415 : UNSUPPORTED_MEDIA_TYPE |Client submitted a media type that is incompatible for the specified resource.|

|5xx|Description|
|---|---|
|500 : INTERNAL_SERVER_ERROR  |Catchall for server processing problem|
|503 : SERVICE_UNAVAILABLE    |Response in the face of too many request|

# HTTP
- [100 Continue](https://support.airship.com/hc/en-us/articles/213492003--Expect-100-Continue-Issues-and-Risks)
- [7-http-methods-every-web-developer-should-know-and-how-to-test-them](https://assertible.com/blog/7-http-methods-every-web-developer-should-know-and-how-to-test-them)
