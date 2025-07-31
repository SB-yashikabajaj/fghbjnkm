---
stoplight-id: 6ti8uave6iwxb
---

# Migrate from Afterpay to Cash App Afterpay

<!-- theme: warning -->
> **Important:** If your app uses an explicit allowlist of Afterpay domains, you *must* add `api.cash.app` and `cash.app` to the allowlist. 
>

If you are a merchant with a direct integration with Afterpay, the information in the [API Integration](#api-integration) section of this page applies to you. 

If you use a platform to host Afterpay, for example Shopify, see the [Platforms](#platforms) section.

## API Integration

We anticipate no changes to the APIs and therefore no changes are needed to your back-end and minimal changes needed for your front-end systems. 

In the API section of this guide, you may notice that the word Afterpay has been replaced by Cash App Afterpay. Likewise we have removed references to Canada, Australia, and New Zealand. Afterpay is called Clearpay in the UK so we have also removed all these references. We had to do this work because Cash App Afterpay is only available to US merchants.

## Afterpay Messaging

We currently support two messaging products, both of which work with Cash App Afterpay.

[On-Site Messaging](../AFTERPAY-MESSAGING/Getting-Started-with-Afterpay-On-Site-Messaging.md) is our current messaging product. Our previous product is messaging from the [JavaScript Library](../AFTERPAY-MESSAGING/JavaScript-Library.md).

**On-Site Messaging**

If you use On-Site Messaging, wait for the automatic update process to occur. Monitor your email for advance notice of this automatic update.

If you use elements of Afterpay Messaging, then see the [Getting Started with Afterpay On-Site Messaging](../AFTERPAY-MESSAGING/Getting-Started-with-Afterpay-On-Site-Messaging.md) page for more information.

**JavaScript Library**

If you use the JavaScript library for your messaging, wait for the automatic update process to occur. Monitor your email for advance notice of this automatic update.

<!-- theme: info -->
> **Note**
>
> If you are using a specific version of the script, please update to version `1.x.js`

## Differences

These are the significant differences between Afterpay and Cash App Afterpay.

* Cash App Afterpay is currently only available in the USA. Unlike Afterpay, it is not available in Australia, Canada, New Zealand. Cash App Afterpay is not available in the United Kingdom where Afterpay is called Clearpay.

* Cash App Afterpay operates in US dollars only, although [Cross Border Trade](../WELCOME/caa-cross-border-trade.md) is available

## Visual Changes

The most obvious and important changes to the Cash App Afterpay integration are visual.

Customers will see *Cash App Afterpay* on your product and payment pages, instead of *Afterpay*.

See the [Cash App Afterpay Merchant guidelines](https://www.figma.com/deck/yC8BbsBfhxkSnxrw8VtYna/Cash-App-Afterpay-%E2%80%93-Merch[…]kF1jqQt-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1) online presentation for much more information on how to display and present Cash App Afterpay. 

## Brand Assets

See the [Brand Assets](../MARKETING/Brand-Assets.md) page in this guide for new assets.

Any custom messaging updates must be reviewed by your Account Manager.

## FAQs

If you have a technical question on the migration, see our [FAQs for the Migration](faq-migration.md) page.

# Platforms

This section is for merchants who use a platform for their integration. Find your platform in the list below for information on migration from Afterpay to Cash App Afterpay.

* [Adobe Commerce (Magento 2)](adobe-commerce-migration.md)

* [Adyen](adyen-migration.md)

* [Big Commerce](big-commerce-migration.md)

* [Ecwid](ecwid-migration.md)

* [PrestaShop](prestashop-migration.md)

* [Salesforce Commerce Cloud](salesforce-cc-migration.md)

* [Shopify](shopify-migration.md)

* [Stripe](stripe-migration.md)

* [Wix](wix-migration.md)

* [WooCommerce](woocommerce-migration.md)

<!-- theme: info -->
> **Note**
>
> There can be reasons why your platform is not listed above. For example, various Australian and New Zealand platforms cannot host Cash App Afterpay because these platforms are not available in the United States. Other platforms are not be available for Cash App Afterpay yet, but will be in the future. See the [Support page](../FAQS-AND-SUPPORT/caa-support.md) if you want to contact us about a specific platform.