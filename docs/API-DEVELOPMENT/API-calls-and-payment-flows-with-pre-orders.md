---
stoplight-id: ux9an0203cpvg
---


# API Calls and Payment Flows with Pre-Orders

The **Afterpay v2 API**  offers merchants a choice of two different payment flows. The v1 API uses the Direct Capture flow.

Normally merchants can choose one of three main payment flows in their integration with Cash App Afterpay:

1. **Immediate Capture:** Funds are captured at or near the time of checkout.
2. **Deferred Capture:** Funds are captured at or near the time of fulfillment which must be within 13 days of the checkout.
3. **Pre-orders:** Funds are captured at or near the time of fulfillment.  Fulfillment is not known to be within 13 days of the checkout.


> Customers' repayment commences once the order has been confirmed. 
> 
> - For Immediate Capture repayment commences on Capture.
> - For Deferred Payment repayment commences on Auth. 

## 1. Direct Capture (Immediate Payment Flow)

This flow allows merchants to capture the full payment amount at the time of order.  
Read more about this payment flow in our [API v2 docs](../ONLINE-API/Immediate-Payment-Flow.md)


![Direct Capture Payment Flow](../../assets/images/Direct-Capture-Payment-Flow.png)


![Immediate Capture Timeline](../../assets/images/ImmediateCaptureTimeline.png)


> All platforms support the Direct Capture payment flow

## 2. Auth and Capture (Deferred Payment Flow)

This flow allows merchants to capture incremental amounts as items are shipped. Afterpay will settle funds when payments are captured by the merchant. If it is later determined that one or more shipments cannot be fulfilled, the un-captured remainder of the payment auth can be voided. This is similar to the Auth and Capture process of an order paid with a credit card.  
Read about this payment flow in our [API v2 docs](../ONLINE-API/Deferred-Payment-Flow.md).


![Auth and Capture Payment Flow](../../assets/images/Auth-and-Capture-Payment-Flow.png)

Merchants may choose to fulfill and capture the full amount as shown immediately below in the Deferred Full Capture Timeline, or capture each partial shipment as items are fulfilled, as shown in the Deferred Partial Capture Timeline.


![Deferred Full Capture Timeline](../../assets/images/DeferredFullCaptureTimeline.png)


![Deferred Partial Capture Timeline](../../assets/images/DeferredPartialCaptureTimeline.png)



> **Supported Platforms for Auth and Capture Payment Flow**
> 
> - Direct API (v2 API)
> - [Salesforce Commerce Cloud](../PLATFORMS/Salesforce-Commerce-Cloud/SFCC-intro.md)
> - [Magento 2](../PLATFORMS/Adobe-Commerce-Magento/Adobe-Commerce-Magento.md)

## 3. Pre-orders

This flow allows for merchants to specify a portion of an order to be fulfilled past the default maximum shipping duration of 13 days. At checkout, the merchant specifies the amount to be included in the initial order, which is the order which will be fulfilled within 13 days. For the initial order, the customer's payment plan will start immediately. 

Then, for items which may be fulfilled past the default maximum shipping duration of 13 days (and up to a maximum duration of 6 months), the Merchant will process a subsequent order as items are fulfilled.  
Read about this payment flow in our [v2 API docs](pre-orders-payment-flow.md).



![Pre-Orders Swimlane](../../assets/images/PreOrdersSwimlane.png)

Merchants will process an initial order (if there are items which are known will ship in 13 days) with the below timeline.  Subsequent orders will have a different timeline, and the Merchant will capture as items are fulfilled.


![Pre-Orders Initial Order Timeline](../../assets/images/PreOrdersInitialOrderTimeline.png)

Below is the subsequent timeline, for items on the order which will not ship within 13 days of the checkout.


![PreOrdersSubsequentOrderTimeline](../../assets/images/PreOrdersSubsequentOrderTimeline.png)

> Supported Platforms for Pre-orders Payment Flow
> - Direct API (v2 API)
> The quickest way to start testing the API is to use our [Postman request collection](Postman-Collection.md)

## Pre-orders Documentation Contents

- [Pre-orders Overview](Pre-Orders.md) 
- [Pre-orders Payment Flow](pre-orders-payment-flow.md) 
- [Upgrading to Pre-orders](Upgrading-to-Pre-orders.md)


