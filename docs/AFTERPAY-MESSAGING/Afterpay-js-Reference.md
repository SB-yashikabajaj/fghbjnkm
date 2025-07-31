---
stoplight-id: 28utzfw4nyxwd
---

# Afterpay.js Reference

> **HTML Dataset Attributes**
> 
> The `<afterpay-placement>` web component is configurable via a set of  [data attributes](https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes)
> 
> For Placements initialized through JavaScript, all attributes should be provided in camel-case.  
> See Mozillas [reference](https://developer.mozilla.org/en-US/docs/Web/API/HTMLOrForeignElement/dataset#name_conversion) on dataset naming conversion for more information.

## Attribute List

Attribute | Accepted Values |
---------|----------|
`amount` | A Number - see the [Definition](#amount). | 
`amount-selector` | A CSS Selector in the DOM - see the [Definition](#amount-selector).| 
`amount-mutation-selector` | Any CSS Selector in the DOM - see the [Definition](#amount-mutation-selector). | 
`badge-theme` | Black-on-white, white-on-black, mint-on-black, and black-on-mint. See the [Definition](#badge-theme).|
`cart-is-eligible` | True or false. See the [Definition](#cart-is-eligible). |
`cbt-enabled` | True or false. See the [Definition](#cbt-enabled). |
`currency` | AUD, CAD, EUR, GBP, NZD and USD - see the [Definition](#currency). |
`data-amount-range` | JSON stringified array of numbers/strings. See the [Definition](#data-amount-range). |
`decimal-separator` | . (period) and , (comma) - see the [Definition](#decimal-separator). |
`intro-text` | Pay, pay, In, in, Or, or, Pay in, pay in. See the [Definition](#intro-text). |
`is-eligible` | True or false. See the [Definition](#is-eligible). |
`locale` | en_AU, en_CA, en_GB, en_NZ, en_US, fr_CA. See the [Definition](#locale) |
`logo-type` | compact-badge, badge, or lockup. See the [Definition](#logo-type). |
`lockup-theme` | black, white, mint - see the [Definition](#lockup-theme). |
`mobile-view-layout` | two-by-two or four-by-one - see the [Definition](#mobile-view-layout) |
`modal-id` | Provided by Afterpay - see the [Definition](#modal-id). |
`modal-link-style` | learn-more-text, more-info-text, circled-info-icon, circled-question-icon, or none. See the [Definition](#modal-link-style). |
`modal-theme` | white. See the [Definition](#modal-theme). |
`payment-amount-is-bold` | true or false. See the [Definition](#payment-amount-is-bold). |
`price-table-theme` | black or white - see the [Definition](#price-table-theme). |
`show-interest-free` | True or false. See the [Definition](#show-interest-free). |
`show-lower-limit` | True or false. See the [Definition](#show-lower-limit). |
`show-upper-limit` | True or false. See the [Definition](#show-upper-limit). |
`show-with` | True or false. See the [Definition](#show-with). |
`size` | xs - 12px, sm - 14px, md - 16px, lg - 18px. See the [Definition](#size). |
`thousands-separator` | . (period) and , (comma) - see the [Definition](#thousands-separator). |
`type` | price-table, or price-paragraph - see the [Definition](#type). |

## Amount

The value provided to the AfterpayPlacement through the `amount` attribute reflects the full price displayed to the customer on the page. The library calculates the installments and displays the messaging appropriately.

On a product page, the amount should be the product price.
On the cart page, the amount should be the *total*.


Accepted Values | 
---------|
Any Integer, or Double with at most 2 significant figures after the decimal separator. | 

The Cash App Afterpay Messaging automatically calculates the new instalment price when the amount attribute changes.

**HTML**

```json
<afterpay-placement data-amount="400"></afterpay-placement>
```

**JavaScript**

```js
const AfterpayPlacement = new Afterpay.AfterpayPlacement()
AfterpayPlacement.amount = 400;
```

## amount-selector

Accepts the [CSS selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) corresponding to the price element on the page. The Cash App AfterpayPlacement element reads the price text from the page and sets the `amount` attribute on the component. 

This attribute takes the second highest precedence after `amount`, and if neither are specified the default amount is set to zero.

> **Price Observers**
>
> Assign a value to `data-amount-selector` to watch for text content changes on a given element; the component will automatically update with the newly calculated price.

**HTML**

```html
<div class="pdp-wrapper">
   <span id="productPrice">59.99</span>
 </div>

<afterpay-placement
   data-amount-selector ="#productPrice">
</afterpay-placement>
```

Configuring the placement with `data-amount-selector` enables the placement to track updates to the price element. When a change is detected, the installment messaging automatically updates with the new calculated installment amount.  

## amount-mutation-selector

Accepts any [CSS selector](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) corresponding to the "target" element on the page to watch for changes.

When `amount-mutation-selector` is defined, an attribute to retrieve the current amount on the page must also be defined. There are two ways to achieve this:

1. Setting `data-amount` .

2. Retrieving the price text from `data-amount-selector`.

**HTML**
```html
<afterpay-placement
     data-amount-mutation-selector = "#targetElement"
     data-amount-selector ="#productPrice">
</afterpay-placement>
```
*Useful for eCommerce platforms like Shopify and BigCommerce where the product price is available to template pages*.

**HTML**
```html
<afterpay-placement
     data-amount-mutation-selector = "#targetElement"
     data-amount ="{{product.price}}">
</afterpay-placement>
```

## cart-is-eligible

Accepted values: `true`, `false`  
When true, the price paragraph displays the normal installment messaging.  
When false, the price paragraph renders *Afterpay not available* messaging.

For more information, see [Set Messaging For Unavailable Items](Advanced-Configuration.md).

## cbt-enabled

Displays Cash App Afterpay Cross Border Trade (CBT) information in the modal context. 

## currency

When provided, formats the currency for a given locale.

**HTML**

```html
<afterpay-placement
	data-amount="300"
	data-locale="en_US"
	data-currency="USD">
</afterpay-placement>
```

<!--
focus: false
-->
![Currency.png](../../assets/images/Currency.png)


## data-amount-range

When you specify a range of possible prices for a product using the `data-amount-range` attribute and the `data-amount` attribute is set to 0, a new messaging variant appears. This new messaging variant is based on the lowest price within the range that fits the minimum and maximum price thresholds set by the merchant.

**HTML**

```html
<afterpay-placement
 data-amount="0"
 data-locale="en_US"
 data-min="50"
 data-max="1000"
 data-amount-range="[95, 100.00, 222, 333.33, 444, 555.55, 666, 777.777, 888, 999.99, 1111]"             
 data-currency="USD">
</afterpay-placement>
```

In the HTML code example above, the message displayed is:

![data-amount-range-new.png](../../assets/images/data-amount-range-new.png)

When the above attributes are set and the `data-amount` is a valid amount, the messaging with the exact instalment amount is displayed.

## decimal-separator

Accepts: `"."`, `","`  
Sets how the component should parse the provided amount.

## intro-text

The first word(s) of the Cash App Afterpay Messaging Paragraph.

Accepted Values (Sentence Case) | Accepted Values (Lowercase) |
---------|----------|
 Or      | or |
 In      | in |
 Pay     | pay |
 Pay in  | pay in |


**HTML**
```html
<afterpay-placement
	data-amount="300"
	data-intro-text="or"
	data-currency="USD">
</afterpay-placement>
```
So in the picture below, the messaging begins with the word **or**:

<!--
focus: false
-->
![show-interest-free - or 4 payments.png](<../../assets/images/show-interest-free - or 4 payments.png>)

## is-eligible

Accepted values: `true`, `false`  
When true, the price paragraph displays the normal installment messaging.  
When false, the price paragraph renders "Cash App Afterpay not available" messaging 

For more information see [Set Messaging For Unavailable Items](Advanced-Configuration.md)

## locale

Accepted values:  `en_US`


Country| Locale | Brand - Language
---------|----------|---------
United States | en_US | Cash App Afterpay - English

## logo-lockup

Accepted values: `lockup`

<!--
focus: false
-->
![Lockup - White.png](<../../assets/images/Lockup - White-2.png>)

<!--
focus: false
-->
![Lockup - Black.png](<../../assets/images/Lockup - Black-2.png>)

<!--
focus: false
-->
![Lockup - Green Black.png](<../../assets/images/Lockup - Green Black-2.png>)

<!--
focus: false
-->
![Lockup - Green White.png](<../../assets/images/Lockup - Green White-2.png>)

**Logo Lockup HTML**

<!--
type: tab
title: Lockup
-->

```html
<afterpay-placement
	data-amount="55.95"
	data-locale="en_US"
	data-logo-type="lockup">
</afterpay-placement>
```
<!-- type: tab-end -->

## lockup-theme

Accepted values are: `white`

**White**

<!--
focus: false
-->
![Lockup - Messaging.png](<../../assets/images/Lockup - Messaging.png>)


## mobile-view-layout

Changes the price table layout for mobile devices and on smaller screen sizes. 

Accepted values: `two-by-two`, `four-by-one`

<!--
focus: false
-->
![mobile-view-layout.png](../../assets/images/mobile-view-layout-2.png)

Above - `four-by-one` layout.

## modal-id

An attribute provided by Afterpay to display custom modal content.

```html
<afterpay-placement
     data-modal-id="en_US-theme-white-lockup"
     data-amount="400">
</afterpay-placement>
```

## modal-link-style

Value | Column Title | 
---------|----------|
learn-more-text | Learn More |
more-info-text | More Info |
none | No icon or text displayed |

There are also two values that display symbols instead of text:

Value = circled-info-icon

<!--
focus: false
-->
![circled-info-icon.svg](../../assets/images/circled-info-icon.svg)

Value = circled-question-icon

<!--
focus: false
-->
![circled-question-icon.svg](../../assets/images/circled-question-icon.svg)


**HTML**
```html
<afterpay-placement
     data-locale="en_US"
     data-currency="USD"
     data-amount="120.00"
     data-modal-link-style="circled-question-icon">
</afterpay-placement>
```

**Fully Customize "learn more link" using Slots**

Provide a child element to `AfterpayPlacement` with the attribute/value pair `slot="learn-more-link"` to render a custom element which opens the Cash App Afterpay information modal when clicked. 

For example:

```html
<afterpay-placement>
      <img slot="learn-more-link" src="./custom-info-icon.png" >
</afterpay-placement>
```

## modal-theme

Configures the modal theme using one color: `white`.

```html
<afterpay-placement
     data-locale="en_US"
     data-currency="USD"
     data-amount="120.00"
     data-modal-theme="white">
</afterpay-placement>
```
**White Modal Theme**

<!--
focus: false
-->
![Modal Theme.png](<../../assets/images/Modal Theme.png>)

## payment-amount-is-bold

Accepts a boolean, `true` , or `false`. True = payment amount is in bold.

You can also apply this attribute to the `afterpay-price-table` component:

<!--
focus: false
-->
![payment-amount-is-bold.png](../../assets/images/payment-amount-is-bold.png)

In the example above, the $75 prices are all in bold.

## price-table-theme

Configures the modal theme using one of two predefined colors: `green` (default), and `white`.

**Green Theme**

<!--
focus: false
-->
![price-table-theme_green.png](../../assets/images/price-table-theme_green.png)

**Green Theme HTML**

```html
<afterpay-placement 
    data-type="price-table" 
    data-price-table-theme="mint" 
    data-amount="200">
</afterpay-placement>
```

**White Theme**

<!--
focus: false
-->
![price-table-theme_white-new.png](../../assets/images/price-table-theme_white-new.png)


**White Theme HTML**

```html
<afterpay-placement 
    data-type="price-table" 
    data-price-table-theme="white" 
    data-amount="200">
</afterpay-placement>
```

## show-interest-free

Accepts a boolean, `true` , or `false`. If neither are provided, defaults to `true`

**True example** 

*4 interest-free payments of $10.25 with Cash App Afterpay

<!--
focus: false
-->
![show-interest-free.png](../../assets/images/show-interest-free.png)


**False example** 

*Or 4 payments of $10.25 with Cash App Afterpay*

<!--
focus: false
-->
![show-interest-free - or 4 payments.png](<../../assets/images/show-interest-free - or 4 payments-2.png>)

## show-lower-limit

Determines whether to show the lower amount e.g) **$1.00** – $1,000 for products outside of the provided minimum/maximum threshold. See [setting a price range](JavaScript-Library.md)

Accepts a boolean, `true` , or `false`. If neither are provided, defaults to `true`

**True example** 

*available for orders between $10 - $1,000 with Cash App Afterpay*

<!--
focus: false
-->
![show-lower-limit.png](../../assets/images/show-lower-limit.png)


**False example** 

*available for orders over $1*.

<!--
focus: false
-->
![show-lower-limit - over $1.png](<../../assets/images/show-lower-limit - over $1.png>)


## show-upper-limit

Accepts a boolean, `true` , or `false`. If neither are provided, defaults to `true`.

**True example** 

_available for orders up to $1000 with Cash App Afterpay_.

<!--
focus: false
-->
![show-upper-limit.png](../../assets/images/show-upper-limit.png)

**False example** 

_available for orders over $1_

<!--
focus: false
-->
![show-lower-limit - over $1.png](<../../assets/images/show-lower-limit - over $1.png>)

## show-with

Accepts a boolean, `true` , or `false`. If neither are provided, defaults to `true`

**True example** 

*or 4 interest-free payments of $50.00 with*

<!--
focus: false
-->
![show-with.png](../../assets/images/show-with.png)

**False example** 

*or 4 interest-free payments of $50.00*

<!--
focus: false
-->
![show-without.png](../../assets/images/show-without.png)

## size

Accepted values: `xs`, `sm`, `md`, `lg`  
The default size for an AfterpayPlacement is **md** (medium).


Placement Size | Size in Pixels| 
---------|----------|
xs | 12px |
sm | 14px |
md | 16px | 
lg | 18px |

## thousands-separator

Accepts: `"."`, `","`  
Sets how the component should parse the provided amount. 

By default, US, CA, AU, and NZ use a **comma** to parse the amount in **thousands**.  
However, in Europe, the thousands separator is automatically configured to accept amounts formatted with a **decimal** in the thousands place.

## type

Refer to [constants](#constants) for a list of possible values.


Name | Value | Reference
---------|----------|---------|
PRICE_PARAGRAPH | "price-paragraph" | `Afterpay.placementTypes.PRICE_PARAGRAPH`
PRICE_TABLE | "price-table" | `Afterpay.placementTypes.PRICE_TABLE`

### Price Table

```html 
<afterpay-placement
  data-type="price-table"
  data-amount="400"
></afterpay-placement
```
```JavaScript
const priceTable = new Afterpay.AfterpayPlacement()
priceTable.type = Afterpay.placementTypes.PRICE_TABLE
priceTable.amount = 400;
document.body.appendChild(priceTable);
```

### Price Paragraph

> **Note:** 
> If no the `data-type` attribute is not provided, the `AfterpayPlacement` will default to `PRICE_PARAGRAPH`

```html HTML
<afterpay-placement
  data-type="price-paragraph"
  data-amount="400"
></afterpay-placement
```
```JavaScript
const placement = new Afterpay.AfterpayPlacement()
placement.type = Afterpay.placementTypes.PRICE_PARAGRAPH
placement.amount = 400;
document.body.appendChild(placement);
```

## Constants

`<CONSTANT_NAME>` | Values |
---------|----------|
`currency` | `USD` |
`locale` | `EN_US` |
`logoType`  | `BADGE`, `LOCKUP` |
`modalLinkStyle` | `CIRCLED_INFO_ICON`, `LEARN_MORE_TEXT`, `MORE_INFO_TEXT`, `CIRCLED_QUESTION_ICON`,  
`NONE` |
`placementTypes` | `PRICE_TABLE`, `PRICE_PARAGRAPH`
`size` | `XS`, `SM`, `MD`, `LG`
`mobileViewLayout` | `FOUR_BY_ONE`, `TWO_BY_TWO`
`theme.`**badge** | `BLACK_ON_MINT`, `BLACK_ON_WHITE`, `MINT_ON_BLACK`, `WHITE_ON_BLACK` |
`theme.`**lockup** | `BLACK`, `WHITE`, `MINT` |
`theme.`**modal** | `WHITE`
`theme.`**priceTable** | `BLACK`, `WHITE` |

> Using Cash App Afterpay Constants
> 
> Constants are exposed to the window via the Afterpay object `Afterpay.<constant_name>`. 
> 
> See some examples below
> 
> ```js
> console.log(Afterpay.locale.EN_US) //  "en_US"
> console.log(Afterpay.theme.lockup) //  "{"BLACK":"black","WHITE":"white","MINT":"mint"}"
> console.log(Afterpay.theme.lockup.BLACK) //  "black"
> 
> ```
> 
> Constants are available once the `Afterpay.ready` event has been dispatched.

## Functions


Name | Description |
---------|----------|
`createPlacements` | Add one or more placements to the page using the targetSelector attribute. [More Info](Advanced-Usage.md) |
`launchModal` | Dynamically open the Cash App Afterpay Modal |
`generatePaymentAmount` | Given a price, returns the payment amount as a float |

## Window Events

Name | Description |
---------|---------|
`ready` | Custom Window Event dispatched when `Afterpay.js` is successfully initialized. |
`modalRenderComplete` | Custom Window Event dispatched when the `<afterpay-modal>` finishes rendering |

## Constructors

Name | Description |
---------|---------|
`AfterpayPlacement` | Creates and returns a new `AfterpayPlacement` class reference. |

Constructors must be instantiated with "new".

`const Placement = new Afterpay.AfterpayPlacement();`

Full example:

```js
// setup event listener for the Afterpay.js initialization function. 

window.addEventListener("Afterpay.ready", function(){
    const Placement = new Afterpay.AfterpayPlacement();
    Placement.locale = "en_AU";
    Placement.amount = 40.00;   

    const parentElement = document.getElementById("#product-price-wrapper")
    parentElement.appendChild(Placement);

});
```

## Additional Components

### Price Table ( Harvey Balls )

<!--
focus: false
-->
![additional-components - price-table-theme_white.png](<../../assets/images/additional-components - price-table-theme_white.png>)

```HTML

 <afterpay-price-table></afterpay-price-table>
 ```

|Attribute	|Type|
|---|---|
|data-amount|	Number (required)|
|data-locale|	`Afterpay.locale`|
|data-currency	|`Afterpay.currency`|
|data-price-table-theme	|[Afterpay.theme.priceTable](Afterpay-js-Glossary.md)

Rendering via `<afterpay-placement>`

```HTML

  <afterpay-placement
    data-type="price-table"
    data-amount="75.00"
    data-currency="en_US"
> </afterpay-placement>
```