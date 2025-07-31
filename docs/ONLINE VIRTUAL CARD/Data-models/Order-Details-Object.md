---
stoplight-id: lwahk4fiaar0j
---

# Order Details Object

## Attributes


| Attributes     | Type                | Description                                            |
|----------------|---------------------|--------------------------------------------------------|
| consumer       | required Consumer   | The customer who placed or is placing the order.       |
| billing        | optional Contact    | The customer's billing address.                        |
| shipping       | optional Contact    | The customer's shipping address.                       |
| courier        | optional Courier    | The customer's chosen shipping courier.                |
| tems           | optional Item[]     | An array of order items.                               |
| discounts      | optional Discount[] | An array of discounts.                                 |
| taxAmount      | optional Money      | The included tax amount, after applying all discounts. |
| shippingAmount | optional Money      | The shipping price charged to the customer.            |

