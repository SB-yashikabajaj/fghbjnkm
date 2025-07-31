---
stoplight-id: 4h9mtqi5cr7g1
---

# On-Site Messaging Migration
Your existing Afterpay messaging will automatically map to the new Cash App Afterpay branding. The themes will transition automatically based on your current selections. All existing integration code will continue to work; no action is required unless you want to change themes.
 

These changes only apply to merchants in the US.

<!-- theme: info-->
> Background color detection afffects some asset themes. If background color dependency is marked "Yes," it means you'll see a light variant on a light background, and a dark variant on a dark background.

### Messaging assets mapping

<!-- theme: info-->
>Badge configurations also apply to the compact badge 


| Asset Type | Configuration | Afterpay Theme | Before | Cash App Afterpay Theme | After | Background Color Dependency |
|------------|--------------|----------------|--------|----------------------|-------|---------------------------|
| Default Lockup | `"logoType": "lockup"` | Black lockup | <img src="../../assets/images/Afterpay_Logo_Black.png" style="all: unset; width: 100px;" /> | Mono light | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black_Monochrome.png" style="all: unset; width: 100px;" /> | No |
| Lockup - Mint | `"logoType": "lockup", "lockupTheme": "mint"` | Mint lockup | <img src="../../assets/images/Afterpay_Logo_Mint.png" style="all: unset; width: 100px;" /> | Color - Light variant OR Dark variant | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black.png" style="all: unset; width: 100px;" /> or <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White (1).png" style="all: unset; width: 100px;" /> | Yes |
| Lockup - White | `"logoType": "lockup", "lockupTheme": "white"` | White lockup | <img src="../../assets/images/Afterpay_Logo_White.png" style="all: unset; width: 100px;" /> | Mono dark | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White_Monochrome (1).png" style="all: unset; width: 100px;" /> | No |
| Lockup - Black | `"logoType": "lockup", "lockupTheme": "black"` | Black lockup | <img src="../../assets/images/Afterpay_Logo_Black.png" style="all: unset; width: 100px;" /> | Mono light | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black_Monochrome.png" style="all: unset; width: 100px;" /> | No |
| Badge Default | `"logoType": "badge"` | Black on mint badge | <img src="../../assets/images/Afterpay_Badge_BlackonMint.jpg" style="all: unset; width: 100px;" /> | Color - Light variant OR Dark variant | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black.png" style="all: unset; width: 100px;" /> or <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White (1).png" style="all: unset; width: 100px;" /> | Yes |
| Badge - Black on Mint | `"logoType": "badge", "badgeTheme": "black-on-mint"` | Black on mint badge |<img src="../../assets/images/Afterpay_Badge_BlackonMint.jpg" style="all: unset; width: 100px;" />| Color - Light variant OR Dark variant | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black.png" style="all: unset; width: 100px;" /> or <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White (1).png" style="all: unset; width: 100px;" /> | Yes |
| Badge - Mint on Black | `"logoType": "badge", "badgeTheme": "mint-on-black"` | Mint on black badge | <img src="../../assets/images/Afterpay_Badge_MintonBlack.png" style="all: unset; width: 100px;" /> | Color - Light variant OR Dark variant | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black.png" style="all: unset; width: 100px;" /> or <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White (1).png" style="all: unset; width: 100px;" /> | Yes |
| Badge - White on Black | `"logoType": "badge", "badgeTheme": "white-on-black"` | White on black badge | <img src="../../assets/images/Afterpay_Badge_WhiteonBlack.png" style="all: unset; width: 100px;" /> | Mono - Dark variant OR Light variant | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black_Monochrome.png" style="all: unset; width: 100px;" /> or <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White_Monochrome (1).png" style="all: unset; width: 100px;" /> | Yes |
| Badge - Black on White | `"logoType": "badge", "badgeTheme": "black-on-white"` | Black on white badge | <img src="../../assets/images/Afterpay_Badge_BlackonWhite.png" style="all: unset; width: 100px;" /> | Mono - Dark variant OR Light variant | <img src="../../assets/images/RGB_CashAppAfterpay_Logo_Black_Monochrome.png" style="all: unset; width: 100px;" /> or <img src="../../assets/images/RGB_CashAppAfterpay_Logo_White_Monochrome (1).png" style="all: unset; width: 100px;" /> | Yes |


### Modal assets mapping

| Asset Type | Configuration | Afterpay Modal | Before | Cash App Afterpay Modal | After | Background Color Dependency |
|------------|--------------|----------------|--------|------------------------|-------|---------------------------|
| Mint Modal | `"modalTheme": "mint"` | Mint Modal | <img src="../../assets/images/Afterpay_Mint_Modal.png" style="all: unset; width: 100px;" /> | Standard Cash App Afterpay Modal | <img src="../../assets/images/CashAppAfterpay_Modal.png" style="all: unset; width: 100px;" /> | No |
| White Modal | `"modalTheme": "white"` | White Modal | <img src="../../assets/images/Afterpay_White_ Modal.png" style="all: unset; width: 100px;" /> | Standard Cash App Afterpay Modal | <img src="../../assets/images/CashAppAfterpay_Modal.png" style="all: unset; width: 100px;" /> | No |


### Icon assets mapping

| Asset Type | Configuration | Afterpay Icon | Before | Cash App Afterpay Icon | After | Background Color Dependency |
|------------|--------------|---------------|--------|---------------------|-------|---------------------------|
| Icon | `"data-type": "icon"` | Afterpay Icon | <img src="../../assets/images/Afterpay_Icon.png" style="all: unset; width: 50px;" /> | Cash App Afterpay Icon | <img src="../../assets/images/CashApp_PaymentBadge_Green.png" style="all: unset; width: 50px;" />  | No |