---
stoplight-id: hd3805e5y2txg
internal: true
---

# Checkout and Store Afterpay as a Payment Method

_What are the API calls required to setup recurring payments with Afterpay in the context of a transaction?_

To enable Recurring Payments functionality, first you setup customer approval for the billing agreement, and then create a Checkout.

> **Make sure you have previously retrieved minimum and maximum order amounts**
>
> Please see [Create Checkout](../../reference/Checkouts.v2.yaml/paths/\~1v2\~1checkouts/post) <!--(api-reference-guide-link-create-checkout-1) --> for more details on utilizing the [Get Configuration](../../reference/Configuration.v2.yaml/paths/\~1v2\~1configuration/get) API to retrieve order limits.

## Create Checkout and Setup Billing Agreement

- [POST /v2/checkouts](../../reference/Checkouts.v2.yaml)

You will call the Create Checkout endpoint to tell Afterpay information including:

- Customer Information

- Order Details

- Order Total

- Shipping Information

- URL you would like to direct the customer to when they complete the Afterpay checkout flow

### Agreement Information

The Checkout request must include this field:

```
"agreements": [
        {
         "type": "BILLING",
         "merchantReference": "merchant-billing-agreement-1234",
         "pageUrl": "https://merchant.com/billing-agreement"
        }
    ],  
```

Afterpay responds with a token used to identify this checkout flow.\
e.g. `002.5lmerr3k945d00c7htvcrdff83q36kp10a247m212fjpa5ju`

The token is used with the [Afterpay.js JavaScript library](../AFTERPAY-MESSAGING/JavaScript-Library.md)<!--(api-reference-guide-link-javascript-afterpayjs)--> to direct the customer to the Afterpay checkout flow.

![checkout-and-store-screenshot-1.png](../../assets/images/checkout-and-store-screenshot-1.png)

After the customer completes the checkout flow they are returned to the merchant website URL provided in the [Create Checkout](../../reference/Checkouts.v2.yaml/paths/\~1v2\~1checkouts/post) request. If using the [redirect method](../ONLINE-API/Standard-Checkout.md#redirect-method) <!--(api-reference-guide-link-redirect-method)--> the URL has a status appended to the Merchant URL. For Example:

- If the customer successfully completes the checkout flow:\
  `www.merchant-example.com/confirm?&status=SUCCESS&orderToken=002.5lmerr3k945d00c7htvcrdff83q36kp10a247m212fjpa5ju`
- If the customer closes the window:\
  `www.merchant-example.com/confirm?&status=CANCELLED&orderToken=002.5lmerr3k945d00c7htvcrdff83q36kp10a247m212fjpa5ju`

> **NOTE:**
> A [popup method](../ONLINE-API/Standard-Checkout.md#popup-method)<!--(api-reference-guide-link-popup-method) --> is also available which uses a `postMessage` to communicate the status and token.

## Choose When You Want to Capture the Order

Now that you have a successful pre-approval for the checkout you can either:

1. Capture the order directly,  or
2. Create an Auth API call to place funds on hold until you are ready to capture.

Both methods allow you to create the Billing Agreement which was approved by the customer.

See the details for both these methods in the following paragraphs:

## 1. Capture Order and Create Billing Agreement

- [POST /v2/payments/capture](../../reference/Immediate-Payment-Flow.v2.yaml/paths/\~1v2\~1payments\~1capture/post)<!--(../reference#capture-full-payment)-->

![checkout-and-store-diagram-2.png](../../assets/images/checkout-and-store-diagram-2.png)

This API captures the order and creates the billing agreement, returning to you an _id_ (that is the Afterpay order ID)for the checkout order and a billing agreement token. Save this token for future transactions.

## 2. Authorize Order and Create Billing Agreement

- [POST /v2/payments/auth](../../reference/Deferred-Payment-Flow.v2.yaml/paths/\~1v2\~1payments\~1auth/post)<!--(../reference#auth)-->

![checkout-and-store-diagram-3.png](../../assets/images/checkout-and-store-diagram-3.png)

This API authorizes the order and creates the billing agreement, returning to you an _Id_ (that is the Afterpay order ID) for the checkout order and a billing agreement token. Save this token for future transactions.

Next, for the checkout order, you can capture the authorization or do multiple partial captures.  Please refer to [Deferred Payment Flow](../ONLINE-API/Deferred-Payment-Flow.md)<!--(api-reference-link-deferred-payment-flow)--> for details.

For the Billing Agreement, you can make recurring payments using the saved billing agreement token.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
