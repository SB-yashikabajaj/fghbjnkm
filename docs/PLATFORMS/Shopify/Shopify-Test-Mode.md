---
stoplight-id: gni27t6mritxn
---

# Shopify Test Mode

The Afterpay US payment app on Shopify supports a Test Mode. This means you are able to mock all supported transactions including:

* Authorizations
* Captures
* Voids
* Refunds

There are the following sections on this page:

* [Enable test mode for Afterpay US](#enable-test-mode-for-afterpay-us)

* [How do I know if Sandbox is enabled](#how-do-i-know-if-sandbox-is-enabled)

* [How to create a test order](#how-to-create-a-test-order)

* [Enable test mode for Cash App Pay](#enable-test-mode-for-cash-app-pay)

<!--theme: warning -->
> **Warning**
>
> Do not enable test mode on your live site. Once the payment method is activated in the store settings, it is live for customers to use. Only use a staging or development Shopify store for testing.

## Enable test mode for Afterpay US

<!---theme: info-->
>**Note**
> 
> Before you enable Test Mode, please complete the initial Afterpay US configuration. To do this, follow the steps to [Add Cash App Afterpay at Checkout](Shopify-Add-Payment-Option.md) to verify your merchant account in the Business Hub.

To enable the test mode for Afterpay US:

1. From your [Shopify admin](https://www.shopify.com/login), go to *Settings* > *Payments*.

2. In the *Additional payment methods* section, click **Afterpay US (New)**.

3. In the *Test mode* section, turn the toggle on. See the screenshot below:
    ![AfterpayUS_testmode.png](../../../assets/images/AfterpayUS_testmode.png)

4. Click **Save**.

You're now ready to test Afterpay US transactions in your dedicated test store.


## How do I know if Sandbox is enabled

To check if Sandbox has been configured correctly, go to your test site and conduct a test transaction. Once it has been redirected to the Cash App Afterpay Login page, check the URL and it should be a Sandbox URL.

For example:

`portal.sandbox.afterpay.com/v2/checkout/en-AU/password`

## How to create a test order

For Cash App Afterpay transactions, follow the instructions [here](../../API-DEVELOPMENT/Customer-Accounts.md) to create a sandbox customer account and mock various transaction approval outcomes.

For Cash App Pay transactions, creating test orders involves slightly different steps for desktop and mobile views. 

* On desktop, you're taken to a page that displays a Cash App Pay QR Code. Scan this QR Code with your mobile device to decide whether to accept or decline the test order 

* On mobile, you're automatically sent to a page where you can directly choose to accept or decline the test order

## Enable test mode for Cash App Pay

<!---theme: info-->
>**Note**
> 
> Before you enable Test Mode, please complete the initial Cash App Pay application configuration. To do this, follow the steps to [Add Cash App Pay at Checkout](Shopify-Cash-App-Pay-Integration.md) and use your production merchant credentials (Production Merchant ID and Production Secret Key). Once the Cash App Pay application is configured using your production merchant credentials, follow the steps below to enable the test mode for Cash App Pay.

To test a Cash App Pay integration, do the following:

1. From your [Shopify admin](https://www.shopify.com/login), go to *Settings* > *Payments*.

2. In the *Additional payment methods* section, click **Cash App Pay**.

3. In the *Test Mode* section, click the toggle on. See the picture below:

    ![cap-shopify-payment-app-test-2-small.png](../../../assets/images/cap-shopify-payment-app-test-2-small.png)

4. On the initial Cash App Pay setup screen, click **Test Mode**.

   ![Shopify-Test-mode.png](../../../assets/images/Shopify-Test-mode-2.png)

5. On the *Test Mode* screen, enter your sandbox credentials.

6. Enter your Cash App Afterpay Sandbox merchant ID in the *Sandbox Merchant ID* field.

7. Enter your Cash App Afterpay Sandbox secret key in the *Sandbox Secret Key* field.<br>

8. Click **Continue**.

![Shopify-Test-mode-success.png](../../../assets/images/Shopify-Test-mode-success-2.png)

Your store is now ready to mock Cash App Pay transactions with your Sandbox credentials.