---
stoplight-id: 0wfnm6nua0m42
internal: true
---

# Create Billing Agreement

_Create a Billing Agreement once it has been setup_

A billing agreement is a contract between you, the merchant, and the customer. The agreement authorises you to create and pay for orders. This step creates the Billing Agreement once the customer has asked for the Billing Agreement.

The process starts with the following POST:

`POST /v2/billing-agreements`

This finalises the Billing Agreement after the Billing Agreement has been approved by the customer. A sample request is:

```http
POST https://api.afterpay.com/v2/billing-agreements HTTP/1.1
Host: api.afterpay.com
Content-Type: application/json
Accept: application/json
```

Request Parameters

| Name | In   | Type        | Required | Description |
| :--- | :--- | :---------- | :------- | :---------- |
| body | body | AuthRequest | No       |             |

Example Request Body

```json
{
  "requestId": "259380f5-a9ac-4607-b987-d9c4baa34f83",
  "token": "001.ltqdpjhbqu3veqikk95g7p3fhvcchfvtlsiobah3u4l5nln8gii9",
  "merchantReference": "merchantOrderId-1234"
}
```

Responses

| Status | Meaning | Description | Schema    |
| :----- | :------ | :---------- | :-------- |
| 200    | OK      | Successful  | Agreement |

Example Responses

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

<!-- theme: info -->

> **Note**
>
> To handle the response, you must be authenticated by MerchantAuthentication.

Now the Billing Agreement is finalised, you should save the Billing Agreement Token within the merchant's system to initiate future orders. See the [Get Billing Agreement](Get-Billing-Agreement.md) topic for that information.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
