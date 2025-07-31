---
stoplight-id: 4a4u4xkihntrd
internal: true
---

# Integrated Shipping

This feature improves the customer experience by embedding your shipping options directly into the Cash App Afterpay Express Checkout flow. It streamlines the checkout process and has two main elements, address and shipping options.

You can also combine integrated shipping with the `buyNow` flag. This creates a one-stop checkout that immediately precedes the order confirmation page.

We recommend the Integrated Shipping flow for merchants with:

- Fewer than five shipping options

- A single shipping option for an entire order (i.e. no Stock Keeping Unit (SKU) level options)

- Simple tiered shipping options (e.g. standard, express, rush)

- A pickup-in-store option before checkout entry

## Configuration Settings and Defaults

Integrated Shipping is configured in the call to `initializeForPopup`, and the **Express Checkout** button triggers this call. Integrated Shipping needs `addressMode` to be an option that contains shipping options. See the address modes with shipping options below.

In any case, to function, Integrated Shipping needs `shippingOptionRequired` to be `true` - this is the default setting. Also, an `onShippingAddressChange` callback must be defined. See the JavaScript example below.

```JavaScript

AfterPay.initializeForPopup({
  // ...
  shippingOptionRequired: true,
  onShippingAddressChange: function (data, actions) {
    /* address in `data` */
    /* calc options, then call `actions.resolve(options)` */
  },
});
```

Full Example with Integrated Shipping

```JavaScript

AfterPay.initializeForPopup({
  countryCode: 'US',
  onCommenceCheckout: function(actions) {
    /* retrieve cash app afterpay token from your server */
    /* then call `actions.resolve(token)` */
  },
  onShippingAddressChange: function (data, actions) {
    /* required for Integrated Shipping  */
    /* address in `data` */
    /* calc options, then call `actions.resolve(options)` */
  },
  onShippingOptionChange: function (data) {
    /* optional - chosen option in `data` */
  },
  onComplete: function (data) {
    /* handle success/failure of checkout */
  },
  target: '#afterpay-express-button',
  buyNow: false,
  pickup: false,
  shippingOptionRequired: true
})
```

Integrated Shipping is enabled by default for Express orders. To disable it, set `shippingOptionRequired` to false. If you do not specify an `addressMode`, the mode ADDRESS_WITH_SHIPPING_OPTIONS is enabled by default for Express orders. To change it, you can set the `addressMode` to one of the alternative `addressMode` options.

## Address Mode

To support different shipping types in the checkout, the property `addressMode` must be configured with a provided constant. These constants have the form `AfterPay.ADDRESS_MODES.<NAME>`, where `<NAME>` is one of the constants in the tables:

| Constant (with shipping options) | Description                                                                                                                                                                                           |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ADDRESS_WITH_SHIPPING_OPTIONS    | This is the default configuration. Displays at checkout so the customer can optionally configure their shipping address. They can also select from the merchant’s list of available shipping options. |
| SHIP_TO_ORDER_ADDRESS            | Displays at checkout with the chosen customer shipping address and the ability to select from the merchant’s list of available shipping options.                                                      |
| PICKUP_FROM_ORDER_ADDRESS        | Displays at checkout with the chosen merchant pickup address for the order.                                                                                                                           |

| Constant (without shipping options)            | Description                                                                                                                                                         |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ADDRESS_WITHOUT_SHIPPING_OPTIONS               | Displays checkout with the option for the customer to configure their shipping address without specifying the type of shipping.                                     |
| SHIP_TO_ORDER_ADDRESS_WITHOUT_SHIPPING_OPTIONS | Displays checkout with the option for the customer to configure their shipping address only with the intention to buy now.                                          |
| NO_ADDRESS                                     | For checkouts that require no address for product delivery, for example, digital goods. This displays at checkout without the address and shipping option sections. |

```javascript
AfterPay.initializeForPopup({
  // ...
  addressMode: AfterPay.ADDRESS_MODES.NO_ADDRESS,
})
```

Integrated Shipping also requires `shippingOptionRequired` to be true (enabled by default) and an **onShippingAddressChange** callback must be defined:

```javascript
AfterPay.initializeForPopup({
  // ...
  shippingOptionRequired: true,
  onShippingAddressChange: function (data, actions) {
    /* address in `data` */
    /* calc options, then call `actions.resolve(options)` */
  },
});
```

## Restrictions

Integrated Shipping needs the Express Checkout flow launched as a popup. This is due to the way shipping information is communicated over the front-end. The redirect method is not supported.

<!-- theme: warning -->

> **Cross Border Trade**
>
> If you use our [Cross Border Trade](../WELCOME/cross-border-trade.md) feature with Express Checkout, always ensure that the currency is consistent throughout the entire checkout flow.
>
> This also applies to shipping costs and taxes. Ensure the same currency used at the start of the Cash App Afterpay checkout flow is the currency used for these transactions.

## Listening for Address Changes

The Shipping Address Change callback is a feature of the Express Checkout. This callback allows you, the merchant, to dynamically update shipping options and taxes based on the shipping address chosen by the customer.

The shipping address change callback is required:

- If you intend to update the order total based on a chosen shipping address
- To validate that you can ship to the selected address

To set up the Shipping Address Change callback, implement the `onShippingAddressChange` function. This function is passed in two arguments: `data` and `actions`.

How you calculate the cost of shipping options is entirely managed by you. You can use Javascript to calculate the cost of shipping options or hand off to an internal API.

If shipping options are available for the given address, you can return them to Cash App Afterpay. To do this, use the `actions.resolve` shown in the code example below. Similarly, use the `actions.reject` when shipping is unavailable.

**Example retrieving shipping options via API**

```JavaScript

AfterPay.initializeForPopup({
  // ...
  onShippingAddressChange: function (data, actions) {
    fetch('/your-shipping-endpoint', {
      method: 'POST',
      headers: { 'content-Type': 'application/json' },
      body: JSON.stringify(data),
    }).then(function(options) {
      actions.resolve(options)
    }).catch(function(error) {
      // Parse the response and send an AfterPay rejection, e.g.:
      actions.reject(AfterPay.CONSTANTS.SHIPPING_UNSUPPORTED)
    })
  },
})
```

**Example calculating shipping options in JS**

```JavaScript

AfterPay.initializeForPopup({
  // ...
  onShippingAddressChange: function (data, actions) {
    if (data.countryCode !== 'US') {
      // Reject any unsupported shipping addresses
      actions.reject(AfterPay.CONSTANTS.SHIPPING_UNSUPPORTED)
    } else {
      // Calc shipping inline
      actions.resolve([ {
        id: '1', name: 'Standard', description: '3 - 5 days',
        shippingAmount: { amount: '0.00', currency: 'USD'},
        taxAmount: { amount: '3.18', currency: 'USD'},
        orderAmount: { amount: '34.99', currency: 'USD'},
      }, {
        id: '2', name: 'Priority', description: 'Next business day',
        shippingAmount: { amount: '10.99', currency: 'USD'},
        taxAmount: { amount: '4.28', currency: 'USD'},
        orderAmount: { amount: '47.08', currency: 'USD'},
      } ])
    }
  },
})
```

**The Data Argument**

| Property      | Type   | Description                                                                                               |
| :------------ | :----- | :-------------------------------------------------------------------------------------------------------- |
| `name`        | String | Full name of the customer.                                                                                |
| `address1`    | String | First line of the address.                                                                                |
| `address2`    | String | Second line of the address.                                                                               |
| `area2`       | String | Village/local area of the address.                                                                        |
| `suburb`      | String | Suburb/City of the address.                                                                               |
| `state`       | String | AU: State, NZ: Region, UK: County, US: State, CA: Province or Territory.                                  |
| `postcode`    | String | ZIP or postal code. If the country does not have postcodes, the countryCode is sent as the value instead. |
| `countryCode` | String | The [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code.                  |
| `phoneNumber` | String | The phone number in [E.123](https://en.wikipedia.org/wiki/E.123) format.                                  |

Cash App Afterpay calls your `onShippingAddressChange` function when:

- The customer first enters the Cash App Afterpay summary page

- The customer makes a change to their shipping address on the Cash App Afterpay summary page

Cash App Afterpay provides the following parameters to your `onShippingAddressChange` function:

`data` parameter: This contains the customer’s selected address with the fields:

- `name`, `phoneNumber`, `address1`, `address2`, `area2`, `suburb`, `state`, `postcode`, and `countryCode`

`action` parameter: This object returns your response to the Cash App Afterpay checkout. It consists of the following methods:

- `resolve` : Call this method to provide the shipping options applicable to the customers address. Takes an array of `ShippingOption` objects.

- `reject` : Call this method when you are unable to handle the request. Do not throw an error, instead call this method with a `ShippingConstant` as the first argument to indicate a status

```JavaScript title="example"
    actions.reject(AfterPay.CONSTANTS.SHIPPING_UNSUPPORTED)
```

## Shipping Option model

| Attribute      | Type             | Description                                                             |
| -------------- | ---------------- | ----------------------------------------------------------------------- |
| id             | String           | (required)	A shipping option identifier. Max length 128.                |
| name           | String           | (required)	The name of the shipping options.                            |
| shippingAmount | Money            | (required)	The shipping amount (without tax, if including `taxAmount`). |
| taxAmount      | Money            | (optional)	The tax amount.                                              |
| orderAmount    | Money (required) | The total amount for the order including shipping and taxes.            |
| description    | String           | A description for this shipping option.                                 |

> For [Cross Border Trade](../WELCOME/cross-border-trade.md) orders, the shipping costs and taxes must be returned in the same currency in which the checkout is initiated. <br/><br/>**Example:** For a US merchant displaying a 100 USD order in AUD for an Australian customer on their website – When initiating Cash App Afterpay checkout, If you initiate checkout by the order amount in USD (i.e. $100 USD), then you must also send the shipping costs and taxes in USD as part of the `onShippingAddressChange` callback. Likewise, if you initiate checkout by sending the order amount in AUD following currency conversion on your side (i.e. $150 AUD), ensure that the shipping costs and taxes are also sent in AUD. In other words, the currency must be consistent throughout the entire checkout flow.

## Shipping Constants

To indicate a number of error scenarios, `actions.reject()` may be invoked with a provided constant.

The form of these constants is `AfterPay.constants.<NAME>`, where `<NAME>` is one of:

| Constant                      | Description                                 |
| ----------------------------- | ------------------------------------------- |
| SHIPPING_ADDRESS_UNRECOGNIZED | Unrecognized address                        |
| SHIPPING_ADDRESS_UNSUPPORTED  | Recognized address, but will not ship there |
| SERVICE_UNAVAILABLE           | General service error.                      |

<!-- theme: warning -->

> **Warning**
>
> Cash App Afterpay Express Checkout does not do any arithmetic. Your web app must calculate the correct total. Each shipping option must have a total order amount that includes taxes and shipping.

## Listening for Shipping Option Changes

The `onShippingOptionChange` callback allows you, the merchant, to track the customer’s chosen shipping option as it changes. It is optional, and is called each time a customer selects a shipping option. This function is passed one argument: `data`

`data` parameter (object): This contains the customer’s selected shipping option, as provided in the response from `onShippingAddressChange`, with fields:

| ID | Name | Description | Shipping Amount | Order Amount |
| -- | ---- | ----------- | --------------- | ------------ |
| id | name | description | shippingAmount  | orderAmount  |

```js

AfterPay.initializeForPopup({
  // ...
  onShippingOptionChange: function (data) {
    console.log(data)
  },
})
```

See also [Updating the Chosen Shipping Option](#updating-the-chosen-shipping-option)

## Preselected Shipping Option

If you enable your customers to enter/select their shipping option before the Cash App Afterpay Express checkout, this information can be passed to Cash App Afterpay. We use this preselected shipping option to ensure the same shipping option is automatically selected in the Cash App Afterpay checkout flow. Customers can change or update this shipping option if they want.

To enable preselected shipping option, set the shipping option ID in the `shippingOptionIdentifier` body parameter when the order is created. This enables the checkout to preselect that option if it is returned from the `onShippingAddressChange` when checkout first loads.

Preselected Shipping Option example:

```
curl --request POST \
  --url https://api-sandbox.afterpay.com/v2/checkouts \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"amount":{"amount":"10.00", “currency”: “AUD”}, “mode”: “express”, "merchant": {"popupOriginUrl": "https://example.com"}, "shipping": {"name": "Your Store Name", "line1": "123 Store Address", "postcode": "0000"}, “shippingOptionIdentifier”: “standard”
}}'

```

Once a customer has entered or chosen their address, you can give them a list of shipping options available for that address. This is an option, that enables it to set the `addressMode` in `initializeForPopup` to one of the following:

- AfterPay.ADDRESS_MODES.SHIP_TO_ORDER_ADDRESS - This enables the list of shipping options

- AfterPay.ADDRESS_MODES.SHIP_TO_ORDER_ADDRESS_WITHOUT_SHIPPING_OPTIONS - This enables the address, but without an associated list of shipping options

```json
AfterPay.initializeForPopup({
  // ...
  addressMode: AfterPay.ADDRESS_MODES.SHIP_TO_ORDER_ADDRESS,
})
```

Create the checkout V2 API call.

Ensure that the shipping address the customer selects/enters is sent to the `shipping` body parameter. See below:

```json
curl --request POST \
  --url https://api-sandbox.afterpay.com/v2/checkouts \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"amount":{"amount":"10.00", “currency”: “AUD”}, “mode”: “express”, "merchant": {"popupOriginUrl": "https://example.com"}, "shipping":{"name":"Joe Consumer","line1":"123 chosen user address", "postcode":"3000", "region":"VIC", "countryCode":"AU"}}'
```

## Updating the Chosen Shipping Option

This is an option. If you want to allow the shipping option amounts to be modified once the customer has selected a shipping option, `onShippingOptionChange` can take an additional action argument. This argument can inform the checkout of these changes.

When the call to onShippingOptionChange happens:

1. Use the shipping option data and make the required modification (eg. contact your backend api to recalculate the tax value of the selected shipping option).

Once you have an updated shipping option you should:

1. Use `actions.resolve` to return an object that contains:

- `id` - this should be the same shipping option ID as received  in `onShippingOptionChange`
- `shippingAmount`- the updated shipping amount of the selected shipping option
- `taxAmount` - the updated tax amount of the selected shipping option
- `orderAmount`- the updated order amount of the selected shipping option to the Cash App Afterpay Express checkout, or use `actions.reject` to signal an error

```javascript
AfterPay.initializeForPopup({
  // ...
  onShippingOptionChange: function (data, action) {
      fetch('/your-update-shipping-option-endpoint', {
          method: 'POST',
          headers: { 'content-Type': 'application/json' },
          body: JSON.stringify(data),
      }).then(function(options) {
          actions.resolve({
             id: data.id, 
             shippingAmount: { amount: '0.00', currency: 'AUD'},
             taxAmount: { amount: '3.18', currency: 'AUD'},
             orderAmount: { amount: '34.99', currency: 'AUD'},
          })
      }).catch(function(error) {
          // Parse the response and send the error, e.g.:
          actions.reject(error)
      })
  },
})
```

The `onShippingOptionChange` actions argument

| Property  | Type     | Description                                                                                                                                                                     |
| --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `resolve` | Function | Call this method to send the modified shipping option. Takes a single shipping option, see the _Shipping Option model to be resolved for `onShippingOptionChange`_ table below. |
| `reject`  | Function | Call this method when you are unable to handle the request.                                                                                                                     |

Shipping Option model to be resolved for `onShippingOptionChange`

| Attribute        | Type                                            | Description                                                                                       |
| ---------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `id`             | String required                                 | The shipping option identifier. This should match the ID of the shipping option you are updating. |
| `shippingAmount` | [Money](../ONLINE-API/Money-object.md) required | The updated shipping amount (without tax, if including `taxAmount`).                              |
| `taxAmount`      | [Money](../ONLINE-API/Money-object.md) optional | The updated tax amount.                                                                           |
| `orderAmount`    | [Money](../ONLINE-API/Money-object.md) required | The updated total amount for the order including shipping and taxes.                              |

## Listening for Warning/Error messages

To handle logging/warning/error messages, you can replace `AfterPay.onMessage` with a custom function. The default function is:

```js

AfterPay.onMessage = function (payload) {
  console[payload.severity](payload.message)
}
```

Replacing this `AfterPay.onMessage` function with a custom function is optional.

## Buy Now

When the Express Checkout is complete, you may either call the `Auth` endpoint immediately or continue checkout on your review page. If you are authorizing (or capturing) payment immediately, set the `buyNow` flag to true - this shows the customer a “Confirm” button at the end of their Cash App Afterpay journey.

```JavaScript

AfterPay.initializeForPopup({
  // ...
  buyNow: true,
})
```

![integrated-shipping_buy now.png](<../../assets/images/integrated-shipping_buy now.png>)

## Configuring a Pickup Order

You can taylor the Express Checkout experience for Click & Collect and other pickup flows. Do the following:

1. Allow your customers the ability to choose pickup options before they select Cash App Afterpay Express. This should include any decisions that may impact the cost of delivery, for instance pickup location and date.

2. If the customer has opted for pickup, provide the chosen pickup address when creating the order via the `shipping` body parameter

```cURL title="example"

    curl --request POST \
    --url https://api.us.afterpay.com/v2/checkouts \
    --header 'accept: application/json' \
    --header 'content-type: application/json' \
    --data '{"amount":{"amount":"10.00", “currency”: “USD”}, “mode”: “express”, "merchant": {"popupOriginUrl": "https://example.com"}, "shipping": {"name": "Your Store Name", "line1": "123 Store Address", "postcode": "0000"}}'
```

3. When invoking `initializeForPopup`
   - Set the pickup flag to `true`.
   - Configure your `onShippingAddressChange` handler to return the name and description of their pickup choice. This will likely mean returning only a single option
   ```js title="example"

   actions.resolve([ {
     id: 'pickup-store-123', name: 'Click & Collect',
     description: 'Available for next-day pickup',
     shippingAmount: { amount: '0.00', currency: 'USD'},
     taxAmount: { amount: '3.18', currency: 'USD'},
     orderAmount: { amount: '34.99', currency: 'USD'},
   } ])
   ```
   - Depending on your configuration, your frontend may have already invoked `initializeForPopup` before knowing whether the customer will opt for pickup. It is safe to invoke `initializeForPopup` multiple times; each call will overwrite the previous settings. In this case you may choose to call `initializeForPopup` in response to the customer selecting a pickup option.

4. Use your order review page to collect additional information regarding the pickup, for example, choosing another person to pick up the order. These details must not affect the order total.
