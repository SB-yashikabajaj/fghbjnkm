---
stoplight-id: 321vdna8hzq5s
---

# Advanced Usage

## Dynamically Create Placements with JavaScript

The `createPlacements` function binds to the `Afterpay` window object, exposing new functionality to dynamically create Cash App Afterpay Placements.

```HTML

<script>
    window.addEventListener('Afterpay.ready', function() {
      Afterpay.createPlacements({
        targetSelector: '.placement-card .product-price-basic',
        attributes: {
          amountSelector: '.placement-card .product-price-basic',
        }
      });
    });
</script>
```

This method injects `<afterpay-placement>` onto the page taking into consideration all the configuration values provided as an object.

|Key|	Type|	Description	|Required|
|---|---|--|--|
|`targetSelector`	|string| A selector to specify the reference element next to which the `<afterpay-placement>` element would be placed	|yes|
|`attributes`	|object| An object holding a collection of attributes to be applied to the `<afterpay-placement> `element	|no|


> **Accepted keys on the attributes object**
>
> The keys specified on the `attributes` object are the camel-cased version of the hyphenated data attributes passed to the `<afterpay-placement>` element.
> Default values are in bold

|Attribute name	|Example of a value|	Supported constants/values|	Comments|
|---|---|---|---|
|locale	|Afterpay.locale.EN_US	| EN_US | Cash App Afterpay is avaiable in the USA only.|
|introText|	Pay in	|In, in, Or, or, Pay, pay, Pay in, pay in	||
|currency	|Afterpay.currency.USD	| USD | Cash App Afterpay is avaiable in the USA only. |
|amount	|Any numeric value between 1-2000	|-|	Takes the highest precedence for an amount value
|amountSelector	|Any CSS selector to read the amount from|	-	||
|logoType|	Afterpay.logoType.LOCKUP|	BADGE, LOCKUP	|This is a required attribute when setting the logo type to a lockup|
|badgeTheme	|Afterpay.theme.badge.MINT_ON_BLACK|	BLACK_ON_MINT, BLACK_ON_WHITE, MINT_ON_BLACK, WHITE_ON_BLACK||	
|lockupTheme|	Afterpay.theme.lockup.BLACK	|BLACK, WHITE, MINT	|Make sure the logoType is set to lockup|
|size|	Afterpay.size.SM	|XS, SM, MD, LG	|These are the different messaging sizes supported
isEligible	|false	|true, false	||
|modalLinkStyle	|Afterpay.modalLinkStyle.CIRCLED_AFTERPAY_ICON|	CIRCLED_INFO_ICON, LEARN_MORE_TEXT, MORE_INFO_TEXT, CIRCLED_QUESTION_ICON, NONE	||
|showUpperLimit|	false|	true, false	||
|showLowerLimit|	false	|true, false	|
|modalTheme	|Afterpay.theme.modal.WHITE	|MINT ,WHITE	|


```HTML

<script>
    window.addEventListener('Afterpay.ready', function() {
      Afterpay.createPlacements({
        targetSelector: '.product-price-selector',
        attributes: {
          locale: Afterpay.locale.EN_GB,
          currency: Afterpay.currency.GBP,
          amount: 120,
          amountSelector: '.placement-card .product-price-selector',
          size: Afterpay.size.SM,
        }
      });
    });
  </script>
  ```