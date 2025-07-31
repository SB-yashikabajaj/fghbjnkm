---
stoplight-id: 351kc13n7yyn0
---

# Shipping Courier Object

## Attributes

| Attribute | Type                       | Description                                                                 |
|-----------|----------------------------|-----------------------------------------------------------------------------|
| shippedAt | optional string (ISO-8601) | The time at which the order was shipped (ISO 8601 UTC/Zulu time).           |
| name      | optional string            | The name of the courier. For pick-up in-store orders use INSTORE_PICKUP     |
| tracking  | optional string            | The tracking number provided by the courier.                                |
| priority  | optional string            | The shipping priority. If provided, must be either “STANDARD” or “EXPRESS”. |

## Error Response
Returned if an API request is unsuccessful.

| Error | Error Message                                       |
|-------|-----------------------------------------------------|
| 422   | courier.shippedAt must be a valid ISO 8601 date     |
| 422   | courier.priority must be one of [STANDARD, EXPRESS] |

