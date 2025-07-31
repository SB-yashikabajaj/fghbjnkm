---
stoplight-id: l2vl3f9o8m9tk
internal: true
---

# Create Recurring Payment (Immediate Capture)

_Create a new recurring payment with the Billing Agreement as the payment method._

This method creates a new recurring payment using the Billing Agreement as the payment method.

When you use the Billing Agreement Token, new orders can be created based on the details in the request body. To achieve this, a Billing Agreement token is provided as the payment method.

The process starts with the following post:

`POST /v2/recurring-payments`

Sample Request

```http
POST https://api.afterpay.com/v2/recurring-payments HTTP/1.1
Host: api.afterpay.com
Content-Type: application/json
Accept: application/json
```

Request Parameters

| Name | In   | Type                    | Required | Description |
| :--- | :--- | :---------------------- | :------- | :---------- |
| body | body | RecurringPaymentRequest | No       |             |

Example Request Body

```json
{
  "requestId": "259380f5-a9ac-4607-b987-d9c4baa34f83",
  "paymentMethod": {
    "type": "BILLING_AGREEMENT",
    "token": "_7IgXzApNiRoxpEb04LbAFQShsvdE_H3"
  },
  "amount": {
    "amount": "16.00",
    "currency": "AUD"
  },
  "consumer": {
    "phoneNumber": "0400 000 000",
    "givenNames": "Joe",
    "surname": "Customer",
    "email": "test@example.com"
  },
  "billing": {
    "name": "Joe Customer",
    "line1": "Level 5",
    "line2": "406 Collins Street",
    "area1": "Melbourne",
    "region": "VIC",
    "postcode": "3000",
    "countryCode": "AU",
    "phoneNumber": "0400 000 000"
  },
  "shipping": {
    "name": "Joe Customer",
    "line1": "Level 5",
    "line2": "406 Collins Street",
    "area1": "Melbourne",
    "region": "VIC",
    "postcode": "3000",
    "countryCode": "AU",
    "phoneNumber": "0400 000 000"
  },
  "courier": {
    "shippedAt": "2019-01-01T00:00:00+10:00",
    "name": "Australia Post",
    "tracking": "AA0000000000000",
    "priority": "STANDARD"
  },
  "description": null,
  "items": null,
    "subscriptions": [
    {
      "name": "VIP Membership Renewal",
      "merchantReference": "vip-1234",
      "pageUrl": "https://merchant.example.com/vip.html",
      "imageUrl": "https://merchant.example.com/vip.jpg",
      "price": {
        "amount": "16.00",
        "currency": "AUD"
      },
      "recurringBilling": {
        "unit": "MONTH",
        "count": 1
      }
    }
  ],
  "discounts": [],
  "merchantReference": "merchantOrder-1234",
  "taxAmount": {
    "amount": "1.45",
    "currency": "AUD"
  },
  "shippingAmount": null
}
```

Responses

| Status | Meaning                | Description                                                                                                                                                                                                                                                                | Schema  |
| :----- | :--------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------ |
| 201    | Created                | If the payment is approved by Afterpay, it returns a Payment object in response, with a status of APPROVED. If the payment is declined by Afterpay, for example, if invalid card details were entered, it returns a Payment object in response, with a status of DECLINED. | Payment |
| 400    | Bad Request            | The request body contains invalid or improperly formatted JSON.                                                                                                                                                                                                            | Error   |
| 401    | Unathorized            | Invalid Merchant API credentials were passed in the Authorization header.                                                                                                                                                                                                  | Error   |
| 402    | Payment Required       | The agreement token is invalid, expired, completed, or does not exist.                                                                                                                                                                                                     | Error   |
| 403    | Forbidden              | Access is forbidden. Recurring payments product must be enabled on the merchant account.                                                                                                                                                                                   | Error   |
| 405    | Method Not Allowed     | The request was made with an unacceptable HTTP Method. Depending on the endpoint, only PUT or POST requests are allowed. Use the OPTIONS HTTP Method to decide which methods are allowed for each endpoint.                                                                | Error   |
| 406    | Not Acceptable         | The request included an Accept header for something other than application/json or _/_.                                                                                                                                                                                    | Error   |
| 415    | Unsupported Media Type | The request did not include a Content-Type header, or its value was anything other than application/json.                                                                                                                                                                  | Error   |
| 422    | Unprocessable Entity   | One or more required fields were missing or invalid.                                                                                                                                                                                                                       | Error   |
| 500    | Internal Server Error  | A common cause of this response from PUT/POST endpoints is that the request body is missing or empty.                                                                                                                                                                      | Error   |

Example responses

200 - 201 Approved

```json
{
  "id": "12345678",
  "token": "001._ltqdpjhbqu3veqikk95g7p3fhvcchfvtlsiobah3u4l5nln8gii9",
  "status": "APPROVED",
  "created": "2019-01-01T00:00:00.000Z",
  "originalAmount": {
    "amount": "16.00",
    "currency": "AUD"
  },
  "openToCaptureAmount": {
    "amount": "0.00",
    "currency": "AUD"
  },
  "paymentState": "CAPTURED",
  "merchantReference": "merchantOrderId-1234",
  "refunds": [],
  "orderDetails": {
    "consumer": {
      "phoneNumber": "0400 000 000",
      "givenNames": "Joe",
      "surname": "Customer",
      "email": "test@example.com"
    },
    "billing": {
      "name": "Joe Customer",
      "line1": "Level 5",
      "line2": "406 Collins Street",
      "area1": "Melbourne",
      "region": "VIC",
      "postcode": "3000",
      "countryCode": "AU",
      "phoneNumber": "0400 000 000"
    },
    "items": null,
        "subscriptions": [
      {
        "name": "VIP Membership Renewal",
        "merchantReference": "vip-1234",
        "pageUrl": "https://merchant.example.com/vip.html",
        "imageUrl": "https://merchant.example.com/vip.jpg",
        "price": {
          "amount": "16.00",
          "currency": "AUD"
        },
        "recurringBilling": {
          "unit": "MONTH",
          "count": 1
        }
      }
    ],
    "discounts": [],
    "taxAmount": {
      "amount": "1.45",
      "currency": "AUD"
    }
  },
  "events": [
    {
      "id": "1OUR16OTqL3DgJ3ELlwKowU9v6K",
      "created": "2019-01-01T00:00:00.000Z",
      "expires": "2019-01-01T00:00:00.000Z",
      "type": "AUTH_APPROVED",
      "amount": {
        "amount": "16.00",
        "currency": "AUD"
      }
    },
    {
      "id": "1OUR16OTqL3DgJ3ELlwKowU9v6K",
      "created": "2019-01-01T00:00:00.000Z",
      "expires": "2019-01-01T00:00:00.000Z",
      "type": "CAPTURED",
      "amount": {
        "amount": "16.00",
        "currency": "AUD"
      }
    }
  ]
}
```

400 Response

```json
{
  "errorCode": "invalid_json",
  "errorId": "16628d4fb02900d4",
  "message": "Bad request",
  "httpStatusCode": 400
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

402 Response

```json
{
  "errorCode": "invalid_token",
  "errorId": "16628d4fb02900d4",
  "message": "The billing agreement token is invalid, expired, completed, or does not exist.",
  "httpStatusCode": 402
}
```

403 Response

```json
{
  "errorCode": "forbidden",
  "errorId": "16628d4fb02900d4",
  "message": "Access is forbidden. Recurring payments product must be enabled on the merchant account.",
  "httpStatusCode": 403
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

415 Response

```json
{
  "errorCode": "error",
  "errorId": "16628d4fb02900d4",
  "message": "Unsupported media type",
  "httpStatusCode": 415
}
```

422 Response

```json
{
  "errorCode": "invalid_object",
  "errorId": "16628d4fb02900d4",
  "message": "One or more required fields were missing or invalid.",
  "httpStatusCode": 422
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
> To create a recurring payment, you must be authenticated by MerchantAuthentication.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
