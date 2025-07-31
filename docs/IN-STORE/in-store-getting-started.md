---
stoplight-id: yade9fp9g59ur
internal: true
---

# In-Store Operations

## How to apply for Cash App Afterpay In-Store

As a merchant, you can apply for **Cash App Afterpay In-Store** by following the instructions [here](https://get.afterpay.com/app/). Our commercial and compliance teams will review your application and complete their due diligence. Once this process is completed, you receive an email. This email has instructions to complete your technical onboarding and also to enable card terminals in your store.

## How In-Store works

Cash App Afterpay Card is a contactless digital card stored in a customer's digital wallet on their phone. The customer adds their Cash App Afterpay Card to their digital wallet via a one-time setup prompted in their Afterpay app.

To make an In-Store purchase using Cash App Afterpay Card, the customer can either initiate the transaction via the Cash App Afterpay app or launch the card directly from their digital wallet. The customer taps their Cash App Afterpay Card on your card terminal to pay and finalize the transaction.

You can find further details on the customer experience in [Download and use the Afterpay app](use-app.md) and on our Customer In-Store Information pages [here](https://www.afterpay.com/en-US/irl?\_branch_match_id=1103638541018819297\&utm_source=Afterpay\&utm_campaign=us-mobileapppage-instoremodule\&utm_medium=organic-banner&\_branch_referrer=H4sIAAAAAAAAA8soKSkottLXT0wrSS0qSKwsLdZLLCjQy8nMy9Y38qn0NvBNjAzITAIAJMTkJScAAAA%3D)

## How to set up your store with Afterpay

When you attempt a Cash App Afterpay card transaction on a card terminal, we receive certain details in our system that identify that specific terminal. We configure these details against your merchant account in order to connect your terminal(s) to your Cash App Afterpay Merchant Account.

The details we use to enable the terminals are:

- Acquirer Merchant Scheme Name
- Acquirer Merchant ID

Sometimes the data that is received by our system may vary depending on the acquirer/terminal provider. For example, sometimes what is technically the **Terminal ID** will appear in our **Merchant ID** field. This can also be true of the merchant scheme name and what appears in this field in our system might not match up exactly with what your acquirer/terminal provider has provided for your terminal.

## How can I request support after my store/terminal is enabled?

You can request support from Afterpay's Merchant Services team via this [form](https://afterpay.formstack.com/forms/global_merchant_technical_support). Make sure you select the **Afterpay/Clearpay - In-store Support** option. The team can support with declines, refunds, adding/removing terminals/stores.

## Square Card Terminals

As Cash App Afterpay is a part of Square, we have simplified our integration for merchants who use Square terminals only. If you have Square terminals in your store, you can enable Cash App Afterpay In-Store in your Square Seller Dashboard by going to your **Account Settings** under **Business** > **Payment Settings**.

<!-- theme: info -->

> **Note**
>
> This enablement creates the same configurations that we create manually for non-Square terminals but the entire process is automated.

## Acquirer and Terminal Provider Resources

Many acquirers and terminal providers have a section in their technical guides on how to enable Cash App Afterpay. Often these technical guides specify the exact fields within their own systems that contain information useful to Cash App Afterpay. This especially applies to aquirer information that you must send to Afterpay, so we can set up your in-store operations.

## Refunds

### Merchant/Customer Experience

From a merchant perspective, refunds are handled like any other digital card refund. Customers tap their Cash App Afterpay cards on the card terminal in order to process the refund.

Refunds can be handled In-Store for purchases made both In-Store and online.

The complete steps for the customer are as follows.

1. The customer should locate the order they want to refund in the **Orders** tab of the Afterpay customer app and click the 3 dots in the top right corner.
2. From the options presented, they should click **Returning an order**.
3. Click **Returning In-Store**
4. Click the **Return to Cash App Afterpay Card** button to launch the Cash App Afterpay Card.
5. The customer should then tap their Cash App Afterpay Card against the card terminal as they would for any other digital card return.

<!-- theme: info -->

> **Note**
>
> Refunds for purchases made In-Store must also be done In-Store. We do not currently support any method of refunds for **Customer Not Present** use cases. This means that In-Store refunds cannot be processed through the Business Hub, unlike online refunds.

### BORIS - Buy Online, Return In-Store

Afterpay matches refunds based on a customer's profile and their persistent Cash App Afterpay Card - whether your systems enable referenced refunds or not, customers are able to return online Cash App Afterpay purchases to Afterpay In-Store - we do all the math.

We'll cancel the outstanding installments and refund customers the installments they've already made. Sometimes Afterpay is unable to make a clear refund match to an order. In this case the customer is notified of a pending refund and guided through the process in-app to match the refund to the order.

### Verifying Last 4 Digits

If your POS receipts display the last four digits of the card information, then the Cash App Afterpay Card is represented by the last four digits of the Device Primary Account Number (DPAN).

A DPAN is a device-specific tokenized card number and is generated after a customer adds the Cash App Afterpay Card to their iOS or Android device. A customer can locate the last four digit of the DPAN on the wallet with the instructions below:

**Apple Pay**

Do the following:

1. Open the Wallet app.

2. Tap the Cash App Afterpay Card.

3. Tap the three dots in the top right hand corner. Device Account Number is located on this screen.

**Google Pay**

Do the following:

1. Open the Google Pay app.

2. Tap on the Cash App Afterpay Card, then scroll to Virtual Account Number.

## Settlements and Reconciliation

Settlement of funds from Cash App Afterpay Card transactions take place in the same way as all other card payments processed by your business, via your card payment processor or acquiring partner. The gross sales amount will settle the next day after the Cash App Afterpay Card transaction takes place. Three days after the Cash App Afterpay Card transaction Afterpay direct debits the fees from the gross amount.

You can download a detailed Reconciliation file that provides line item information on Cash App Afterpay Card payments that were captured by your acquirer daily. These files can be downloaded from the [Afterpay Business Hub](https://hub.afterpay.com/us).

Cash App Afterpay Card fees are calculated per purchase. The fees are debited from your nominated account in line with order settlement per day, as per the terms of your Merchant Agreement.

Cash App Afterpay Cards have a dedicated BIN (US - 427140), so this can be used to identify Cash App Afterpay Card transactions in any store's financial reporting.

## FAQs

**Q: Is my Cash App Afterpay customer account linked to my Cash App Afterpay merchant account?**

**A:** No, these are entirely separate and can use the same email as the primary email address. The two types of account are in no way linked.

**Q: Why did my dummy tap decline?**

**A:** The dummy tap is supposed to decline as we do not currently have your card terminal details configured on your merchant account.

**Q: Does Cash App Afterpay support Card Not Present transactions in store?**

**A:** No, we only support card present transactions as the implementation relies on customers physically tapping their card on the terminal. This is also true for refunds.

**Q: What types of card terminals support Cash App Afterpay In-Store?**

**A:** Any card terminal that supports Apple/Google payments can support Cash App Afterpay cards.

**Q: Does Cash App Afterpay support split tender transactions?**

**A:** Yes, as with other card payments, a customer can select to pay part of their transaction using their Cash App Afterpay card. This is supported for refunds in the same way.

## Additional Resources

- [Merchant Information](https://www.afterpay.com/en-US/for-retailers)

- [Customer Experience](https://www.afterpay.com/en-US/irl?\_branch_match_id=1103638541018819297\&utm_source=Afterpay\&utm_campaign=us-mobileapppage-instoremodule\&utm_medium=organic-banner&\_branch_referrer=H4sIAAAAAAAAA8soKSkottLXT0wrSS0qSKwsLdZLLCjQy8nMy9Y38qn0NvBNjAzITAIAJMTkJScAAAA%3D)

- [Merchant Onboarding Portal](https://get.afterpay.com/app/)

- [Log a Support Ticket](https://afterpay.formstack.com/forms/global_merchant_technical_support)
