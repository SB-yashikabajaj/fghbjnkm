---
stoplight-id: fotq5xw26az05
internal: true
---

# Get Billing Agreement

_Retrieve a Billing Agreement at this endpoint._

This function retrieves the Billing Agreement to an endpoint, once the Billing Agreement has been setup and created.

The process starts with the following GET:

`GET /v2/billing-agreements/{token}`

This endpoint retrieves a billing agreement. A sample request is:

```http
GET https://api-sandbox.afterpay.com/v2/billing-agreements/{token} HTTP/1.1
Host: api-sandbox.afterpay.com
Accept: application/json
```

### Request Parameters

| Name  | In   | Type   | Required | Description                                 |
| :---- | :--- | :----- | :------- | :------------------------------------------ |
| token | path | string | true     | The token of the agreement to be retrieved. |

### Standard Responses (including webhook)

<!-- theme: warning -->

> **Important**
>
> The webhook status and the GET API status have different names in some cases, but have the same meaning. See the table below:

| GET API Status | Webhook Status | Description                                                                                                                                                                                                                                                                                                                                                      |
| -------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ACTIVE         | ACTIVE         | **Definition**:<br> ACTIVE status means the Billing Agreement Token is valid and can be used to process future Recurring Payments. <br>**Customer Scenario**: <br>The customer has gone through the checkout flow and the merchant successfully captures the Billing Agreement token. The customer's account has a valid credit card.                            |
| CANCELLED      | TERMINATED     | **Definition**:<br> CANCELLED/TERMINATED status means a token can no longer take any path back to ACTIVE status. <br> **Customer Scenarios**: <br> The customer cancels their Billing Agreement Token, OR the customer deletes their Afterpay Account, OR the merchant calls the 'delete' Billing Agreement endpoint.                                            |
| EXPIRED        | INACTIVE       | **Definition** <br> EXPIRED/INACTIVE' status means a token is still valid, but the credit card attached to the customer's account is expired. <br> Once a valid credit card is added to the customer's account, the token returns to ACTIVE status. <br> **Customer Scenario**:<br> The customer has a token, but their credit card is expired in their account. |

### Numeric Responses

| Status | Meaning               | Description                                                                                                                                                                                                     | Schema    |
| :----- | :-------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------- |
| 200    | OK                    | Sucessful                                                                                                                                                                                                       | Agreement |
| 401    | Unauthorized          | Invalid Merchant API credentials were passed in the Authorization header.                                                                                                                                       | Error     |
| 404    | Not Found             | The agreement with this ID could not be found.                                                                                                                                                                  | Error     |
| 405    | Method Not Allowed    | The request was made using an unacceptable HTTP method. Depending on the endpoint, only PUT or POST requests are allowed. Use the OPTIONS HTTP method to determine which methods are allowed for each endpoint. | Error     |
| 406    | Not Acceptable        | The request included an Accept header for something other than application/json or _/_.                                                                                                                         | Error     |
| 500    | Internal Server Error | Commonly this response from PUT/POST endpoints is caused by the request body  missing or empty.                                                                                                                 | Error     |

### Example Responses

200 Response

```json
{
  "token": "_7IgXzApNiRoxpEb04LbAFQShsvdE_H3",
  "type": "BILLING",
  "status": "ACTIVE",
  "merchantReference": "merchant-billing-agreement-1234",
  "created": "2021-04-16T02:49:04.740Z",
  "cancelled": null,
  "expires": null
}
```

401 Response

```json
{
  "errorCode": "unauthorized",
  "errorId": "16628d4fb02900d4",
  "message": "Credentials are required to access this resource.",
  "httpStatusCode": 401
}
```

404 Response

```json
{
  "errorCode": "not_found",
  "errorId": "16628d4fb02900d4",
  "message": "Not found",
  "httpStatusCode": 404
}
```

405 Response

```json
{
  "errorCode": "method_not_allowed",
  "errorId": "16628d4fb02900d4",
  "message": "Method not allowed",
  "httpStatusCode": 405
}
```

406 Response

```json
{
  "errorCode": "error",
  "errorId": "16628d4fb02900d4",
  "message": "Not acceptable",
  "httpStatusCode": 406
}
```

500 Response

```json
{
  "errorCode": "error",
  "errorId": "16628d4fb02900d4",
  "message": "Internal server error",
  "httpStatusCode": 500
}
```

> **Note**
>
> To handle the response, you must be authenticated by MerchantAuthentication.

In some circumstances a Billing Agreement has to be cancelled. For information on this, see the [Cancel Billing Agreement](Cancel-Billing-Agreement.md) topic.

### Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
