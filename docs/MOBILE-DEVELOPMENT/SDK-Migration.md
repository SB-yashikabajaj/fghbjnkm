---
stoplight-id: s36zmtbvwmm2c
---

# SDK Migration Guide

<!-- theme: info -->

> This guide is relevant for merchants using the [iOS](https://github.com/afterpay/sdk-ios) and [Android](https://github.com/afterpay/sdk-android) native app SDKs for their current Afterpay integration.

All merchant-owned surfaces featuring “Afterpay” will need to be updated to reflect the new “Cash App Afterpay” brand. This includes the product detail page, cart, checkout, FAQs, emails, and any other pages using Afterpay branding.

## What do I need to do?

### Afterpay checkout

No action is needed. The brand updates will automatically appear within Afterpay checkout when Afterpay is migrated to Cash App Afterpay.

### UI messaging elements

The native Afterpay SDK provides its own UI elements that merchants can use ([iOS](https://afterpay.github.io/sdk-ios/ui-components/) and [Android](https://afterpay.github.io/sdk-android/ui-components/)). These UI elements are embedded in the app's codebase and can't be controlled dynamically from Cash App Afterpay's backend.

The steps to migrate from Afterpay branding to Cash App Afterpay branding depends on whether you use Afterpay's UI elements or your own custom UI elements.

#### Afterpay UI elements

If you use Afterpay UI elements, update your SDK to version 4.8+ on Android and version 5.8+ on iOS to access the rebranded assets.

When you update, you'll see new names that refer to both the Afterpay themes and the Cash App Afterpay themes.  A mapping of the themes and their assets are in the table below.

| Legacy Afterpay theme | Afterpay asset                                                                                   | New Cash App Afterpay theme | New Cash App Afterpay asset                                                                             |
| --------------------- | ------------------------------------------------------------------------------------------------ | --------------------------- | ------------------------------------------------------------------------------------------------------- |
| mintOnBlack           | <img src="../../assets/images/Afterpay_Button_Checkout.png" style="all: unset; width: 250px;" /> | Default                     | <img src="../../assets/images/CashAppAfterpay_Button_Checkout.png" style="all: unset; width: 250px;" /> |
| blackOnMint           | <img src="../../assets/images/Afterpay_Button_Continue.png" style="all: unset; width: 250px;" /> | Alt                         | <img src="../../assets/images/CashAppAfterpay_Button_Continue (1).png" style="all: unset; width: 250px;" /> |
| blackOnWhite          | <img src="../../assets/images/Afterpay_Button_Buy.png" style="all: unset; width: 250px;" />      | Light Monochrome            | <img src="../../assets/images/CashAppAfterpay_Button_Buy (1).png" style="all: unset; width: 250px;" />  |
| whiteOnBlack          | <img src="../../assets/images/Afterpay_Button_Pay.png" style="all: unset; width: 250px;" />      | Dark Monochrome             | <img src="../../assets/images/CashAppAfterpay_Button_Pay.png" style="all: unset; width: 250px;" />      |

##### Cash App Afterpay regions

If your region migrated to the new Cash App Afterpay themes, then the SDK will use the new Cash App Afterpay assets. You must select your preferred theme.


**Asset changes**

- The "Place order" button is replaced by a "Continue with" button. All other button types are the same.
- For the Price Breakdown component, the US region now only supports the Lockup logo type ([iOS](https://afterpay.github.io/sdk-ios/ui-components/price-breakdown/#logo-type) and [Android](https://afterpay.github.io/sdk-android/ui-components/price-breakdown/#logo-type)). Both the Compact Badge and Badge logo types are no longer supported in the US region.

##### Afterpay regions

If your region uses the Afterpay themes, you'll still need to select the appropriate Cash App Afterpay theme that corresponds to the Afterpay asset. However, there will be no changes to the UI and all logos will remain supported.

#### Custom UI elements

If you use custom UI elements, update your custom assets with our rebranded versions [here](https://developers.cash.app/docs/merchant/marketing/brand-assets).

### Need help?

If you have any questions, please contact your Account Manager.
