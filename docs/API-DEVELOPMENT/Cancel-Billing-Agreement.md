---
stoplight-id: 3afmtb16jsglj
internal: true
---

# Cancel Billing Agreement

_Cancel an existing Billing Agreement._

You must cancel a Billing Agreement when a customer or you, the merchant, want to end an agreement.

The process starts with the following delete:

`DELETE /v2/billing-agreements/{token}`

This endpoint cancels an active billing agreement.

Sample Request

```http
DELETE https://api.afterpay.com/v2/billing-agreements/{token} HTTP/1.1
Host: api.afterpay.com
Accept: application/json
```

Request Parameters

| Name  | In   | Type   | Required | Description                                |
| :---- | :--- | :----- | :------- | :----------------------------------------- |
| token | path | string | yes      | The token of the agreement to be canceled. |

Responses

| Status | Meaning               | Description                                                                                                                                                                                        | Schema    |
| :----- | :-------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------- |
| 200    | OK                    | Successful. Returns the billing agreement object with a status of canceled.                                                                                                                        | Agreement |
| 401    | Unauthorized          | Invalid Merchant API credentials were passed in the Authorization header.                                                                                                                          | Error     |
| 404    | Not Found             | The agreement with the given ID could not be found.                                                                                                                                                | Error     |
| 405    | Method Not Allowed    | The request used an unacceptable HTTP method. Depending on the endpoint, only PUT or POST requests are allowed. Use the OPTIONS HTTP method to decide which methods are allowed for each endpoint. | Error     |
| 406    | Not Acceptable        | The request included an Accept header for something other than application/json or "_/_"                                                                                                           | Error     |
| 412    | Precondition Failed   | The agreement has already been canceled.                                                                                                                                                           | Error     |
| 500    | Internal Server Error | A common cause of this response from PUT/POST endpoints is that the request body is missing or empty.                                                                                              | Error     |

Example responses

200 Response

```json
{
  "id": "_7IgXzApNiRoxpEb04LbAFQShsvdE_H3",
  "merchantReference": "merchant-billing-agreement-1234",
  "pageUrl": "https://merchant.com/billing-agreement",
  "consumer": {
    "phoneNumber": "0400 000 000",
    "givenNames": "Joe",
    "surname": "Customer",
    "email": "test@example.com"
  },
  "createdAt": "2021-04-16T02:49:04.740Z",
  "status": "CANCELLED",
  "cancelledAt": "2021-07-05T11:23:07.740Z"
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

412 Response

```json
{
  "errorCode": "invalid_billing_agreement_status",
  "errorId": "16628d4fb02900d4",
  "message": "The billing agreement has already been cancelled.",
  "httpStatusCode": 412
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

<!-- theme: info -->

> **Note**
>
> To cancel a Billing Agreement, you must be authenticated by MerchantAuthentication.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
