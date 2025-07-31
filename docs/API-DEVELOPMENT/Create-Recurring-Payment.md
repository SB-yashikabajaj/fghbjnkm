---
stoplight-id: 9nxcbbvdf1nnx
internal: true
---

# Create Recurring Payment

_What are the API calls to initiate recurring payments?_

This flow allows a merchant to initiate transactions to the merchant from a customer who previously approved a billing agreement.

## Create Recurring Payment

- [Create Recurring Payment (Immediate Capture)](../../reference/Immediate-Payment-Flow.v2.yaml/paths/\~1v2\~1payments\~1capture/post) or [Authorize Recurring Payment (Deferred Capture)](../../reference/Deferred-Payment-Flow.v2.yaml/paths/\~1v2\~1payments\~1auth/post)

![create-recurring-payment-diagram-1.png](../../assets/images/create-recurring-payment-diagram-1.png)

The Create Recurring Payment call is idempotent, so it is safe for you to retry requests within 24 hours using the same unique requestId.

## Recurring Payments - More Information

- [Recurring Payments](Recurring-Payments.md)
- [Store Afterpay as Payment Method](Store-Afterpay-as-Payment-Method.md)
- [Checkout and Store Afterpay as Payment Method](Checkout-and-Store-Afterpay-as-Payment-Method.md)
- [Recurring Payment Flows](Recurring-Payments-Flows.md)
- [Setup Billing Agreement Approval](Setup-Billing-Agreement-Approval.md)
- [Create a Billing Agreement](Create-Billing-Agreement.md)
- [Cancel a Billing Agreement](Cancel-Billing-Agreement.md)
- [Get a Billing Agreement](Get-Billing-Agreement.md)
- [Create a Recurrring Payment - Immediate Capture](Create-Recurring-Payment-ic.md)
- [Authorize a Recurring Payment - Deferred Capture](Authorize-Recurring-Payment-dc.md)
- [USA Legal Requirements](USA-Legal-Requirements.md)
