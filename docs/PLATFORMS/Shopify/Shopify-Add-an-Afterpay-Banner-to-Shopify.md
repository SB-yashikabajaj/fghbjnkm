---
stoplight-id: m2ny9vhp6kptl
internal: true
---

# Add a Cash App Afterpay Banner to Shopify

Banners display Cash App Afterpay information at the top of your Shopify page, as shown in the images below.

To add a Cash App Afterpay banner, you must edit your store's code. Before proceeding, ensure that:

- The [Afterpay US](https://apps.shopify.com/afterpay-us) payment app is already installed and running on your online store

- You have chosen a banner that aligns with the guidelines

<!-- theme: info -->

> **Recommendation**
>
> You are changing your online store's code, so be careful. We recommend you create a duplicate page and only publish it once you have verified the changes.

## Steps to Add the Banner

1. Click **Actions** and select _Edit Code_ from the drop-down menu.

2. Scroll down to _Sections_ and click **Add a new section**.

3. In the _Create a new section called_ field enter **cash-app-afterpay-banner**. The _cash-app-afterpay-banner.liquid_ tab appears.

4. Delete the code that populates the _cash-app-afterpay-banner.liquid_ tab.

### Add the Liquid file

1. Click the link to the [banner code snippet](https://static.afterpay.com/shopify-cash-app-afterpay-banner-liquid.html).

2. Click the **Copy to Clipboard** button.

3. Paste the banner code snippet into the _cash-app-afterpay-banner.liquid_ tab.

4. Click **Save**.

### Editing the Theme Liquid file

1. Open the `theme-liquid` file.

2. Locate the line {% sections 'header-group' %} or {% section 'header' %}.

3. Add {% section 'cash-app-afterpay-banner' %} above this line. In the example below, it is added to line 4:

   ```
   <div class = "black-body"></div>
   {% section 'popup' %}
   {% section 'announcement-bar' %}
   {% section 'cash-app-afterpay-banner' %}
   {% section 'header' %}
   <div id="PageContainer" class="is-moved-by-drawer">
   ```

4. Click **Save**.

To verify the changes, click **Preview** and check for the banners appearance at the top of the page.

The images below illustrate a white, black, and green banner:

![white-banner-new.png](../../../assets/images/white-banner-new.png)

<br>

![black-banner-new.png](../../../assets/images/black-banner-new.png)

<br>

![green-banner-new.png](../../../assets/images/green-banner-new.png)

### Changing the Banner Color

To change the banner color:

1. Login to your **Shopify Admin** and navigate to your **Theme Settings** page: Go to **Online Store**> **Themes**.

2. Click **Customize** to change the theme with the Cash App Afterpay Banner.

   ![publish-customize.png](../../../assets/images/publish-customize.png)

3. Click **Cash App Afterpay Banner**.

   ![home-page.png](../../../assets/images/home-page.png)

4. Click **Banner color**.

5. Select **Black**, **White**, or **Green**.

   ![shopify-banner-for-caap.png](../../../assets/images/shopify-banner-for-caap.png)

6. Click **Save**.

## Brand Assets

For more examples and information on brand assets, including banners, see the [Brand Assets](../../MARKETING/Brand-Assets.md) section of this guide.
