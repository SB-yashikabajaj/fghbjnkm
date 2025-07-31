---
stoplight-id: 64mrfly67s08h
---

# SFRA File Change Review

The following templates are present in Cash App Afterpay's Salesforce Reference Architecture (SFRA) cartridge as well as the `app_storefront_base` cartridge. That means the template in Cash App Afterpay's cartridge will override the base template. 

Since Cash App Afterpay's cartridge was built to work with the base cartridge, this override should be fine. However, if you've made custom changes to these templates in the base cartridge, or have installed plugins which override these templates, you must merge these changes yourself. 

It may be useful to refer to that version to see the Cash App Afterpay-specific changes in the overridden file. In general, comments have been left in the files to make it easier to identify Cash App Afterpay-specific changes vs. base-SFRA content.

| Template File                 | Location & Purpose for Change       |
|-------------------------------|-----------------------------------------------------------|
| `cart.isml`                     | `cartridge/templates/default/cart/cart.ismlIncludes /js/afterpay.js` and `/css/afterpaystyle.js`<br/>Default error messaging on page will also display Cash App Afterpay-specific error messages.     |
| `cartTotals.isml`               | `cartridge/templates/default/cart/cartTotals.ismlDisplay` <br/>Cash App Afterpay messaging under cart totals on the cart page.         |
| `checkoutButtons.isml`          | `cartridge/templates/default/cart/checkoutButtons.isml` <br/>Display Cash App Afterpay Express Checkout Button on the cart page.             |
| `paymentOptionsTabs.isml`      | `cartridge/templates/default/checkout/billing/paymentOptions/paymentOptionsTabs.isml` <br/>Adds a payment tab for Cash App Afterpay and/or Cash App Pay    |
| `paymentOptionsContent.isml`    | `cartridge/templates/default/checkout/billing/paymentOptions/paymentOptionsContent.isml` <br/>Include content displayed in the Cash App Afterpay and/or Cash App Pay payment tab.   |
| `paymentOptionsSummary.isml`    | `cartridge/templates/default/checkout/billing/paymentOptions/paymentOptionsSummary.isml`<br/>Include content displayed in the payment summary when Cash App Afterpay and/or Cash App Pay is the payment method.  |
| `confirmationPaymentInfo.isml`  | `cartridge/templates/default/checkout/confirmation/confirmationPaymentInfo.isml` <br/>Included Cash App Afterpay or Cash App Pay in the payment confirmation.    |
| `checkout.isml`                 | `cartridge/templates/default/checkout/checkout.isml`<br/>Make all default SFRA checkout buttons hideable with CSS. Add the Cash App Afterpay and/or Cash App Pay checkout button. Add Cash App Afterpay Checkout Widget. Include Cash App Afterpay and Cash App Pay client-side JS (JavaScript) and CSS (Cascading Style Sheets). |
| `scripts.isml`| `cartridge/templates/default/common/scripts.isml`<br/>Adds JS files required to load the Cash App Afterpay assets.    |
| `pageFooter.isml`               | `cartridge/templates/default/components/pageFooter.isml`<br/> Adds Cash App Afterpay among the accepted payment methods in the footer.          |
| `addToCartButtonExtension.isml` | `cartridge/templates/default/product/components/addToCartButtonExtension.isml` <br/>Add express checkout buttons on the PDP page.      |
| `setItems.isml`                 | `cartridge/templates/default/product/components/setItems.isml`   |
| `bundleDetails.isml`            | `cartridge/templates/default/product/bundleDetails.isml`<br/> Add Cash App Afterpay messaging for bundles. Include Afterpay JS / CSS.          |
| `productDetails.isml`           | `cartridge/templates/default/product/productDetails.isml`<br/> Include Cash App Afterpay JS/CSS. Display Cash App Afterpay messaging on product details page.|
| `productTile.isml`              | `cartridge/templates/default/product/productTile.isml`<br/> Display Cash App Afterpay messaging on product tile.        |
| `quickView.isml`                | `cartridge/templates/default/product/quickView.isml`<br/> Display Cash App Afterpay messaging on quick view.           |
| `setDetails.isml`               | `cartridge/templates/default/product/setDetails.isml`<br/> Include Cash App Afterpay JS/CSS.   |
| `setQuickView.isml`             | `cartridge/templates/default/product/setQuickView.isml`                                                                                                 |
| `catLanding.isml`               | `cartridge/templates/default/rendering/category/catLanding.isml`<br/> Include Cash App Afterpay JS/CSS.    |
| `searchResults.isml`            | `cartridge/templates/default/search/searchResults.isml`<br/> Include Cash App Afterpay JS/CSS.   |

Similarly, if you’ve made customizations to the following JS (JavaScript) and SCSS (Salesforce Cascading Style Sheet) files, you may need to merge the Cash App Afterpay changes.

| JS File        | Location & Purpose for Change                                               |
|----------------|-----------------------------------------------------------------------------|
| `checkout.js`    | `cartridge/client/default/js/checkout.js` <br/>Include Cash App Afterpay client-side JS.    |
| `productTile.js` | `cartridge/client/default/js/productTile.js` <br/>Include Cash App Afterpay client-side JS. |


| SCSS File     | Location      |
|---------------|----|
| `homePage.scss` | `cartridge/client/default/scss/homePage.scss` <br/> Adds CSS for Cash App Afterpay’s checkout button. Specifically used by the minicart when opened on the store home page. |