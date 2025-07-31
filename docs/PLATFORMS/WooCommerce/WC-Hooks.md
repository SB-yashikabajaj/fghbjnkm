---
stoplight-id: kro4hzwqshqhr
---

# Hooks

This section outlines the WordPress hooks utilised by the Afterpay WooCommerce integration.

## Product Eligibility

The Afterpay plugin runs a series of checks to determine whether Afterpay should be an available payment option for each individual product. Third-party plugins can exclude Afterpay from products that would otherwise be considered supported. This can be done by attaching to the following filter hook:  
`afterpay_is_product_supported`

Example:

```php
/**
 * @param bool		$bool_result
 * @param WC_Product	$product
 */
function afterpay_ips_callback( $bool_result, $product ) {
	# My custom products don't support Afterpay.
	if ($product->get_type() == 'my-custom-product-type') {
		$bool_result = false;
	}
	return $bool_result;
}
add_filter( 'afterpay_is_product_supported', 'afterpay_ips_callback', 10, 2 );
```

## Customising Hooks & Priorities

Various WooCommerce hooks are assumed to be implemented by the active WordPress theme. Afterpay methods can be detached from their default hooks and reattached to different hooks, or to the same hooks with different priorities.

Since version 2.1.0, hooks and priorities can be customised from within the plugin settings page.

![hooks-1.png](../../../assets/images/hooks-1.png)