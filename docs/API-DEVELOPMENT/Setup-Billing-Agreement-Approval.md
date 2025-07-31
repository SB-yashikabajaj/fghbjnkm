---
stoplight-id: 4t1m64mjhu95n
internal: true
---

# Setup Billing Agreement Approval

_Set up a Billing Agreement ready for creation_

A billing agreement is a contract between the merchant and the customer. Afterpay sets the agreement that authorises the merchant to create and pay for orders. This step sets up the Billing Agreement ready for it to be created.

The process starts with the following POST:

`POST /v2/billing-agreements/approvals`

This offers billing agreement terms to the customer for them to accept or reject. Assuming they accept the billing agreement terms, the flow continues. A sample request is:

```http
POST https://api.afterpay.com/v2/billing-agreements/approvals HTTP/1.1
Host: api.afterpay.com
Content-Type: application/json
Accept: application/json
```

Request Parameters

| Name | In   | Type                            | Required | Description |
| :--- | :--- | :------------------------------ | :------- | :---------- |
| body | body | BillingAgreementApprovalRequest | No       |             |

Example Request Body

```json
{
  "consumer": {
    "phoneNumber": "0400 000 000",
    "givenNames": "Joe",
    "surname": "Customer",
    "email": "test@example.com"
  },
  "agreements": [
    {
      "type": "BILLING",
      "merchantReference": "merchant-billing-agreement-1234",
      "pageUrl": "https://merchant.com/payment-methods"
    }
  ],
  "merchantReference": "merchant-payment-method-registration-1234",
  "merchant": {
    "redirectConfirmUrl": "http://merchant.com/confirm",
    "redirectCancelUrl": "http://merchant.com/cancel"
  }
}
```

Responses

| Status | Meaning | Description | Schema                |
| :----- | :------ | :---------- | :-------------------- |
| 200    | OK      | Sucessful   | CheckoutTokenResponse |

Example Responses

200 Response

```json
{
  "expires": "2019-08-24T14:15:22Z",
  "token": "001.jqtiticbqbo1a5img3oc54pafo5ijgul3oemjjkfb47vech7cqrf4857acu6dolg",
  "redirectCheckoutUrl": "https://afterpay.com/checkout"
}
```

<!-- theme: warning -->

> **Tokens**
>
> Recurring Payments need two tokens. The token above is the Billing Agreement token. There is also a Checkout token. Do not confuse these two tokens.

> 📘 Note
>
> To handle the response, you must be authenticated by MerchantAuthentication.

Now the Billing Agreement approval is set up, you must create the Billing Agreement. See the [Create Billing Agreement](Create-Billing-Agreement.md) topic for that information.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
