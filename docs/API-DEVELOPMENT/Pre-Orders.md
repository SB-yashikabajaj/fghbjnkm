---
stoplight-id: vzzmn6pxcqd6p
internal: true
---

# Overview: Pre-Orders

## Scope

Use the pre-order feature if you are not sure that all items in a checkout will be fulfilled within 13 days. For pre-orders, Afterpay offers the concept of a purchase agreement. Depending on the case, a purchase agreement may have multiple orders, and so have multiple installment payment schedules for the customer. This allows you, the merchant, to use existing payment processing logic for these pre-orders.

Pre-order functionality is currently supported only on API v2.

Furthermore, the following exclusions apply to availability:

- Merchants who use Express Checkout are not currently able to use Pre-orders, although this will be available in future
- Currently, only US Merchants are supported.

For details on support for Pre-order functionality within an Afterpay Direct API (v2 API) integration, see the [Pre-orders Payment Flow](pre-orders-payment-flow.md) topic.

## Use Cases Supported

The following business use cases are supported by Pre-order functionality:

- **Pre-orders:** You want to allow customers to buy items that are not currently available, but will become available in the near future.  Pre-orders may or may not include a deposit at the time of checkout
- **Backorders:** You want to allow customers to buy items that are temporarily unavailable, but will become available in the near future.  Backorders may or may not include a down payment at the time of checkout

To support the above, Afterpay has provided support for the following use cases:

- **Initial Order Only:** You, the merchant, can ship the entire order within 13 days.  This is not a Pre-order scenario. See [Immediate Capture Overview](Immediate-Capture-Overview.md) and/or [Deferred Capture Overview](Deferred-Capture.md)
- **Initial Order and Pre-order Orders:** You can partially ship the order within 13 days, but a portion of the order will ship after 13 days or is unknown
- **Pre-order Only:** For every item in the checkout you will not ship the item within 13 days, or the shipment time is unknown for the entire order
- **Pre-order Only with Up-front Deposit:** You need an up-front deposit for items that will not ship within 13 days, or the shipment time is unknown
- **Initial Order and Pre-order Orders with Up-front Deposit:** You need an up-front deposit for items which will not ship within 13 days or the shipment time is unknown.  Furthermore, you can ship a portion of the order within 13 days

## Customer Experience

A customer checking out items which will not ship within 13 days will see that their payment schedule starts when the items are ready.
![](../../assets/images/preorder.png)

A customer checking out with both pre-order items which will not ship within 13 days and items which will ship soon will see both of the following:

- The initial order payment schedule, including amount due today.
- The items marked as pre-order that will not ship within 13 days along with notification that remaining payments will begin once pre-order items become available to ship.

![](../../assets/images/preorder2.png)

## Pre-orders Documentation Contents

- [Pre-orders Overview](Pre-Orders.md)
- [Pre-orders Payment Flow](pre-orders-payment-flow.md)
- [Upgrading to Pre-orders](Upgrading-to-Pre-orders.md)

---
