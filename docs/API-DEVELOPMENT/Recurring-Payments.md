---
stoplight-id: 2clsv0hxv9t0u
internal: true
---

# Recurring Payments

## Scope

Recurring Payments functionality allows customers to save their Afterpay details with merchants for future payments in certain use cases. Merchants must be approved by Afterpay to offer one or more Recurring Payment types/use cases described below.

For both Fixed Recurring Payments and Flexible Recurring Payments, merchants will have approval in advance from the customer for future payments. In both cases the customer does not need to be present to make a payment. Merchants can use the approval in advance to take payments from the customer on a regular or irregular schedule. This applies to both Fixed Recurring Payments and Flexible Recurring Payments. An example of a Fixed Recurring Payment is a subscription. An example of a Flexible Recurring Payment is where the amounts and/or frequency of payments fluctuates.

The merchant must maintain the schedule of any Fixed Recurring Payments or Flexible Recurring Payments and use an API call to start each individual payment.

Recurring Payments functionality is currently supported only on API v2.

Recurring Payments functionality is only available in AU and NZ for approved merchants.  It is available in the US for approved merchants on an exceptions basis only.

## Recurring Payment Types

The following business use cases are supported by Recurring Payments functionality:

**Fixed Recurring Payments**

Definition: Automatic payment of a fixed amount on a monthly, quarterly, annual or other fixed cadence basis (as applicable). These payments are for an ongoing subscription, where the customer does not need to be present on the merchant's website(s) to approve each Recurring Payment. The only time the customer needs to be present is when this type of payment is set up. An example of a Fixed Recurring Payment is a regular, ongoing subscription or membership.

**Flexible Recurring Payments**

Definition: Automatic payment over a fixed or variable cadence basis (as applicable) where the amount may vary across billing periods according to the customer's usage or needs. This may include flexible subscription arrangements and bill payments where the customer does not need to be present on merchant website(s) to approve each Recurring Payment. The only time the customer needs to be present is when this type of payment is set up. An example of a Flexible Recurring Payment is a utility bill with usage-based pricing.

**Future Orders**

Definition: Payment for ad hoc future Afterpay purchases without the customer needing to subsequently log in to their Afterpay account to complete the Afterpay purchase. The customer must be present on the merchant website(s) to approve each Recurring Payment.

Approval for each use case above is dependent upon a number of factors. These factors include merchant location, merchant business vertical, and individual merchant risk factors. Contact your Afterpay representative for more detail.

To support the above, Afterpay has provided support for the following use cases:

- **Customer Stores Payment Method with Merchant:** By following this flow, the merchant gets approval from the customer to take payments from the customer to the merchant. This is the first step in each of the business use cases above, when the merchant doesn't need an upfront payment from the customer

- **Customer Stores Payment Method with Merchant with Upfront Payment:** The merchant gets approval from the customer to take payments as well as take a payment at the time of approval. This is the first step in each of the business use cases above, when the merchant takes an upfront payment from the customer

- **Merchant Initiates Customer Payment Against Stored Payment Method:** This flow uses the stored payment method from the previous use cases to start a new payment from the customer to the merchant

## Customer Experience

A customer storing their payment method with a merchant.

![recurring-payments-1.png](../../assets/images/recurring-payments-1.png)

A customer storing their payment method with a Merchant with an upfront payment.

![recurring-payments-2.png](../../assets/images/recurring-payments-2.png)

## Afterpay Messaging

With Recurring Payments, use the following Afterpay Messaging at checkout:

_4 interest-free payments estimated at $XX.00 every 2 weeks. See Payment Schedule for final details._

<!-- theme: info -->

> **Note**
>
> In the message above, make the $ amount the highest of the 4 instalments if there is any variation between instalment amounts (e.g. due to rounding).

## Recurring Payments - More Information

- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
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
