---
stoplight-id: 7h5mhmiopb9hd
---
# JavaScript Library

**How can I easily add Cash App Afterpay Messaging to my site?**

---

> **NOTE:** Merchants using our legacy documentation
>
> We recommend you upgrade to our current Cash App Afterpay messaging tool called [On-Site Messaging](Getting-Started-with-Afterpay-On-Site-Messaging.md).

Cash App Afterpay's JavaScript Library allows you to easily display installment amounts throughout the checkout flow.


## Loading the Library

The Afterpay.js script loads various Cash App Afterpay Messaging and assets for merchants to use throughout their store. To load the **Afterpay.js** library add the following async script tag to the `<head>` section of your site.

```HTML

<script src="https://js.afterpay.com/afterpay-1.x.js" data-analytics-enabled
        async
></script>
```

<!-- theme: info -->
> **Note**
>
> If you are using a specific version of the script, please update to version `1.x.js`

## Cash App Afterpay Messaging

To display the installment messaging add the `<afterpay-placement>` tag to the product and cart HTML files. Place the installment messaging immediately below the price element on both product and cart pages.

<!--
focus: false
-->
![Result Messaging.png](<../../assets/images/Result Messaging.png>)


To render Cash App Afterpay messaging with the correct language and calculated installment amount, provide the **locale**, **currency**, and **amount** attributes to the custom element.

```HTML

<afterpay-placement 
    data-locale="en_US"
    data-currency="USD" 
    data-amount="44.00"
 ></afterpay-placement>
 ```

|Attribute	|Type	|Default|
|--|--|--|
|data-locale|	String `required`	|
|[data-currency](Afterpay-js-Glossary.md)|	String `required`|	
|data-amount|	String `required`	|
|data-show-upper-limit|	String|	`true`|
|data-show-lower-limit|	String	|`true`|
|[data-logo-type](Style-Messaging.md)	|String	|`badge`|
|[data-badge-theme](Style-Messaging.md)	|String	|`black-on-mint`|
|[data-size](Style-Messaging.md)|	String	|`md`|

## Pay Monthly enhanced messaging feature

If you are a Cash App Afterpay merchant with a direct integration, you can use Pay Monthly enhanced messaging. This displays specific messages on the product detail page and the shopping cart. See [Pay Monthly enhanced messaging features](Pay-Monthly-enhanced-JavaScript-library-features.md) for more details.


## Setting a price range to show Cash App Afterpay (optional)

`data-min` and `data-max` define the minimum and maximum for the messaging. When a product or cart total is outside of this range, the messaging appears as:

<!--
focus: false
-->
![Setting a price range.png](<../../assets/images/Setting a price range.png>)

Often merchants want to restrict customers from using Cash App Afterpay on items that fall outside a specific price range. To configure the minimum an maximum threshold, add the following attribute to the Afterpay.js Script tag:
E.g)

```HTML

<script
    src="https://js.afterpay.com/afterpay-1.x.js"
    data-analytics-enabled
    data-min="35.00"
    data-max="1000.00"
    async 
></script>
```
<br/>
<br/>

|Attribute|	Type|	Default|
|---|---|---|
|data-min	|String|	`1.00`|
|data-max|	String|	`1000.00`|

### HTML Example

![JS Fiddle image](../../assets/images/JS-fiddle.png)[Edit in JSFiddle](https://jsfiddle.net/afterpay/apu6gjqe/)
```html
<!doctype html>
<html>

  <head>
    <script src="https://js.afterpay.com/afterpay-1.x.js" 
       data-min="25.00" data-max="2000.00" async></script>
  </head>

  <body>

    <div class="container">
      <div class="ap-example">
        <img id="product-img" src="https://static-us.afterpay.com/docs/assets/jsfiddle/sample-product.png" alt="family-reunion-knit-sweater" />

        <div id="product-description-wrapper">
          <h1>Family Reunion Knit Sweater</h1>
          <div class="product-price">$80.00</div>
          <!-- Afterpay Messaging Placement-->
          <afterpay-placement data-locale="en_US" data-amount="20"></afterpay-placement>
        </div>
      </div>
    </div>


  </body>

</html>
```

### Result 

<!--
focus: false
-->
![Cash App Afterpay Messaging.png](<../../assets/images/Cash App Afterpay Messaging.png>)


<!-- theme: info -->
>**Note**
>
> The min and max values only affect the amounts used in the messaging. To request a different minimum or maximum threshold for your account, please contact Cash App Afterpay.