---
stoplight-id: sv2qsla8mv64y
---

# Payment object

## Attributes

|Attribute|	Type|	Description|
|--|--|--|
|id	|string	|The unique, permanent, Cash App Afterpay-generated Order ID.|
|token	|string	|Checkout token that was used to complete payment.|
|status|	string|	An order status of "APPROVED" or "DECLINED".|
|created|	string|	The UTC timestamp of when the payment was completed, in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format.|
|originalAmount	|[Money](Money-object.md)|	Total amount charged to the customer for the order.|
|openToCaptureAmount|	[Money](Money-object.md)	|Remaining amount that can be captured. Will always be zero for [Immediate Payment Flow](Immediate-Payment-Flow.md) orders.|
|paymentState	|string|	Current state for capturing payments. Will be one of: "AUTH_APPROVED", "AUTH_DECLINED", "PARTIALLY_CAPTURED", "CAPTURED", "CAPTURE_DECLINED","VOIDED".|
|merchantReference|	string	|The merchant's order id/reference that this payment corresponds to.|
|refunds	|[Refund](Refund-object.md)	|An array of refunds. Note: in response to a [Capture Full Payment](../../reference/Immediate-Payment-Flow.v2.yaml/paths/~1v2~1payments~1capture/post) call, this array will always be empty, since refunds cannot occur until payment is captured.|
|orderDetails|	[Order Details](Order-Details-object.md)|	The details of the order bound to the payment.|
|events	|[Payment Event](Payment-Event-object.md)|	One or more payment events that have occurred against the order.|

 Link to [Capture Full Payment](../../reference/Immediate-Payment-Flow.v2.yaml/paths/~1v2~1payments~1capture/post)

## Example Payment object

```json
{
  "id" : "12345678",
  "token" : "ltqdpjhbqu3veqikk95g7p3fhvcchfvtlsiobah3u4l5nln8gii9",
  "status" : "APPROVED",
  "created" : "2024-01-01T00:00:00.000Z",
  "originalAmount" : {
    "amount" : "100.00",
    "currency" : "USD"
  },
  "openToCaptureAmount" : {
    "amount" : "100.00",
    "currency" : "USD"
  },
  "paymentState" : "AUTH_APPROVED",
  "merchantReference" : "merchantOrderId-1234",
  "refunds" : [
    ...
  ],
  "orderDetails" : {
    ...
  },
  "events" : [ {
    "id" : "1OUR16OTqL3DgJ3ELlwKowU9v6K",
    "created" : "2024-01-01T00:00:00.000Z",
    "expires" : "2024-01-01T00:00:00.000Z",
    "type" : "AUTH_APPROVED",
    "amount" : {
      "amount" : "100.00",
      "currency" : "USD"
    }
  }, ... ]
}
```