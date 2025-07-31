---
stoplight-id: iqrlt6u3bw0ge
---


# V1 to V2
This page outlines the key points that should be reviewed when upgrading from API V1 to V2. The recommendation is to reach out to your Afterpay Contact to receive direct support and guidance on when completing this activity.

![Afterpay-v1-v2-flows.png](../../assets/images/Afterpay-v1-v2-flows.png)

## `CreateOrder` vs `CreateCheckout` - Retrieving an Afterpay Token
### Endpoint Differences
- V1: `CreateOrder /v1/orders`: Response Body includes 2 values in response, (token and expiry)
- V2: `CreateCheckout /v2/checkouts`: Response Body includes 3 values in response, (token, expiry, and redirect URL)

### Object Differences
**Field `totalAmount` is updated to `amount`**

- V1: v1/orders request Body Parameters for amount is `totalAmount`.
- V2: v2/checkouts Body Parameters for amount is `amount` - functionally the same as `totalAmount` for v1/orders.

**Field `Suburb` is updated to `area1`**

- V1: v1/orders request Body Parameters for amount is “Suburb”
- V2: v2/checkouts Body Parameters for amount is “area1” - functionally the same as “totalAmount” for v1/orders.

**Field `State` is updated to `region`**

- V1: v1/orders request Body Parameters for amount is `State`.
- V2: v2/checkouts Body Parameters for amount is `region` - functionally the same as `totalAmount` for v1/orders.

## `GetOrder` vs `GetCheckout` - Checking the Token’s Order Information
### Endpoint Differences
- V1: /GetOrder (provides all values associated with order)
- V2: /GetCheckout (provides all values associated with order)

## V1 Capture vs V2 Capture - Immediate Capture
<!--theme: warning-->
> API V2 provides Approved and Declined responses inside the response body.
> Ensure you check the response body for the order's Approval Status.

When integrating in API V1, an Approved order results in a 201 response; whilst a Declined order provides a 402 response. When upgrading from V1 to V2, instead of checking for a 402 response, please check the response body for the Approval Status.

### Endpoint Differences

- V1: Capture /v1/payments/capture
  - Capture Approved: Response code: 201
  - Capture Decline: Response Code: 402 (error)
- V2:Capture /v2/payments/capture
  - Capture Approved: Response code: 201 - Body response includes Approval Status
  - Capture Declined: Response code: 201 - Body response includes Decline Status

> Order Management requests (i.e. GET Payment, Create refund, Update payment, Reverse Payment, etc.) can only be utilised once a payment capture has occurred. I.e. do not try and attempt a GET v2/payments/{order_id} request prior to receiving a 201 (successful) response for the v2/payments/capture or v2/payments/{order_id}/capture request. This also applies to v1 order management endpoints.

## V2 Auth/Capture/Void
Auth and Capture was not previously available in API V1. This addition includes three endpoints, Auth/Capture/Void. When moving from V1 Immediate Capture to V2 Auth/Capture process, note that all uncaptured orders will be automatically voided 13 days after completing this request. Voided orders cannot be 'un-voided'.

### Endpoint Differences
**Auth**
- V1: Auth/Capture not available
- V2: Auth /v2/payments/auth

- Auth Approved: Body response includes Approval Status
- Auth Declined: Body response includes Decline Status
- Auth has an expiry time, please check the expiry time to ensure all orders are CAPTURED, or Partially or completely Voided before the expiry time is up.
- At the expiry time, orders will be automatically voided; any paid funds returned to the customer and the order will no longer be able to be captured.

**Capture**
- V2: Capture /v2/payments/{orderId}/capture
- Once Auth has been approved, the order can be captured. This endpoint can capture a full or partial amounts of the order. Any amounts successfully captured will be settled from Afterpay to the merchant's nominated bank account based on your settlement terms.

**Void**
- V2: Void /v2/payments/{orderId}/void
- Any orders / services unable to be shipped should be voided as soon as the information is confirmed. Authorised Payments that have not been captured will be automatically voided after 13 days. For example if a customer buys multiple products; and one of those is out of stock (never to return) a void with the amount of that product is anticipated.



> Authorised payments (201 v2/payments/auth responses) will be automatically voided 13 days after completing this request.
> <br/><br/>Please note that once a payment has been voided it can no longer be captured (v2/payments/{order_id}/capture)
> <br/>Any captured amounts can still be refunded via v2/payments/{​order_id}/refund against the portion of the order that was captured.

