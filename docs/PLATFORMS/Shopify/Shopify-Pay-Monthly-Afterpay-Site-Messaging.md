---
stoplight-id: vhnqa9v6qsqfv
---

# Shopify Pay Monthly Afterpay Site Messaging

## Pay Monthly

If you are, or want to be a Pay Monthly user, this section describes the special steps you need to take to install Afterpay site messaging.

<!--theme: info-->
> **Note**
>
> At present, Pay Monthly specific Afterpay site messaging is only available to Shopify merchants through Shopify Snippet. It is not available through the Afterpay On-Site Messaging app.

### New Merchant with No Afterpay Site Messaging

If you are new to Pay Monthly and so far have not implemented any Afterpay site messaging, do the following:

1. Copy the code below to your clipboard, a **Copy to Clipboard** icon makes this easy:
    ```json
    <!-- Begin Shopify-Afterpay JavaScript Snippet (v1.2.0) -->
    {% if cart.currency.iso_code == shop.currency %}
    <script type="text/javascript">
    // Overrides:
    var afterpay_apr_loans_available = true;

    // Non-editable fields:
    var afterpay_js_language = {{ localization.language.iso_code | slice: 0, 2 | json }};
    var afterpay_js_country = {{ localization.country.iso_code | json }};
    var afterpay_shop_currency = {{ shop.currency | json }};
    var afterpay_cart_currency = {{ cart.currency.iso_code | json }};
    var afterpay_shop_money_format = {{ shop.money_format | json }};
    var afterpay_shop_permanent_domain = {{ shop.permanent_domain | json }};
    var afterpay_theme_name = {{ theme.name | json }};
    var afterpay_product = {{ product | json }};
    var afterpay_current_variant = {{ product.selected_or_first_available_variant | json }};
    var afterpay_cart_total_price = {{ cart.total_price | json }};
    var afterpay_js_snippet_version = '1.2.0';
    </script>
    <script type="text/javascript" src="https://static.afterpay.com/shopify-afterpay-javascript.js"></script>
    {% else %}
    <!-- Afterpay disabled: {{ cart.currency.iso_code }} != {{ shop.currency }} -->
    {% endif %}
    <!-- End Shopify-Afterpay JavaScript Snippet (v1.2.0) -->
    ```

2. Log in to [Shopify Admin](https://accounts.shopify.com/lookup?rid=edf4fd64-060c-48a7-bf95-095eb87b831c).

3. Navigate to **Themes**. To do this, go to **Sales channels** > **Online Store** > **Themes**.

    ![shopify-ap-site-mess-1.png](../../../assets/images/shopify-ap-site-mess-1.png)

4. Navigate to the current theme, then go to **Actions** > **edit code**.

    ![shop-ap-site-mess-2.png](../../../assets/images/shop-ap-site-mess-2.png)

5. Under the **Layout** folder, click **theme.liquid**.
   
    ![step5.png](../../../assets/images/Step_5.png)

6. Scroll to the bottom of the `theme.liquid` file.

    ![step5.png](../../../assets/images/Step_6.png)

7. Paste the copied text (Step 1), at the bottom of the `theme.liquid` file.

    ![Pay-Monthly-shopify.jpeg](../../../assets/images/Pay-Monthly-shopify.jpeg)

8. Click **Save**, and go to the website to review the product and cart pages for Afterpay assets.

### Existing Merchant who uses Afterpay Site Messaging

To add Afterpay site messaging to your Pay Monthly offering, add an override to the `theme.liquid` file:

1. Follow all the Configuration steps above, from step 1 to step 7.

2. Locate the `theme.liquid` file.

3. Add the following override above the Non-editable fields: `var afterpay_apr_loans_available = true`

4. Follow step 8 as normal.

<!-- theme: info -->
> **Note**
>
> Shopify have a help topic on editing Liquid files [here](https://shopify.dev/docs/api/liquid).
