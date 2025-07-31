---
stoplight-id: dc0gz7j8d3k7r
---

# Discount object

## Attributes

|Attribute|	Type|	 Status|Description|
|--|--|--|--|
|displayName|	string |required	|A display name for the discount. Limited to 128 characters.|
|amount|	[Money](Money-object.md) |required	|The discount amount.|

## Example Discount object

```json
{
  "displayName": "New Customer Coupon",
  "amount": {
    "amount": "29.99",
    "currency": "USD"
  }
}
```
