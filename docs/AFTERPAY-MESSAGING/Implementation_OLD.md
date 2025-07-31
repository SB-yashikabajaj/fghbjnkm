---
stoplight-id: 2pt2vd9z4wp24
---

# Implementation

*How to implement on-site messaging.*

## Messaging Installation

On-Site Messaging adds pay-over-time messaging to your store’s website. For example, in the picture below the messaging is:

_4 payments of $25.00 with Cash App Afterpay_ 
_Learn more_

<!--
focus: false
-->
![Product page messaging.png](<../../assets/images/Product page messaging-2.png>)


Updates to the messaging are automatic, and a specific set of messaging logic is designed for your products (Pay in 4, Pay Monthly, etc). Use our On-Site Messaging Tool to see message previews and the WYSIWYG (What You See Is What You Get) tool to customize and manage your messaging.

## Requirements

To use this On-site Messaging feature you must:

- Be an existing Cash App Afterpay merchant

- Have a direct integration with Cash App Afterpay

- Have at least one retail website live and ready for use, although a Sandbox environment is available for testing without a retail website

<!-- theme: info -->

> **Note**
>
> If you already have Cash App Afterpay Messaging through the JavaScript library, we recommend you replace these with On-Site Messaging instead. See the [Migration page](Migration.md) for details.

## Sandbox Test Environment

We recommend that you use the Sandbox On-Site Messaging portal to review the Cash App Afterpay messaging on your store before you go live.

To test, you will need access to the Sandbox Portal and a set of Sandbox credentials. Click the links below for these:

* [Sandbox On-Site Messaging Portal](https://messaging-us-sbox.afterpay-beta.com/) 

* [Sandbox credentials](../API-DEVELOPMENT/Test-Environment-Sandbox.md)

The suggested tests are:

* Run through the Cash App Afterpay payment flow. Check how your messaging appears at various points in the customer journey. For example, the product page and the shopping cart

* Check that you meet Cassh App Afterpay's technical and compliance requirements before you deploy live

* Experiment with different customisations so you can choose the best option for messaging on your store and products. Remember to keep within Cash App Afterpay guidelines

### Sandbox On-Site Messaging - Quickstart Guide

1. From the [Sandbox On-Site Messaging Portal](https://messaging-us-sbox.afterpay-beta.com/) go to the *Placements* page. See picture below:

    <!--
    focus: false
    -->
    ![Placements.png](../../assets/images/Placements.png)

2. Select the Product/Cart page to customise your messaging from the options available.

3. Click the *Implementation guide* tab and follow the instructions there to set up messaging. See picture below:

    <!--
    focus: false
    -->
    ![Implementation guide.png](<../../assets/images/Implementation guide.png>)

4. Check the product page and cart page to see what your messaging looks like. From the *Placements* page, you can make adjustments to the logo, text size and theme.

5. Visit the *Settings* page to review and configure overall messaging settings. These could include changes to your wording, or how messaging appears on products and orders that are unavailable through Cash App Afterpay. See the picture below:

    <!--
    focus: false
    -->
    ![Settings.png](../../assets/images/Settings.png)

6. When you are satisfied with your testing, you're ready to go to the live [On-Site Messaging Portal](https://messaging.afterpay.com/login). From this portal you can configure Cash App Afterpay messaging for the live system. The information on the rest of this page helps you do that. 

## Add the Messaging Widget to your website

These instructions assume that you are installing messaging for the first time on a production (live) site. Your system does not already feature messaging. If you already have messaging, go to the [Migration page](Migration.md) and follow the instructions there.

To add messaging for the first time:

1. Go to the [Cash App Afterpay Messaging website](http://messaging.afterpay.com/) and log-in with your Merchant ID (MID) and Secret Key.

![image6.png](../../assets/images/image6.png)

2. Open the [Implementation Guide](https://messaging.afterpay.com/editor/implementation-guide) and follow the instructions.

3. Put the script tag in the head section of the codebase. See the _Step 1 - Add script tag to head section_ in the screenshot below step 4.

4. Configure the code snippets for the Product page and the Cart page snippets. See the _Step 2 - Product page_ and _Step 3 Cart page_ in the screenshot below.

![add-mess-widget.png](../../assets/images/add-mess-widget.png)

5. To display installment messaging, add the `<square-placement>` tag to the product page HTML files. Place the messaging immediately below the price element of the product.

6. Set the `data-amount` with the amount that appears on the page to calculate the installments. Keep the `data-mpid` and `data-placement-id` attributes in place with their current values unchanged.

7. Set the `data-currency` to the customer’s currency and `data-consumer-locale` to the customer’s country.

8. Set `data-item-skus` to any unique product identifier you use, provided as a string. If you have multiple products in the cart, separate them with a comma.

9. Set `data-item-categories` as one or more category names for the relevant product. This is provided as a string or for multiple categories, separate them with a comma.

10. To restrict a product from sale with Cash App Afterpay, set the `data-is-eligible` attribute to false. To restrict a cart from sale with Cash App Afterpay, set the `data-cart-is-eligible` attribute to false. This is optional.

## Customizing Messaging

You can customize the messaging so it fits your products and your web page design. To do this on a production (live) site:

1. Go to the [Cash App Afterpay Messaging website](http://messaging.afterpay.com/) and log-in with your Merchant ID (MID) and Secret Key.

2. On the home page, select the Product page or the Cart page placement card.

In the picture below, the user has selected the Product page.

![image4.png](../../assets/images/image4-2.png)

- Make configuration changes to the Product page and the Cart page in their placements on the homepage. More advanced configurations are under _Settings_.

- The tool is WYSIWYG, so the preview accurately shows the effect of any changes you make.

- You can customize multiple pages. When you are finished, click **Save all changes**. Your changes are updated automatically on your website (there could be up to 5 minutes of delay), provided that the code has been implemented.
