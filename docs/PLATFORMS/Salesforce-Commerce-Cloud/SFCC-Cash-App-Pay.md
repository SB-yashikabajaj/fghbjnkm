---
stoplight-id: 8bamv23ub3z2g
---

# SFCC Cash App Pay

Follow the instructions in this topic to enable Cash App Pay along with Afterpay as a payment method on your checkout page. At present, Cash App Pay is only available to US merchants. 



> If you have version 23.2.0 of the Afterpay cartridge installed, go direct to the [Enable Cash App Pay](#enable-cash-app-pay) section of this page to enable Cash App Pay. 
> 
> If you are on version 22.0.0 of the Afterpay cartridge, read through all the sections on this page.

For US merchants, Afterpay provides access to Cash App Pay through its cartridges for the [Salesforce Commerce Cloud](https://github.com/afterpay/afterpay-salesforce-commerce-cloud). There are two of these cartridges depending on the type of Salesforce Commerce Cloud you have:

- Salesforce Reference Architecture (SFRA)

- SiteGenesis

<!-- theme: warning -->
> You must have Afterpay Cartridge 22.0.0 and have Cash App Pay enabled on your Afterpay Merchant Account before you attempt to enable Cash App Pay on either cartridge. Remember this functionality is only available for US based merchants.


## Upgrade guides

You can download detailed upgrade documentation on both cartridges:

- [Version 23.2.0 for Salesforce Commerce Cloud - SFRA](https://github.com/afterpay/afterpay-salesforce-commerce-cloud/blob/main/documentation/Upgrade%20Guide/Cash%20App%20Pay/Cash%20App%20Pay%20V23.4.0%20Upgrade%20Guide%20SFRA.docx)

- [Version 23.2.0 for Salesforce Commerce Cloud - SiteGenesis](https://github.com/afterpay/afterpay-salesforce-commerce-cloud/blob/main/documentation/Upgrade%20Guide/Cash%20App%20Pay/Cash%20App%20Pay%20V23.4.0%20Upgrade%20Guide%20SiteGenesis.docx)

## Enable Cash App Pay

After you install the cartridge, a new configuration option appears in the Business Manager. Do the following:

1. In the Business Manager, go to **Merchant Tools** > **Site Preferences** > **Custom Preferences** > **Integration_Afterpay**.

2. Set the `enableCashAppPay` site preference to **True**. See table below.


Site Preference | Description | Default
---------|----------|---------
 Enable CashAppPay `enableCashAppPay` | The field determines if the Cash App Pay is enabled/disabled in the cartridge. | False

<!-- theme: warning -->
> If you set the `enableCashAppPay` preference to **True**, ensure that:
> - Cash App integration is enabled for you in the portal 
> - Enable Afterpay is also set to **True**. Cash App Pay will not load unless Afterpay is also enabled.
