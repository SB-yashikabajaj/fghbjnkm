---
stoplight-id: 1fs6xrmnsvz7y
internal: true
---

# Hide Payment Methods at Checkout

Shopify Plus merchants can stop Cash App Afterpay and Cash App Pay being offered at the checkout for selected products.

<!-- theme: info -->

> **Note**
>
> This feature is for merchants with a Shopify Plus integration only.

Use this feature to hide the Cash App Afterpay and/or Cash App Pay payment methods at checkout for specific products that you, the merchant, choose.

<!-- theme: info -->

> **Note**
>
> You cannot use Shopify Scripts unless you already have the Script Editor installed. Shopify will not support Shopify Scripts after August 28th 2025.  In future you can use Shopify Functions apps to customize your checkout.

To prevent your customers using Cash App Afterpay or Cash App Pay to pay for a specific product, tag that product as **no-cash-app-afterpay** or **no-cash-app-pay**.

To implement this feature, do the following:

1. Download the [Script Editor Shopify App](https://apps.shopify.com/script-editor).

   ![hide-checkout-1.png](../../../assets/images/hide-checkout-1.png)

2. Add **no-cash-app-afterpay** [Shopify tags](https://help.shopify.com/en/manual/shopify-admin/productivity-tools/using-tags) to each product that is not available to buy with Cash App Afterpay.

3. Add **no-cash-app-pay** [Shopify tags](https://help.shopify.com/en/manual/shopify-admin/productivity-tools/using-tags) to each product that is not available to buy with Cash App Pay.

## Create and Edit Script

### Create the Script in the Editor

Once you have added the tags in steps 2 and/or 3 above, you need to create the script. Do the following::

1. Open the [Script Editor Shopify App](https://apps.shopify.com/script-editor) if it is not already open.

2. Click **Create Script**.

3. Select the _Payment gateways_ tab, then click the **Hide payment gateway** radio button. See picture below:

![hide-checkout-2.png](../../../assets/images/hide-checkout-2.png)

### Edit the Script in the Editor

Use the [Script Editor Shopify App](https://apps.shopify.com/script-editor) to edit the following:

1. Update the _Title_ field.

2. Set _Channels_ radio button to _Online Store only_.

3. Copy and paste the following code snippet into the Ruby source code section:

   ```unset
   no_afterpay = Input.cart.line_items.any? { |line_item| line_item.variant.product.tags.include?('no-afterpay') }

   no_cash_app_pay = Input.cart.line_items.any? { |line_item| line_item.variant.product.tags.include?('no-cash-app-pay') }

   Output.payment_gateways = Input.payment_gateways

   if no_afterpay  
     Output.payment_gateways = Output.payment_gateways.delete_if { |payment_gateway|    payment_gateway.name.include?("Afterpay") }
       end
   if no_cash_app_pay  
   Output.payment_gateways = Output.payment_gateways.delete_if { |payment_gateway|    payment_gateway.name.include?("Cash App Pay") }
   end

   ```

   <!-- theme: info -->

   > **Note**
   >
   > You may need to edit this code snippet depending on your specific site setup and/or the product tags you decide to use for this purpose. This is a Shopify feature, so we (Cash App Afterpay) cannot give specific instructions for all cases and setups.

4. Click the **Save and publish** button.

5. Test the conditional Cash App Afterpay and/or Cash App Pay gateway visibility on selected products on your site's checkout page.

   <!-- theme: warning -->

   > **Important**
   >
   > The script and tags described on this page **do not** apply to draft orders. These draft orders are created when you send the customer an [invoice by email](https://help.shopify.com/en/manual/orders/create-orders#email-invoice). Cash App Afterpay and/or Cash App Pay will appear as payment methods on these invoices.
