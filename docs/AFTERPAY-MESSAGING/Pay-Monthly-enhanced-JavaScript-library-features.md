---
stoplight-id: p0uqjy142eveo
---

# Pay Monthly enhanced JavaScript library features

---

If you have a direct integration to Cash App Afterpay, you can access some enhanced features for Pay Monthly. 

Merchants who have customer lending (Pay Monthly) enabled can use the existing widget to display specific messaging on the Product Detail Page (PDP) and shopping cart.

<!-- theme: info -->
> **Note**
>
> At present, Pay Monthly is only available to customers with existing Afterpay accounts. Customers who have Cash App accounts only cannot use Pay Monthly.

**What is Pay Monthly?**

Pay Monthly is a monthly payment product that is a long-term, installment-based lending option. It gives your customers more flexible ways to pay for high-value orders greater than $100.

**How does Pay Monthly work in practice?** 

Messaging appears when the cart or item price is greater than or equal to $100. It is displayed up to the data-max value that is returned. See the screenshot below:

<!--
focus: false
-->
![Pay monthly - Messaging.png](<../../assets/images/Pay monthly - Messaging.png>)

Your customer clicks the Cash App Afterpay button on the shopping cart message.

Two monthly payment options appear to the customer, who can select the option they want.

<!--
focus: false
-->
![Pay monthly - Checkout options.png](<../../assets/images/Pay monthly - Checkout options.png>)

There are two ways to add this attribute:

- **Cash App Afterpay placement:** This way is applicable to most merchants

- **JavaScript create placement:** This has more capabilities to dynamically create placements

These two ways are described below.

## Cash App Afterpay placement

Do the following:

If you already use the JavaScript Library's `<afterpay-placement>` element, add the `data-apr-loans-available="true"` attribute.

A full code example, Webcomponent.html, is below. The `aprLoansAvailable` attribute is below the `amount` attribute, and is set to `true`.

```html

<!doctype html>
<html>
 <head>
   <script src="https://js.afterpay.com/afterpay-1.x.js" async onload="createMessaging()"></script>
   <script>
     function createMessaging () {
       Afterpay.createPlacements({
         targetSelector: "#afterpay-messaging-widget",
         attributes: {
           locale: "en_US",
           currency: "USD",
           amount: "420",
           aprLoansAvailable: "true",
         }
       });
     }
   </script>
 </head>
 <body>
   <div id="afterpay-messaging-widget"></div>
 </body>
</html>
```

## JavaScript create placement

Do the following:

1. Check that you use the JavaScript library's `Afterpay.createPlacements` item. If you do, continue to step 2.

2. Find the attributes object and then add `aprLoansAvailable:true`.

A full code example, Webcomponent.js is below. The `aprLoansAvailable` attribute is below the `amount` attribute, and is set to `true`.

```html

<!doctype html>
<html>
 <head>
   <script src="https://js.afterpay.com/afterpay-1.x.js" async onload="createMessaging()"></script>
   <script>
     function createMessaging () {
       Afterpay.createPlacements({
         targetSelector: "#afterpay-messaging-widget",
         attributes: {
           locale: "en_US",
           currency: "USD",
           amount: "420",
           aprLoansAvailable: "true",
         }
       });
     }
   </script>
 </head>
 <body>
   <div id="afterpay-messaging-widget"></div>
 </body>
</html>
```