---
stoplight-id: mdj3heewnag9u
---


# Receiving and Retrieving a Dispute

In this section you can learn about:

- [Receiving disputes](#receiving-disputes)

- [Retrieving disputes](#retrieving-disputes)

When a customer opens up a dispute, Cash App Afterpay calls the webhook with `webhook_event_type = created`.

Merchants can use the **Get Dispute** endpoint below to get the detailed information of the dispute.

## Receiving disputes
### Get Dispute - Endpoint 
GET https://{afterpay_global_url}/v2/disputes/{dispute_id}

#### Connection Timeouts
| Timeout | Time (seconds) |
|------------|-----------|
| `OPEN`       | 10    | 
| `Read `       | 20    | 

#### Request Headers

| Header | Type | Example        |
|------------|-----------|---------------------|
| `User-Agent`| String | `MyCashAppAfterpayModule/1.0.0 (E-Commerce Platform Name/1.0.0; PHP/7.0.0; Merchant/60032000) https://merchant.example.com` |

| Header | Type | Default Value        |
|------------|-----------|------------------|
| `Accept`   | String    | application/json |


#### Request Parameters
| Field name | Data type | Description         |
|------------|-----------|---------------------|
| `dispute_id `       | String    | (Required) Dispute identifier |

#### Response
| Field name | Data type     | Description                 |
|------------|---------------|-----------------------------|
| `dispute`    | DisputeObject | The updated dispute object |


#### Dispute Object 

| Field name             | Data type             | Description     |
|------------------------|-----------------------|-----|
| `id`                    | String                | Dispute identifier     |
| `order`                  | String                | The token of the order that the dispute is for.     |
| `amount`                 | String                | Amount of the dispute.  (Example: 40.13)                                |
| `currency`               | String                | Currency of the dispute. (ISO-4217 standard, example: USD) |
| `reason`                 | String                | Reason for the dispute. See the section on recommended [Dispute Reasons](#dispute-reasons) below.   |
| `status`                 | String                | The current state of the dispute. Values depend on how the dispute state machine is modeled. See the section on recommended [Dispute Status](#dispute-status) below.     |
| `open`                   | Boolean               | `True` if a final decision on the dispute hasn’t been made yet.   |
| `responseDueBy`          | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))            | Deadline by which the merchant must respond to this dispute. (Epoch timestamp in seconds, Timezone: UTC +0:00)  |
| `createdAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))             | A timestamp indicating when the dispute was created. (Epoch timestamp in seconds, Timezone: UTC +0:00)     |
| `openingNote`            | String                | Text blob from the customer describing why the dispute was opened or the reason for the complaint. While dispute category codes are helpful at informing what a merchant should present, it doesn’t provide reasoning behind the customer’s complaint.  In some cases, this can help merchants troubleshoot the dispute directly with their customers.      |
| `openingNoteAttachments` | FileId                | Attachments to supplement the `openingNote`. If the customer provided photos or screenshots as part of their description on why the dispute was  |
| `updatedAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing)) (optional)  | Timestamp when the dispute was updated. (Epoch timestamp in seconds, Timezone: UTC +0:00)    |
| `closingReason`         | String                | A reason indicating how the final decision on the dispute was reached. Recommended possible values are listed in [Closing Reasons](#closing-reasons) below.|
| `closingNote`            | String (optional)     | A text blob describing in detail how the final decision on the dispute was reached. This supplements the `closingReason`.  |
| `merchantOrderId`        | String                | The identifier for the transaction on the merchant side.      |
| `transactionDate`        | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))            | The timestamp of the order created by the customer. (Epoch timestamp in seconds, Timezone: UTC +0:00)    |
| `settlementAmount`       | String                | The settlementAmount for audit usage.   |
| `meta`                   | MetaObject (Optional) | The extra information for merchants to match payment.      |

#### Meta Object

| Field name         | Data type         | Description                                                              |
|--------------------|-------------------|----|
| `transactionAmount`  | String            | The transaction amount for the order.                                    |
| `network`           | String (Optional) | The payment network used by the customer.  (Typically, Visa or MasterCard)    |
| `networkReferenceId` | String(Optional)  | The identifier for the payment. (For in-store payments, the field exists) |
| `orderType`          | String            | The type of the order, should be `ONLINE` or `INSTORE`.                       |

#### Dispute Object Example
| Field name             | Data type   | Example    |
| ---------------------- |------------- | ------------------ |
| `id`      | String      | dp_N64jYg4RC4ZBUsXjLzE3W5   |
| `order`    | String    | 123456789   |
| `amount`      | String       | 48.46     |
| `currency`   | String    | USD       |
| `reason `    | String       | fraudulent  |
| `status`        | String        |   won      |
| `open`       | Boolean     | false|
| `responseDueBy`         | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))| 1691884800                                                                     |
| `createdAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing)) | 1691884800                                                                     |
| `openingNote`            | String                                                                  | Customer has no knowledge of the Payment.                                      |
| `openingNoteAttachments` | FileId      | [“fi_48vmw3sXdVqvtJGXbgKbAZ”]       |
| `updatedAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing)) (optional) | 1691884800    |
| `closingReason`          | String |merchant_accepted    |
| `closingNote`            | String (optional)  | Merchant accepted the dispute.  |
| `merchantOrderId`       | String  | merchantorderid12345       |
| `transactionDate` | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))  | 1691884800      |
| `settlementAmount`       | String    | 48.46<br>           |
| `meta`                   | MetaObject (Optional)    | {  <br> <space> "transactionAmount": "48.46",<br> "orderType":"ONLINE" <br> } |

### Dispute Status

Cash App Afterpay supports the following dispute status: 

<!-- theme: info-->
> **Note**
>
> We don’t support `partially_won` status in the first version, but have plans to support it in the future.

| Status         | Description   |
|----------------|-----------------------------|
| `needs_response` | Cash App Afterpay has created the dispute and notified the merchant, but the merchant has not taken action.       |
| `under_review`   | Merchant has submitted evidence to Cash App Afterpay, and it is currently under review.         |
| `partially_won`  | If the final dispute settlement was less than the original dispute amount, then this indicates the merchant partially won the dispute. Note that, this is a terminal state.  |
| `won`            | The evidence submitted is accepted by Cash App Afterpay and the dispute is won by the merchant. Note that, this is a terminal state.                                                  |
| `lost`           | The evidence submitted is rejected by Cash App Afterpay and the dispute is lost by the merchant. Note that, this is a terminal state.                                                 |
|`merchant_refunded`|Merchant has issued a refund.  If the refund is equal to or greater than the dispute amount, then this is a terminal state.  |
|`merchant_voided`|Merchant has canceled all or a portion of the order.  If the voided amount is equal to or greater than the dispute amount, then this is a terminal state.|

## Dispute Windows

Cash App Afterpay updates the dispute status and triggers dispute notifications according to the dispute window time frames. The following is the time frame (in calendar days) to exercise and defend a chargeback: 

| Summary  | Description    |          |
|----------|----------------|----------|
| Dispute Open Window  | The maximum window of time (from the transaction date) for a dispute to be opened, beyond which a customer can no longer initiate a dispute. | 120 days |
| Merchant’s Evidence Submission Window | The allowed time between the merchant being notified of a dispute and the final time for evidence submission. | 13 days  |
| Cash App Afterpay’s Decision Window | The allowed time from the moment of evidence submission to Cash App Afterpay’s final decision.  | 30 days  |
 
### Dispute Reasons

There will always be a dispute reason when a dispute is triggered. The following are the dispute reasons that the Disputes API will currently respond to and support:

> Cash App Afterpay's dispute reasons are limited to `product_not_received` right now, and we have planned updates to this in the future. Cash App Pay's dispute system is fully implemented and incorporates all reasons, including card network chargebacks.

| Merchant-facing Dispute Reason | Active |Description          |
|--------------------------------|--|--------------------------------|
| `product_not_received`           |Cash App Afterpay / Cash App Pay |The customer claims they did not receive the products or services purchased.    |
| `product_unacceptable`           | Cash App Afterpay (Q4 release) / Cash App pay|The product or service was received, but was defective, damaged, or not as described.     |
| `credit_not_processed`           | Cash App Afterpay (Q4 release) / Cash App pay| The customer claims that the purchased product was returned or the transaction was otherwise canceled, but that the merchant has not yet provided a refund or credit. |
|`order_canceled`|Cash App pay |The merchandise/service was cancelled.|
| `duplicate`                    |Cash App pay  |The customer claims that they were charged multiple times for the same product or service.   |
|`incorrect_amount`| Cash App pay|The payment amount differs from the agreed amount.|
|`paid_by_other_means`| Cash App pay|The customer paid by other payment methods.|
| `fraudulent`                    | Cash App pay|The customer claims that they didn’t authorize the payment.       |
| `fraudulent_merchant`                    | Cash App pay| The customer has no knowledge of the payment and the liability has shifted to the merchant due to collusion, fraud monitoring program thresholds, or any other reason.       |



## Closing Reasons

A closing reason indicating how the final decision on the dispute was reached is displayed to the merchant. The following are the closing reasons and their descriptions:

| Merchant-facing Closing Reason| Description |
|--|--|
|`merchant_accepted`|Merchant accepted the dispute.|
|`evidence_accepted`|Merchant submitted evidence which was accepted, The dispute was closed in the merchant’s favor.|
|`evidence_rejected` |Merchant submitted the evidence but it was rejected and the dispute was closed in the customer’s favor.|
|`deadline_expired`|Merchant failed to submit evidence for the dispute and the submission window timed out. Dispute was closed in the customer's favor.|
|`customer_cancelled`| Customer withdrew the dispute and therefore it was closed in the merchant’s favor.|

## Retrieving disputes

### List Disputes - Endpoint
List disputes within a date range based on certain criteria. This endpoint can be used for debugging or synchronizing the disputes from Cash App Afterpay if/when you are unable to use the webhook method.

```
GET https://{afterpay_global_url}/v2/disputes
```

#### Connection Timeouts
| Timeout | Time (seconds) |
|------------|-----------|
| `OPEN`       | 10    | 
| `Read `       | 20    | 

#### Request Headers

| Header | Type | Example        |
|------------|-----------|---------------------|
| `User-Agent`| String | `MyCashAppAfterpayModule/1.0.0 (E-Commerce Platform Name/1.0.0; PHP/7.0.0; Merchant/60032000) https://merchant.example.com` |

| Header | Type | Default Value        |
|------------|-----------|------------------|
| `Accept`   | String    | application/json |

#### Request Parameters

| Field name   | Data type | Description   |
|--------------|-----------|-----------------------------------|
| `order`       | Integer   | Payment or Order token using which you can filter the list.  |
| `merchant`     | String    | Merchant token using which you can filter the list.   |
| `status`       | String    | Dispute status using which you can filter the list.         |
| `openedAfter`  | Timestamp | Filter disputes that were created on or after this timestamp (inclusive).  |
| `openedBefore` | Timestamp | Filter disputes that were created on or before this timestamp (inclusive). |
| `offset`       | Integer   | Offset for the search results. Example: Offset = 0, limit = 10 means that we will display the first ten disputes. Offset = 10, limit = 10 means that we will display the disputes numbered 10-20 in the search results.    |
| `limit`        | Integer   | The maximum number of records that you want returned from this request.   |

#### Response
| Field name | Data type            | Description  |
| ---------- | -------------------- | ------------ |
| `data`       | Array (DisputeObject) | An array of dispute objects that match the filter criteria in the request. |
| `offset`     | Integer   | Offset for the search results. Example: Offset = 0, limit = 10 means that we will display the first ten disputes. Offset = 10, limit = 10 means that we will display the disputes numbered 10-20 in the search results.   |
| `limit`      | Integer   | The maximum number of records that you want returned from this request.     |
| `total`      | Integer   | Total dispute records in the search condition.  |


#### Response Example

| Field name   | Data type             | Example |
| ------------ | --------------------- | ------- |
| `data`       | Array (DisputeObject) | See [Data example code](#data-example-code) below. |
| `offset`     | Integer               | 0   |
| `limit`      | Integer               | 1   |
| `total`      | Integer               | 1   |


#### Data example code

```json
[
  {
    "id": "dp_N64jYg4RC4ZBUsXjLzE3W5",
    "order": "12312312312",
    "amount": "48.46",
    "currency": "USD",
    "status": "won",
    "reason": "fraudulent",
    "open": false,
    "responseDueBy": -1,
    "openingNote": "Cash dispute: Customer has no knowledge of the Payment.",
    "openingNoteAttachments": [],
    "merchantOrderId": "12312312312",
    "transactionDate": 1690836227,
    "createdAt": 1691884800,
    "updatedAt": 1692067909,
    "meta": {
              "transactionAmount": "48.46",
              "orderType": "ONLINE"
            }
  }
]
```
