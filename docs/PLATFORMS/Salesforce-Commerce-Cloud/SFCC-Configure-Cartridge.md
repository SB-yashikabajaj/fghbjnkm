---
stoplight-id: tydqj3301c7ry
---

# SFCC Configure the Cartridge

## Set the Cartridge Path

Before the Cash App Afterpay functionality can be available to your site, there is a cartridge task. Your task is to add the cartridge names to the cartridge path of the site’s settings. To do this, do the following: 	

1. Log into *Business Manager*.

2. Go to *Administration** > *Sites* > *Manage Sites* > *[yourSite]* > **Settings**.
    - If you are using SFRA (Salesforce Reference Architecture), enter: `int_afterpay_sfra:int_afterpay_core:app_storefront_base`. If you are using SFRA > 6.0.0 then you should use `int_afterpay_sfra_6 instead`.
    - If you are using SiteGenesis, enter: `int_afterpay_sg:int_afterpay_core` in front of SiteGenesis base cartridges.

3. Click **Apply**.

## Set SFCC (Demandware) Service

Go to *Administration* > *Operations* > *Services* > *Credentials* > and select the required service and enter the account details.

|||
|----------|---------------------------------------------------------------------|
| URL      | Sandbox https://global-api-sandbox.afterpay.com/v2/ <br>Production https://global-api.afterpay.com/v2/ |
| User     | Enter the Merchant ID provided by Cash App Afterpay.   |
| Password | Enter the Secret Key provided by Cash App Afterpay.    |

## Set Cash App Afterpay Custom Site Preferences

<!-- theme: info-->
> **Note**
>
> The SFCC cartridge and the Business Manager call Cash App Afterpay by the single word Afterpay. This doesn't affect any of the instructions or description below.

To set the custom site preferences, do the following:

1. In *Business Manager*, go to the *Merchant Tools* > *Site Preferences* > *Custom Preferences*. A custom site preference group with the ID `Integration_Afterpay` is available for you to use. Select it and edit the attributes according to your Cash App Afterpay account data and the data shown in the table below. 

<!-- theme: info-->
> **Note**
>
> Listed preferences are for the Afterpay cartridge v23.4.1 and above. If you are using any other versions see the integration guide in the documentation folder in the [repository](https://github.com/afterpay/afterpay-salesforce-commerce-cloud).

| Site Preference       | Description      | Default      |
|-----------------------|------------------|--------------|
| Enable Afterpay (`enableAfterpay`) | Sets whether all of the cartridge functionality is active and visible on your storefront. You can use this field to temporarily disable the payment method at checkout along with all customer-facing messaging throughout the site without uninstalling the cartridge.  | No    |
| Enable CashAppPay (`enableCashAppPay`)     | Sets if Cash App Pay is enabled/disabled in the cartridge.<br>**Note:** Cash App Pay gives customers the option to pay with Cash App, but relies on a connection to your Cash App Afterpay merchant account for settlement. If you are setting this preference to `true`,  ensure that: <br>Cash App Pay integration is included in your Cash App Afterpay merchant contract and enabled on your Cash App Afterpay merchant account <br>Enable Cash App Afterpay is also true. Cash App Pay won’t load without it on the checkout page. | No      |
| Brand settings (`apBrandSettings`) | Cash App Afterpay brand-related settings in JSON format where: <br>Brand – Afterpay <br>Service – the field is used to identify the service with Cash App Afterpay.(You can find the services under *Administration* > *Operations* > *Services*).      | ` {     "US": {         "brand": "afterpay",         "service": "afterpay.service.US"     } } ` |
| Afterpay JavaScript URL (`apJavaScript`)          | The endpoint where the javascript library is obtained from – Use: <br>Sandbox - https://js-sandbox.squarecdn.com/square-marketplace.js <br>Production - https://js.squarecdn.com/square-marketplace.js     |    |
| Afterpay Display Product Details Page Information (`apDisplayPdpInfo`) | Sets if the Cash App Afterpay messaging is displayed on the **Product Details** page.  | Yes |
| Afterpay Display Product List Page Information (`apDisplayPlpInfo`) | Sets if the Cash App Afterpay messaging is displayed on the **Product List** Page.   | No  |
| Afterpay Display Cart Page Information (`apDisplayCartInfo`)         | Sets if the Cash App Afterpay messaging is displayed on the **Cart** Page.      | Yes        |
| Afterpay Payment Mode (`apPaymentMode`)           | Sets if the payment should be authorized only or if the merchant will use **Direct Capture** instead.   | Merchant Specific – Select the ones to be supported.         |
| CapturePaymentTimeout (`apCaptureTimeout`)        | Sets timeout for the **Direct Timeout Capture** payments.      |  |
| apDelayRetry (`apDelayRetry`)        | Sets the delay time for the unavailable service    |        |
| Enable Express Checkout (`apEnableExpressCheckout`)       | Enables the **Express Checkout** feature.       | Yes      |
| Enable BuyNow (`apEnableExpressCheckoutBuyNow`)         | Enables the **BuyNow** mode. Skips review page on merchant checkout. (Note: Only used for **Integrated Shipping**)     | Yes    |
| Express Checkout Shipping Strategy (`apExpressCheckoutShippingStrategy`)       | Select either **Integrated Shipping** (Cash App Afterpay Checkout prompts for shipping method), or **Deferred** (merchant site handles shipping method selection)<br><br>**Note:** If there are multiple shipping methods in the cart, the cartridge disregards this preference and selects the deferred shipping strategy.       | Integrated           |
| Description Express Checkout will use for In-Store Pickup (`apStorePickupDescription`) | Prompt to use in Cash App Afterpay Express Checkout for in-store pickup orders     | Available for next-day pickup                                                                   |
| Enable Express Checkout on Product Details Page (`apEnableExpressCheckoutPdp`)         | Enables Express Checkout directly from the product detail page. If this setting is disabled but Express Checkout is enabled, the button appears only on the cart page for SiteGenesis storefronts, the cart page and minicart for SFRA storefronts.       | No    |
| Enable Express Checkout option on cart (`apEnableExpressCheckoutCart`)      | Enable Express Checkout option on cart and minicart(SFRA) page.      |  Yes   |
| Default Controller Cartridge Name (`apControllerCartridgeName`)                        | This is used for SiteGenesis only and can be ignored for SFRA.   | `app_storefront_controllers`   |
| Default Core Cartridge (`apCoreCartridge`)      | This is used for SiteGenesis only and can be ignored for SFRA.      | `app_storefront_core `   |
| Restricted Products(`apRestrictedProducts`)        | The product ids of products that are to be excluded from Cash App Afterpay separated by “,”      | |


## Add the Cash App Afterpay Image to the Payment Method (For SiteGenesis)

To display the Cash App Afterpay image on the site, you must add the image to your site:

1. Go to *Merchant Tools* > *Ordering* > *Payment Methods*.

2. Select the payment method with the ID *AFTERPAY/CASHAPPPAY* (depending on the target region) and locate the image attribute and upload the image included in the cartridge.

    The images are:

    * int_afterpay_sg/cartridge/static/default/images/logo-afterpay-colour.png

    * int_afterpay_sg/cartridge/static/default/images/cashapppay-logomark1x.png
