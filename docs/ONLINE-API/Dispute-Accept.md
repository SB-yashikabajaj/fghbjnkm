---
stoplight-id: 8zpbsq1i86x57
---

# Accepting or Contesting Disputes

When a dispute is created, Cash App Afterpay encourages the merchant to contact their customer. The merchant can then decide to do one of the following:

* [Accept the dispute](#accepting-a-dispute)

* [Collect and submit evidence to help resolve the dispute](#evidence-submission-pipeline)

The merchant can either use the Business Hub or the following APIs to accept or contest disputes. 

<!-- theme: info-->
> **Note**
>
> Currently, Cash App Afterpay only supports one round of evidence submission, we have plans to support multiple rounds in the future.

## Accepting a dispute

Merchants can call the following endpoint to accept a dispute case. This endpoint only works if the dispute is in a non-terminal state, that is, the dispute status is not `won` or `lost`. 

<!-- theme: info-->
> **Note**
>
> Calling the API changes the dispute status to `lost`.

## Accept Dispute - Endpoint
```
POST https://{afterpay_global_url}/v2/disputes/{dispute_id}/accept
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

### Request Parameters
| Field name | Data type | Description         |
|------------|-----------|---------------------|
| `dispute_id`         | String    | (Required) Dispute identifier. |

### Response

| Field name | Data type     | Description                 |
|------------|---------------|-----------------------------|
| `dispute`    | DisputeObject | The updated dispute object. |

### Dispute Object Example

| Field name             | Data type             | Example                                                                     |
|------------------------|-----------------------|-----------------------------------------------------------------------------|
| `id`                     | String                | dp_ivpMnZkDhLykyXeoSr5WF4                                                   |
| `order`                  | String                | 123456789                                                                   |
| `amount`                 | String                | 48.46                                                                       |
| `currency`               | String                | USD                                                                         |
| `reason`                 | String                | paid_by_other_means                                                         |
| `status`                 | String                | lost                                                                        |
| `open`                   | Boolean               | false                                                                       |
| `responseDueBy`          | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))          | 1691884800                                                                  |
| `createdAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))             | 1691884800                                                                  |
| `openingNote`            | String                | Customer has no knowledge of the Payment.                                   |
| `openingNoteAttachments` | FileId                | [“fi_48vmw3sXdVqvtJGXbgKbAZ”]                                               |
| `updatedAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing)) (optional)  | 1691884800                                                                  |
| `closingReason`          | String                | merchant_accepted                                                           |
| `closingNote`            | String (optional)     | Merchant accepted the dispute                                              |
| `merchantOrderId`        | String                | merchantorderid12345                                                        |
| `transactionDate`        | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))             | 1691884800                                                                  |
| `settlementAmount`      | String                | 48.46                                                                       |
| `meta`                   | MetaObject (Optional) | {        <br> "transactionAmount": "48.46",         <br>"orderType": "ONLINE"    <br> } |

## Evidence Submission Pipeline

If a merchant does not want to accept a dispute, Cash App Afterpay provides a way to submit evidence to contest the dispute through the Business Hub or the API. 

Cash App Afterpay provides a file upload API for merchants to upload the evidence needed for contesting the dispute. The tokens returned from the file upload API can then be specified as part of the request/response for the API endpoints of the dispute. For file upload API details, see [Uploading Files](Disputes-Retrieve.md#uploading-files).

## Respond to the dispute

The *Respond to the dispute* (e.g., submit evidence) endpoint enables the merchant to submit evidence for the dispute. This is only allowed if the dispute is the state `needs_response`.

This means merchants only have one opportunity to submit evidence. Once a 200 response is received, this information cannot be updated or changed.

### Endpoint
```
POST https://{afterpay_global_url}/v2/disputes/{dispute_id}
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
|`Content-Type` | String | application/json |

### Request Parameters

| Field name | Data type       | Description                              |
|------------|-----------------|------------------------------------------|
| `id`        | String          | A unique ID given to a dispute.                      |
| `evidence`   | Evidence object | See [evidence fields](#evidence-fields). Note that there should be at least one valid field.|

### Response

| Field name | Data type     | Description                |
|------------|---------------|----------------------------|
| `dispute`    | DisputeObject | The updated dispute object. |

## Evidence Fields

| Field                    | Data Type         | Limit         | Description          |
|--------------------------|-------------------|-------------|-----------|
| `productDescription`      | String (Optional) | Length: 1-5000 characters                          | A description of the product or service and any relevant details on how this was presented to the customer at the time of purchase.  |
| `refundPolicy`             | String (Optional) | Valid File Token Generated by [Upload File](Disputes-Retrieve.md#uploading-files) Endpoint | Token of the file upload. The merchant’s refund policy, as shown or provided to the customer.     |
| `refundPolicyDisclosure`   | String (Optional) | Length: 1-5000 characters                          | An explanation of how and when the customer was shown or provided with the merchant’s refund policy prior to purchase.	      |
| `refundRefusalExplanation` | String (Optional) | Length: 1-5000 characters                          | The merchant’s explanation for why the customer is not entitled to a refund.	      |
| `shippingDocumentation`    | String (Optional) | Valid File Token Generated by [Upload File](Disputes-Retrieve.md#uploading-files) Endpoint | Token of the file upload. A shipping label or receipt for the disputed payment.  |
| `shippingAddress`          | String (Optional) | Length: 1-5000 characters                          | The address to which a physical product was shipped.    |
| `shippingDate`             | String (Optional) | Length: 1-5000 characters                          | In cases of physical products, the date that a physical product began its route to the shipping address in a clear human-readable format. This date should be prior to the date of the dispute.	  |
| `shippingCarrier`          | String (Optional) | Length: 1-5000 characters                          | In cases of physical products, the delivery service that shipped a physical product, such as Fedex, UPS, USPS, etc. If multiple carriers were used for this purchase, separate them with commas.	 |
| `shippingTrackingNumber`   | String (Optional) | Length: 1-5000 characters                          | The tracking number for a physical product, obtained from the delivery service.   |
| `uncategorizedFile`        | String (Optional) | Valid File Token Generated by [Upload File](Disputes-Retrieve.md#uploading-files) Endpoint| Token of the file upload. Additional file that’s not in any of the categories above.         |
| `uncategorizedText`       | String (Optional) | Length: 1-5000 characters                          | Any additional text deemed relevant by the merchant.      |

### Dispute Object Example

| Field name             | Data type             | Example                                                                     |
|------------------------|-----------------------|-----------------------------------------------------------------------------|
| `id`                     | String                | dp_ivpMnZkDhLykyXeoSr5WF4                                                   |
| `order`                  | String                | 123456789                                                                   |
| `amount`                 | String                | 48.46                                                                       |
| `currency`               | String                | USD                                                                         |
| `reason`                 | String                | paid_by_other_means                                                         |
| `status`                 | String                | under_review                                                                        |
| `open`                   | Boolean               | true                                                                       |
| `responseDueBy`          | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))          | 1691884800                                                                  |
| `createdAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))             | 1691884800                                                                  |
| `openingNote`            | String                | Customer has no knowledge of the Payment                                   |
| `openingNoteAttachments` | FileId                | [“fi_48vmw3sXdVqvtJGXbgKbAZ”]                                               |
| `updatedAt`              | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing)) (optional)  | 1691884800                                                                  |
| `closingReason`          | String                | merchant_accepted                                                           |
| `closingNote`            | String (optional)     | Merchant accepted the dispute                                              |
| `merchantOrderId`        | String                | merchantorderid12345                                                        |
| `transactionDate`        | [Timestamp](https://en.wikipedia.org/wiki/Epoch_(computing))             | 1691884800                                                                  |
| `settlementAmount`      | String                | 48.46                                                                       |
| `meta`                   | MetaObject (Optional) | {        <br> "transactionAmount": "48.46",         <br>"orderType": "ONLINE"    <br> } |