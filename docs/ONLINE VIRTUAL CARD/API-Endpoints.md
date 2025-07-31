---
stoplight-id: 7a8xnrv7dalsy
---

# API-Endpoints




## Production
### US & CA

`https://api-plus.us.afterpay.com/v2/`
## Sandbox
### US & CA

`https://api-plus.us-sandbox.afterpay.com/v2/`

## Authentication
The Afterpay Online API uses Basic HTTP Authentication, a simple authentication scheme built into the HTTP protocol, as specified by RFC 7617.

With the exception of Ping, all Online API endpoints require this form of authentication. Failure to correctly authenticate an API request will result in a "401 Unauthorized" response.

Consider the following example.

|Merchant ID	|Secret Key|
|--|--|
|32|	abcdefgh|


>In conventional HTTP terms, "Merchant ID" is the username and "Secret Key" is the password.

The credentials are joined by a colon character (without any spaces), then base64-encoded.

|Plain Text	|Base64 Encoded|
|--|---|
|32:abcdefgh|	MzI6YWJjZGVmZ2g=|

The 'Authorization' header can then be formed by including the word 'basic', followed by a single space character, followed by the base64-encoded credential pair.

|Final Header|
|--|
|Authorization: Basic MzI6YWJjZGVmZ2g=|

<!--theme: warning-->
> **Security Notice**<br>
> Please note that the base64-encoding of the 'Authorization' header is unrelated to security. All HTTP headers and bodies (for both requests and responses) between the Merchant and Afterpay are encrypted with TLS. The reason for base64-encoding is solely to comply with the RFC 7617 standard, which allows non-HTTP characters and multibyte strings to be used for Basic HTTP Authentication.

## Idempotent Requests
The Afterpay API supports [idempotency](https://en.wikipedia.org/wiki/Idempotence) that allows the safe retry of requests, guaranteeing the operation is only performed once.

For example, if a Create Refund request fails with a network error, the request can be retried with the same 'requestId' and 'merchantReference'. This is especially important for partial refunds to ensure retry attempts are not processed as separate refunds.

Afterpay recommends that merchants generate UUIDs for use as request IDs. The resources that include a 'requestId' may send back the same response for requests made with the same 'requestId' for up to 24 hours.



> When performing an idempotent retry of an API request, an HTTP 409 response may be encountered. This generally indicates that the original request was received, but is still processing. Please try again in a few moments, and repeat with the same 'requestId' until something other than a 409 response is received.

## Timeouts
Afterpay will attempt to respond to all requests as soon as possible. However, in some cases, latency delays may occur. Particularly where an API call is dependent on downstream banking networks, response times can vary considerably, and can be unusually high in rare cases.

As a guideline, this document provides recommended network connection open timeout and read timeout values for each API resource. Resources that are dependent on banking networks will have higher timeout values.

All resources that are identified as idempotent can be safely retried when timeouts occur.

