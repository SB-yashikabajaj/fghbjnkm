---
stoplight-id: byubazn07r3uw
internal: true
---

# Store Afterpay as a Payment Method

_What are the API calls required to setup recurring payments with Afterpay?_

The first step to enable Recurring Payments functionality is to setup customer approval by calling the billing agreements approval API.

## Setup Billing Agreement Approval

- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md) <!--(api-link-here-setup-billing-agreement-approval) -->

![store-afterpay-diagram.png](../../assets/images/store-afterpay-diagram.png)

You will call the Setup Billing Agreement Approval endpoint to tell Afterpay information including:

- Customer Information
- The URL you would like to direct the customer to when they complete the Afterpay approval flow
- Agreement Information

Afterpay responds with a token used to identify this approval flow.\
e.g. `002.5lmerr3k945d00c7htvcrdff83q36kp10a247m212fjpa5ju`

The token is used with the [Afterpay.js JavaScript library](../AFTERPAY-MESSAGING/JavaScript-Library.md) to direct the customer to the Afterpay approval flow.

![store-afterpay-screenshot.png](../../assets/images/store-afterpay-screenshot.png)

After the customer completes the approval flow, they are returned to the Merchant website URL provided in the Setup Billing Agreement request. If using the [redirect method](../ONLINE-API/Standard-Checkout.md#redirect-method)<!--(api-link-here#redirect-method)--> the URL will have status appended to the Merchant URL. For Example:

- If the customer successfully completes the approval flow:\
  `www.merchant-example.com/confirm?&status=SUCCESS&orderToken=002.5lmerr3k945d00c7htvcrdff83q36kp10a247m212fjpa5ju`

- If the customer closes the window:\
  `www.merchant-example.com/confirm?&status=CANCELLED&orderToken=002.5lmerr3k945d00c7htvcrdff83q36kp10a247m212fjpa5ju`

> A [popup method](../ONLINE-API/Standard-Checkout.md#popup-method) is also available that uses a `postMessage` to communicate the status and token.

Now that you have the customer's approval of the billing agreement, you can create the Billing Agreement itself.

## Create Billing Agreement

- [Create Billing Agreement](Create-Billing-Agreement.md)

![store-afterpay-diagram-2.png](../../assets/images/store-afterpay-diagram-2.png)

This API creates the billing agreement, and returns to you a billing agreement token. Save this token for future transactions.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
