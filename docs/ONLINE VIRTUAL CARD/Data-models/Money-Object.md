---
stoplight-id: dwwsz8t4kbovb
---

# Money Object

## Attributes
| Attribute | Type            | Description                                                                                                                                                                                       |
|-----------|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| amount    | required string | The amount is a string representation of a decimal number, rounded to 2 decimal places                                                                                                            |
| currency  | required string | The currency in ISO 4217 format. Supported values include "AUD", "NZD", "CAD", and "USD". However, the value provided must correspond to the currency of the Merchant account making the request. |

## Error Response
Returned if an API request is unsuccessful.

| Error | Error Message                                        |
|-------|------------------------------------------------------|
| 422   | money.amount Amount field required                   |
| 422   | money.currency Currency field required               |
| 422   | Payment type not supported for this order.           |
| 422   | amount must be greater than 0.00                     |
| 422   | money.currency must be a valid ISO 4217 format value |
