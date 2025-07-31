---
stoplight-id: z5ddgvjxi0slu
internal: true
---

# Add messaging to the dynamic/drawer cart

To add messaging to the dynamic/drawer cart, do the following:

1. Navigate to your `theme.liquid file` and add the standard code snippet.
2. Find the required selector on the drawer cart.
3. Add the selector to the code and enable the dynamic cart integration.

## Example Code snippet for Afterpay US

```js

// var afterpay_dynamic_cart_integration_enabled = true;

// var afterpay_dynamic_cart_selector = '.cart-drawer__footer .totals';

// var afterpay_dynamic_cart_observer_target = '#CartDrawer';

```

## Example of code with selectors

```js
var afterpay_dynamic_cart_integration_enabled = true;
var afterpay_dynamic_cart_selector = '.total';
var afterpay_dynamic_cart_observer_target = '#CartDrawer';
```

## Example of the completed Sliding Cart

![Completed sliding cart image redacted](../../../assets/images/barber.png)
