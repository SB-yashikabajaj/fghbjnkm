---
stoplight-id: o3hqditjtewod
---

# Shopify Migration

If you'realready using the **Afterpay US (New)** payment app, no action is required. The new Cash App Afterpay branding will be updated automatically. Here's how it should appear:

<img src="./../../assets/images/Shopify-Cash-Afterpay-updated-method.png" style="max-width: 500px;">

If you haven't migrated from the **Afterpay (New)** payment app to **Afterpay US (New)**, see [Migrate to the Afterpay US App](#migrate-to-the-afterpay-us-app) below.

<!-- theme: info -->

> While the Shopify App Store listing and app logo will reflect the new Cash App Afterpay brand, the payment app itself will continue to be called **Afterpay US**. If you see Afterpay US (New) under your additional payment methods, you're all set.

## Afterpay US Messaging

Messaging automatically works if you use the Afterpay On-Site Messaging app or the liquid code snippet from the Afterpay technical guide. No work is needed, as the messaging is automatically enabled.

Messaging uses settings from Afterpay Messaging. It automatically displays the correct branding per region.

## Brand Assets

There are new Cash App Afterpay brand assets to use at checkout and across your site. See the [Brand Assets](../MARKETING/Brand-Assets.md) page in this guide for these new assets.

The table below has examples of the changes:

|         | Afterpay                                                                                | Cash App Afterpay                                                                               |
| ------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Logos   | <img src="../../assets/images/ap-logo-resized.png" style="all: unset; width: 150px;" /> | <img src="../../assets/images/caap-white-logo-resized.png" style="all: unset; width: 150px;" /> |
| Buttons | <img src="../../assets/images/ap-button.png" style="all: unset; width: 200px;" />       | <img src="../../assets/images/caap-button.png" style="all: unset; width: 200px;" />             |

Any custom messaging updates must be reviewed by your Account Manager.

### Cash App Afterpay Messaging

Messaging automatically works if you use the Afterpay On-Site Messaging app, or the liquid code snippet from the Afterpay technical guide. No migration work is needed as the messaging is automatically enabled. Monitor your email for advance notice of this automatic update. The messaging uses settings from Afterpay Messaging and automatically displays the correct branding per region.

See the table below for an example of the changes:

| Afterpay                                                                          | Cash App Afterpay                                                                   |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| <img src="../../assets/images/ap-mess-2.png" style="all: unset; width: 250px;" /> | <img src="../../assets/images/caap-mess-1.png" style="all: unset; width: 250px;" /> |

The automatic Messaging update includes changes to _learn more_/lightbox asset if you use that.

If you use elements of Afterpay Messaging but not the standard Onsite Messaging Widget, then update the Afterpay elements with new Cash App Afterpay elements. See the [Brand Assets](#brand-assets) section above.

Any custom messaging updates must be reviewed by your Account Manager.

## Migrate to the Afterpay US app

https://player.vimeo.com/video/1051911198?badge=0&controls=0&autopause=0&player_id=0&app_id=58479

If you haven't migrated to the Afterpay US app yet, follow these two steps:

1. Install the **Afterpay US** payment app.
2. Deactivate the **Afterpay** payment app you'd previously been using.

<!-- theme: info-->
> **Note**
>
> Before you start, make sure you meet the requirements for the migration, see [Requirements](#requirements) at the bottom of the page.

### Install the Afterpay US App

<!-- theme: none -->

> **Note:** For this migration, you don't need your merchant credentials to configure Afterpay US.

1. Click [here](https://accounts.shopify.com/store-login?redirect=settings%2Fpayments/alternative-providers/84934657) to download the Afterpay US payment app.
2. When the **Install app** screen appears, click **Install**. <img src="./../../assets/images/Shopify-Cash-AfterpayUS-install.png" style="max-width: 600px;">
3. Once installed, Afterpay US (New) appears in your list of apps, ready to activate. Click **Activate**.

Once Afterpay US (New) appears with the green 'Active' sign next to it, your customers can immediately use Afterpay US to make payments. You don't need to do any further work to configure the app.

<img src="./../../assets/images/Shopify-Cash-AfterpayUS-activated.png" style="max-width: 600px;">

### Deactivate the previous Afterpay app

The final task is to deactivate the **Afterpay (New)** payment app in Shopify. Despite its name, this is the app you'd previously been using.

1. Go to **Shopify Admin**.

2. Go to **Settings**, then select **Payments**.

3. Under Additional payment methods, select **Afterpay (New)**. Make sure _not_ to select **Afterpay US (New)**, which you just installed. <img src="./../../assets/images/Shopify-Cash-AfterpayUS-delete-method.png" style="max-width: 500px;">

4. On the Afterpay (New) screen, click **Deactivate**, then click **Deactivate** again to confirm your choice.

5. Return to your list of additional payment methods. Make sure that **Afterpay US (New)** is listed as an active payment method; **Afterpay (New)** shouldn't be on the list. <img src="./../../assets/images/Shopify-Cash-Afterpay-updated-method.png" style="max-width: 500px;">

<!-- theme: info -->

> **Note:** In case you need to issue a refund, capture payments, or void payments that were previously made with Afterpay, we recommend that you keep the **Afterpay (New)** payment app in your system. After you deactivate the app, don't uninstall it.

## New payment method name

The Afterpay US payment app uses a new payment method name: **Afterpay US (New)**.

If your store has post-order processes that rely on the payment method name—like Shopify Flows or custom reporting—update any references from **Afterpay (New)** to **Afterpay US (New)**.

This only applies to merchants with custom backend systems that use the payment method name to trigger workflows.

## FAQs

If you have a technical question on the migration, see our [FAQs for the Migration](faq-migration.md) page or below for Shopify-specific FAQs.

#### Refunds - I’m having trouble completing a refund, what should I do?

If the payment was taken on the Afterpay payment gateway and you have uninstalled the app, you must reinstall the app. Follow [these instructions](../PLATFORMS/Shopify/Shopify-Getting-Started.md) to install the Afterpay app. You will not need to configure your Afterpay app again.

Please do not activate the Afterpay app (leave it deactivated).

#### Cross Border Trade (CBT) - are all customers available to use Cross Border Trade on my Shopify store?

Cross Border Trade is available to Afterpay customers. It is not yet available to Cash App customers new to Afterpay.

Before the customer checks out, they see the appropriate brand for your shop's region. When the customer checks out, they see the appropriate brand based on the region associated with their Afterpay account.

For example, if your store is set in US, and your customer is based in the Canada, they will see the following brands:

- On your Shopify store: Cash App Afterpay

- During Afterpay checkout: Afterpay

#### Help! I accidentally uninstalled the Afterpay (New) app.

If you uninstalled the Afterpay (New) payment app when migrating to the Afterpay US app, you must reinstall Afterpay (New) to manage outstanding Afterpay orders placed before the migration.

Follow these steps:

1. Use this link to log in to your Shopify account and reinstall the app: [Reinstall Afterpay (New) App](https://accounts.shopify.com/store-login?redirect=settings%2Fpayments/alternative-providers/1057655)

2. Once you reinstall the app, don't activate it. Reinstalling without activating lets you manage transactions that occurred before you migrated.

3. Now that the app is reinstalled, you can issue refunds for pre-migration Afterpay orders, capture payments for pending transactions, and void payments as needed.

<!-- theme: info -->

> **Keep the app installed!** To avoid any issues with managing pre-migration Afterpay orders, we recommend keeping the Afterpay (New) app installed on your Shopify store.

#### Afterpay appears twice at checkout

<img src="./../../assets/images/Shopify-Cash-Afterpay-appears-twice.png" style="max-width: 500px;">

If Afterpay appears twice at checkout (as shown above), make sure to deactivate the **Afterpay (New)** app. Only the **Afterpay US (New)** app should be active. Follow the instructions to [deactivate the previous Afterpay app](#deactivate-the-previous-afterpay-app).

#### Update the Afterpay Banner

If you use the banner as part of your messaging, follow the instructions below to update it: 

1. On Shopify, open the code editor to edit the theme files.

2. In theme.liquid, delete {% section 'afterpay-banner' %}.

3. Delete the afterpay-banner.liquid file.

4. Follow the steps [here](../PLATFORMS/Shopify/Shopify-Add-an-Afterpay-Banner-to-Shopify.md) to add the Cash App Afterpay banner to your theme.

#### Requirements

To avoid issues installing the new Afterpay US payment app, check that you have Shopify installed and working.

Make sure that your company or organization meets the following requirements:

Your business address is in one of the the following:

- Australia
- Canada
- Hong Kong SAR
- New Zealand
- United Kingdom
- United States

You must ship to the United States.

You must accept the currency USD (United States Dollars).