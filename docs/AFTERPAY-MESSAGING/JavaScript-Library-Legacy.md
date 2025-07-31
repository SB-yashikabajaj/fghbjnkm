---
stoplight-id: r7fhipywd4unn
---

# JavaScript Library (Legacy)

**Information about our older JavaScript library**

----

> **Please Upgrade to our Current JavaScript Library**
> 
> Merchants integrating after August 1, 2020 should visit our new [JavaScript Library](JavaScript-Library.md) for the latest version.

Afterpay has a javascript widget that allows you to easily display installment amounts throughout the checkout flow.

The Javascript can be added in a few lines of code and customized to match the look and feel of your website.

## Loading the Afterpay Widget

Place the code below just before the closing </head> tag:

```HTML
<script type="text/javascript" src="https://static-us.afterpay.com/javascript/present-afterpay.js"></script>
```

## Required Fields

The Afterpay Messaging Widget is constructed by passing a configuration object into the `presentAfterpay` class.

The following object properties are required to construct `presentAfterpay`.


Property | Type | Description
---------|------|---------
`priceSelector` | string | The HTML element the Afterpay Messaging should be positioned below.
`locale` | string | The language of the Afterpay Messaging/ Afterpay Modal content - based on region.

To initialize the the Widget, call the method `.init()`.

![JS Fiddle image](../../assets/images/JS-fiddle.png)[Edit in JSFiddle](https://jsfiddle.net/afterpay/apu6gjqe/)

**JavaScript**

```js
/* Configure the Widget */
    const apConfig = {
      priceSelector: '.product-price',
      locale: 'en_US',
      currency: 'USD',
      minMaxThreshold: {
        min: 100,
        max: 100000,
      },
    };

    /* Initialize the Widget */
    document.addEventListener('DOMContentLoaded', function() {
      new presentAfterpay(apConfig).init();
    })
```

**HTML**

```js
<!doctype html>
<html>

  <head>
    <script type="text/javascript" src="https://static-us.afterpay.com/javascript/present-afterpay.js"></script>
  </head>

  <body>

    <div class="container">
      <div class="ap-example">
        <img id="product-img"
             src="https://static-us.afterpay.com/docs/assets/jsfiddle/sample-product.png"
             alt="small bag" />
             
        <div id="product-description-wrapper">
            <h1>Small Backpack</h1>
```

**Result**

![Afterpay-message.png](../../assets/images/Afterpay-message.png)

