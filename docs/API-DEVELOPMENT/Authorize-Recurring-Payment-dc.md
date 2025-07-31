---
stoplight-id: 17euja5ngmk2g
internal: true
---

# Authorize Recurring Payment (Deferred Capture)

_Request recurring payment authorisation using a billing agreement as the payment method._

Deferred capture is useful for merchants who ship goods in a recurring payment scenario. You, the merchant, first authorize the payment. If the authorization is successful you dispatch the order to the warehouse for packing and shipping. Once the item or items have been shipped, you capture the payment.

For the Authorize Recurring Payment flow, the authorisation uses a Billing Agreement as the payment method. This endpoint determines the order approval status.

If the order is approved, the Auth (authorisation) has an expiration date and time. This information is returned in the events list for the AUTH_APPROVED payment event.

The process starts with this post:

`POST /v2/recurring-payments/auth`

Sample Request

```http
POST https://api.afterpay.com/v2/recurring-payments/auth HTTP/1.1
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
    "currency": "GBP"
  },
  "consumer": {
    "phoneNumber": "0400 000 000",
    "givenNames": "Joe",
    "surname": "Customer",
    "email": "test@example.com"
  },
  "billing": {
    "name": "Joe Customer",
    "line1": "Flat 5",
    "line2": "46 Collins Street",
    "area1": "Some-Town-Somewhere",
    "region": "Suffolk",
    "postcode": "AB1 2XY",
    "countryCode": "UK",
    "phoneNumber": "0400 000 000"
  },
  "shipping": {
    "name": "Joe Customer",
    "line1": "Flat 5",
    "line2": "46 Collins Street",
    "area1": "Some-Town-Somewhere",
    "region": "Suffolk",
    "postcode": "Ab1 2XY",
    "countryCode": "UK",
    "phoneNumber": "0400 000 000"
  },
  "courier": {
    "shippedAt": "2019-01-01T00:00:00+10:00",
    "name": "UK Fast",
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
        "currency": "GBP"
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
    "currency": "GBP"
  },
  "shippingAmount": null
}
```

Responses

| Status | Meaning                | Description                                                                                                                                                                                                                                                     | Schema  |
| :----- | :--------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------ |
| 201    | Created                | If payment is approved by Afterpay, returns a Payment object in response, with a status of _APPROVED_.                                                                                                                                                          | Payment |
| 400    | Bad Request            | The request body contains invalid or improperly formatted JSON.                                                                                                                                                                                                 | Error   |
| 401    | Unauthorized           | Invalid Merchant API credentials were passed in the Authorisation header.                                                                                                                                                                                       | Error   |
| 402    | Payment Required       | The payment is declined by Afterpay, for example, if invalid card details were entered. Afterpay returns a Payment object in response, with a status of DECLINED. This occurs if the billing agreement token is invalid, expired, completed, or does not exist. | Error   |
| 403    | Forbidden              | None.                                                                                                                                                                                                                                                           | Error   |
| 405    | Method Not Allowed     | The request was made using an unacceptable HTTP method. Depending on the endpoint, only PUT or POST requests are allowed. Use the OPTIONS HTTP method to determine which methods are allowed for each endpoint.                                                 | Error   |
| 406    | Not Acceptable         | The request included an Accept header for something other than application/json or _/_.                                                                                                                                                                         | Error   |
| 415    | Unsupported Media Type | The request did not include a Content-Type header, or its value was anything other than application/json.                                                                                                                                                       | Error   |
| 422    | Unprocessable Entity   | The _create checkout_ request could not be processed for one of the reasons listed below.                                                                                                                                                                       |         |

**Unprocessable Entity reasons - 422 in the table above**

- invalid_object: One or more required fields were missing or invalid
- unsupported_payment_type: The amount is outside the merchant’s payment limits, as returned by \_Get Configuration\_
- unsupported_currency: One or more money objects may have contained a currency that differs from the merchant's account currency.|Inline| |500|Internal Server Error| A common cause of this response from PUT/POST endpoints is that the request body is missing or empty. |Error|

Example Responses

201 Response

```json
{
  "id": "12345678",
  "token": "ltqdpjhbqu3veqikk95g7p3fhvcchfvtlsiobah3u4l5nln8gii9",
  "status": "APPROVED",
  "created": "2023-01-01T00:00:00.000Z",
  "originalAmount": {
    "amount": "16.00",
    "currency": "GBP"
  },
  "openToCaptureAmount": {
    "amount": "0.00",
    "currency": "GBP"
  },
  "paymentState": "AUTH_APPROVED",
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
      "name": "Joe Consumer",
      "line1": "Flat 5",
      "line2": "46 Collins Street",
      "area1": "Some-Town-Somewhere",
      "region": "Suffolk",
      "postcode": "AB1 2XY",
      "countryCode": "GB",
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
          "currency": "GBP"
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
      "currency": "GBP"
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
        "currency": "GBP"
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

Declined Payment

If the payment is declined by Afterpay, it returns a Payment object in response, with a status of “DECLINED”. For example, if invalid card details were entered.

This occurs if the billing agreement token is invalid, expired, completed, or does not exist.

```json
{
  "id": "12345678",
  "token": "ltqdpjhbqu3veqikk95g7p3fhvcchfvtlsiobah3u4l5nln8gii9",
  "status": "DECLINED",
  "created": "2019-01-01T00:00:00.000Z",
  "originalAmount": {
    "amount": "29.99",
    "currency": "GBP"
  },
  "openToCaptureAmount": {
    "amount": "29.99",
    "currency": "GBP"
  },
  "paymentState": "AUTH_DECLINED",
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
      "line1": "Flat 5",
      "line2": "46 Collins Street",
      "area1": "Some-Town-Somewhere",
      "region": "Suffolk",
      "postcode": "AB1 2XY",
      "countryCode": "UK",
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
          "currency": "GBP"
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
      "currency": "GBP"
    }
  },
  "events": [
    {
      "id": "1OUR16OTqL3DgJ3ELlwKowU9v6K",
      "created": "2019-01-01T00:00:00.000Z",
      "expires": "2019-01-01T00:00:00.000Z",
      "type": "AUTH_DECLINED",
      "amount": {
        "amount": "16.00",
        "currency": "GBP"
      }
    }
  ]
}
{
  "errorCode": "invalid_token",
  "errorId": "16628d4fb02900d4",
  "message": "The checkout token is invalid, expired, completed, or does not exist.",
  "httpStatusCode": 402
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

The Create Checkout request could not be processed for one of these reasons:

- invalid_object: One or more required fields were missing or invalid.
- unsupported_payment_type: The amount is outside of the merchant’s payment limits, as returned by Get Configuration.
- unsupported_currency: One or more money objects may have contained a currency that differs from the merchant’s account currency.

```json
{
  "errorCode": "invalid_object",
  "errorId": "16628d4fb02900d4",
  "message": "One or more required fields were missing or invalid",
  "httpStatusCode": 422
}
{
  "errorCode": "unsupported_payment_type",
  "errorId": "16628d4fb02900d4",
  "message": "Unsupported payment type",
  "httpStatusCode": 422
}
{
  "errorCode": "unsupported_currency",
  "errorId": "16628d4fb02900d4",
  "message": "Unsupported currency",
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

Response Schema

Enumerated Values

| Property     | Value              |
| :----------- | :----------------- |
| status       | APPROVED           |
| status       | DECLINED           |
| paymentState | AUTH_APPROVED      |
| paymentState | AUTH_DECLINED      |
| paymentState | PARTIALLY_CAPTURED |
| paymentState | CAPTURED           |
| paymentState | CAPTURE_DECLINED   |
| paymentState | VOIDED             |
| priority     | STANDARD           |
| priority     | EXPRESS            |
| type         | BILLING            |
| status       | ACTIVE             |
| status       | COMPLETED          |
| status       | CANCELLED          |
| status       | EXPIRED            |

## Capturing the Payment

The payment is captured in the same way as any other standard payment is captured. See the [Deferred Capture](Deferred-Capture.md) topic for more details

> 📘 Note
>
> To do any of the above operations, you must be authenticated by MerchantAuthentication.

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
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
