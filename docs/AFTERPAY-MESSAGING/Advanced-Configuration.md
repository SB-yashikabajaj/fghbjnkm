---
stoplight-id: 4yak9bhkzhith
---

# Advanced Configuration

## Attribute list

You can find the complete attribute list on the [Afterpay-js-Reference Page](Afterpay-js-Reference.md). See also the [Afterpay-js-Glossary](Afterpay-js-Glossary.md).

|Attribute|	Type|	Requirement|
|---|---|---|
|`data-amount`	|Number (decimal)|	Required if `data-amount-selector` is omitted|
|`data-amount-selector`|	String (CSS selector)|	Required if `data-amount` is omitted|


> **Price Observers**
>
> Assign a value to `data-amount-selector` to watch for text content changes on a given element; the component will automatically update with the newly calculated price.


|Boolean Attributes	|Type|	Default|
|---|---|---|
|data-show-interest-free|	Boolean|	true|
|data-is-eligible|	Boolean|	true|
|data-cart-is-eligible	|Boolean|	true|
|data-show-upper-limit	|Boolean|	true|
|data-show-lower-limit|	Boolean	|true|
|data-show-with	|Boolean|	true|
|data-payment-amount-is-bold	|Boolean	|false|
|data-cbt-enabled	|Boolean	|false|


## `data-show-lower-limit`

<!--
focus: false
-->
![data-show-lower-limit](../../assets/images/show-lower.png)

<br>

```HTML

<afterpay-placement
    data-amount="2000"
    data-locale="en_US"
    data-currency="USD"
    data-show-lower-limit="false">
</afterpay-placement>
```

## Set messaging for unavailable items

### Product Pages

Add the attribute `data-is-eligible` to the `<afterpay-placement>` tag and assign its value to `false`.

```HTML

<afterpay-placement
    data-is-eligible="false"
    data-locale="en_US"
    data-currency="USD"
    data-amount="120.00">
</afterpay-placement>
```

<br>

<!--
focus: false
-->
![Product Pages.png](<../../assets/images/Product Pages.png>)


### Cart Page

Add the attribute `data-cart-is-eligible` to the `<afterpay-placement>` tag and assign its value to `false`.

```HTML

<afterpay-placement
    data-cart-is-eligible="false"
    data-locale="en_US"
    data-currency="USD"
    data-amount="120.00">
</afterpay-placement>
```
<br>

<!--
focus: false
-->
![Cart Pages.png](<../../assets/images/Cart Pages.png>)


To return the component back to its standard messaging, either assign `data-is-eligible` / `data-cart-is-eligible` to `true`, or remove the attribute from the web component.

## Customize Text

|Attribute|	Default	|Accepted Values|
|---|---|---|
|`data-intro-text`|	"or"	|In, in, Or, or, Pay, pay, Pay in, pay in|
|`data-modal-link-style`|	"circled-info-icon"	|more-info-text , learn-more-text, circled-question-icon, circled-info-icon|

See the [Dynamic Placements](Advanced-Usage.md) section for infomation on dynamically creating Afterpay Placements.


## Additional Components

### Price Table (Harvey Balls)

<!--
focus: false
-->
![](../../assets/images/pricetable.png)

<br>

```HTML

 <afterpay-price-table></afterpay-price-table>
 ```
 
<br>

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
    data-amount="100.00"
    data-currency="en_GB"
> </afterpay-placement>
```