---
stoplight-id: fgkqmdoi3cwho
internal: true
---

# USA Legal Requirements

This page is for US merchants only.

It contains important legal and technical information so you, the merchant, obey US law when you use Afterpay's Recurring Payments feature to bill customers.

## Overview

When you create a billing agreement for Recurring Payments, you get a token that uniquely identifies this billing agreement.

Afterpay expects you to use the Recurring Payments API to provide and use this token for any deferred or immediate capture. A legal requirement exists for US merchants who use the token to pay for:

- **Newly placed orders** The customer uses Afterpay to place another new order with you and relies on the existing billing agreement. In other words your customer does not go through the standard Afterpay checkout flow

- **Modified orders** The customer modifies an existing recurring order or subscription. This recurring order is associated with a billing agreement, and the order amount has now changed

In both the cases above, you must message the customer. To do this, you use Afterpay owned widgets that you enable on your site or app. There are two of these widgets, the [Payment Schedule widget](#the-payment-schedule-widget) and the [Amended Order widget](#the-amended-order-widget).

## The Payment Schedule Widget

This is essential if a customer with an existing billing agreement places an Afterpay order without going through the usual Afterpay checkout flow. When the Payment Schedule widget is placed on your site, it displays the customer's payment schedule. The widget can update the payment schedule as the order total changes. For example, in response to promotional codes entered on your site.

The Payment Schedule widget is a JavaScript widget. Put it next to the call-to-action to place an order with Afterpay using an existing billing agreement.

To show an accurate payment schedule for a given customer, supply the Payment Schedule widget with a payment schedule token. See the Payment Schedule Tokens section below for details on how to get one of these tokens.

There are two versions of the Payment Schedule widget, the [Standard Payment Schedule widget](#standard-payment-schedule-widget) and the [Compact Payment Schedule widget](#compact-payment-schedule-widget).

### Standard Payment Schedule Widget

This is the default version of the Standard Payment Schedule widget. It displays accurate payment schedule information, the payment amount due today and the legal disclaimer. Use JavaScript to render the Standard Payment Schedule widget into a target container on your page. The widget is responsive and will fit any container with a minimum width of 300 pixels.

![rp-standard-widget.png](../../assets/images/rp-standard-widget.png)

Here is an example of how to initialize the Standard Payment Schedule widget, and a sample function for updating the amount to a new value.

```html
<html>
  <body>
    <div id="afterpay-widget-container"></div>
    <script>
      // Ensure this function is defined before loading afterpay.js
      function createAfterpayWidget () {
        window.afterpayWidget = new AfterPay.Widgets.PaymentSchedule({
          target: '#afterpay-widget-container',
          locale: 'en-US',
          amount: {
            amount: "1338.00",
            currency: "USD"
          },
          // Use your payment schedule token to reflect an accurate payment schedule to your customers
          paymentScheduleToken: "PAYMENT_SCHEDULE_TOKEN_PLACEHOLDER",
        })
      }

      function updateAmount() {
        window.afterpayWidget.update(
            amount: { amount: "1000.00", currency: "USD" }
        )
      }


    </script>
    <script src="https://portal.afterpay.com/afterpay.js" async onload="createAfterpayWidget()">
    </script>

    <button onclick="updateAmount()">Update amount</script>
  </body>
</html>
```

See the [Checkout Widget](../ONLINE-API/Checkout-Widget.md) topic for more information on this widget.

### Compact Payment Schedule Widget

This is a more compact version of the Payment Schedule widget. It presents the same information as the standard widget but takes up less space.

![rp-compact-widget.png](../../assets/images/rp-compact-widget.png)

Here is an example of the Compact Payment Schedule widget.

```html
<html>
  <body>
    <div id="afterpay-widget-container"></div>
    <script>
      // Ensure this function is defined before loading afterpay.js
      function createAfterpayWidget () {
        window.afterpayWidget = new AfterPay.Widgets.PaymentSchedule({
          target: '#afterpay-widget-container',
          locale: 'en-US',
          amount: {
            amount: "1338.00",
            currency: "USD"
          },
          style: {
             theme: "TIMELINE"
          },
          // Use your payment schedule token to reflect an accurate payment schedule to your customers
          paymentScheduleToken: "PAYMENT_SCHEDULE_TOKEN_PLACEHOLDER",
        })
      }
    </script>
    <script src="https://portal.afterpay.com/afterpay.js" async onload="createAfterpayWidget()">
    </script>
  </body>
</html>

```

<!-- theme: warning -->

> **Important - for any US merchant offering Afterpay Recurring Payments**
>
> If a customer with an existing billing agreement can place an Afterpay order without going through the usual Afterpay checkout flow, then:
>
> You **must** embed and display the Payment Schedule widget on your site.

## Payment Schedule Tokens

To generate an accurate payment schedule for a customer, the Payment Schedule widget needs a Payment Schedule token. This token is separate from the Billing Agreement token, and is designed to be publicly safe and has a limited usage scope.

### Get a Public Token through the Recurring Payments API

To get a Payment Schedule token that corresponds to a Billing Agreement, the Billing Agreement API exposes a POST endpoint. The endpoint accepts a Billing Agreement token, and an optional duration string in ISO8601 format. The Billing Agreement API returns a Payment Schedule token, and an expiry time for this Payment Schedule token.

The endpoint is `/v2/billing-agreements/alias`

**The Request Payload**

The payload is a JSON object:

```json
{
  "token": "required, a string identifying a BA created by the merchant",
  "duration": "recommended, ISO8601 string for the desired lifespan of the returned token"
}
```

**The Response**

You can expect a 2XX response together with the following response payload:

```json
{
  "token": "guaranteed, a string aliasing a BA, safe to use in public context",
  "expiry": "guaranteed, ISO8601 UTC timestamp string of the returned token's expiry"
}

```

403 and 404 codes are returned in cases where you, the merchant, are not authorized to use this endpoint. You may also get a 403 or 404 if the request’s token is not identified. It's possible that other conventional and case-specific 4XX errors are also returned.

Sometimes the request fails and the payment schedule cannot be rendered with a payment schedule token. If this happens, do not present the Afterpay payment method to your customer, because the payment method is non-compliant.

<!-- theme: info -->

> **Duration and Expiry**
>
> The expiry returned in the response is guaranteed, and might not respect the duration specified in the request. If no duration is specified in the request, the default expiry is 15 minutes. It is possible that the requested duration exceeds the internally-defined duration cap. In this case the maximum allowed duration is used to calculate the expiry (e.g. 1 hour). The expiry represents the Total Time Limit (TTL) of the token. The expiry is a reliable time value, so you can use it for tasks such as caching the response.

## The Amended Order Widget

Use this widget when a customer modifies an existing recurring order and changes the order amount. Specifically, the modified order must be a recurring order or a subscription, and it must have an associated Billing Agreement.

In this case, where the customer changes the order amount, you must render a brief paragraph that describes the change to the installment amount.

Here is an example of the widget displayed:

![rp-amended-order.png](../../assets/images/rp-amended-order.png)

Here is an example of the head and body of the widget that a merchant has initialized:

**Head**

```json
<script src="https://js-sandbox.squarecdn.com/square-marketplace.js" async></script>
```

**Body**

```json
<square-placement
  data-type="recurring-instalments"
  data-mpid="MPID_PLACEHOLDER"
  data-placement-id="PLACEMENT_ID_PLACEHOLDER"
  data-amount="AMOUNT_PLACEHOLDER"
  data-currency="USD"
  data-consumer-locale="en_US"
  data-is-eligible="true">
</square-placement>
```

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Recurring Payments Flow Charts](Recurring-Payments-Flows.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Create Recurring Payment](Create-Recurring-Payment.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
