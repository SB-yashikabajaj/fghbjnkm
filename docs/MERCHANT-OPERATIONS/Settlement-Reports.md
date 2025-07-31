---
stoplight-id: r99735389lnto
---
# Settlement Reports

**How Can I View Settlement Reports?**
---

Settlement Reports explain in detail all payments made by Cash App Afterpay to you and help you to reconcile your accounts. There is one settlement report for each settlement to your bank account. Typically, there is one settlement every day that you capture a Cash App Afterpay order.

See also: [Settlement Timing](Getting-Paid.md)

## Viewing Settlement Reports

You can view and export your settlement files in the [Reconciliation tab](https://hub.us.afterpay.com/us) of the Business Hub.

<!-- 
focus: false 
-->
![Viewing Settlement Reports.png](<../../assets/images/Viewing Settlement Reports-3.png>)

## Downloading the Settlement Report

You can export your settlement files by using the Settlement Export option from your Reconciliation tab. For additional download options, such as API requests, contact your account manager.

<!-- 
focus: false 
-->
![Downloading the Settlement Report.png](<../../assets/images/Downloading the Settlement Report-3.png>)

## Settlement Report Fields
|Description|	Type|	Format|	Example Value| Displayed in CSV Format |
|--|--|--|--|--
|Settlement Date|	String|	See table below|	See table below	|See table below|
|Order Date and Time	|String	|dd/MM/yyyy HH:mm	|12/01/2018 10:43	|"24/06/2019 22:56"|
|Order Month	|String|	MMM	|Jan|	"Jun"|
|Order Year|	String|	|	2019|	"2019"|
|Afterpay Order ID|	Number	|79043810	|12345679	|"79169085"|
|Merchant Order ID|	String|	Merchant Supplied	|2345678	|"2345678"|
|Merchant Refund ID	|String	|Merchant Supplied	|9163251003631241	|"9163251003631241"|
|Order Amount	|String|	$00.00 or $0.00	|$85.95	|"85.95" - with the currency symbol before the number|
|Settlement Amount|	String|	$00.00 or $0.00	|$85.95	|"85.95" - with the currency symbol before the number|
|Merchant Fee excl Tax	|String|	$00.00 or $0.00|	$5.46|	"5.46" - with the currency symbol before the number|
|Merchant Fee Tax	|String|	$00.00 or $0.00	|$0.55|	"0.55" - with the currency symbol before the number|
|Merchant Fee incl Tax	|String	|$00.00 or $0.00|	$6.00|	"6.00" - with the currency symbol before the number|
|Net Settlement Amount	|String|	$00.00 or $0.00|	$79.95|	"79.95" - with the currency symbol before the number|
|Type | String|	|	Order|	"Order"|
|Channel | String | | Online | "Online" |
|Store Name	|String| | |	|
|Store Id	|		| |	 | 9756|
|Device Name	|		| |	 |	"POS251"|
|Device Id	|		| |	 |38301|
|Afterpay Refund ID	|Number				| |	 |4561545|
|Refund Date and Time	|String	|dd/MM/yyyy HH:mm|	|	"24/06/2019 18:43"|
|Acquirer Terminal ID		|		||||
|Consumer Country |String|		| |"US"|
