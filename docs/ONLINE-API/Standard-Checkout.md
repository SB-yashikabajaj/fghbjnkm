---
stoplight-id: pipq3y5nx0wwx
---

# Standard Checkout

**JavaScript afterpay.js**

## Production - All Regions

`https://portal.afterpay.com/afterpay.js`

## Sandbox - All Regions

`https://portal.sandbox.afterpay.com/afterpay.js`

The `afterpay.js` launches the Cash App Afterpay screenflow, where the customer logs in, or registers, then confirms their payment schedule.

<!--theme: info-->
>**Note**
>
> Before you can use this JavaScript, you, the merchant, must call [Create Checkout](../../reference/Checkouts.v2.yaml/paths/~1v2~1checkouts/post) from your server backend and retrieve a checkout token. The token is then used in conjunction with this JavaScript to launch the Cash App Afterpay screenflow.
>
> It is only after the customer completes the Cash App Afterpay screenflow and returns to your website that a subsequent Auth or Capture (Without Auth) call can be completed.


## Redirect Method

The Redirect Method is the standard method used by most merchants. This method redirects the customer away from your website to Cash App Afterpay to complete the payment. At the end of the process, the customer is redirected back to your website.

- If the customer clicks **Confirm**, they are redirected to the `redirectConfirmUrl`, with the `orderToken` and a `status` of **SUCCESS** appended as HTTP query parameters

- If the customer cancels, they are redirected to the `redirectCancelUrl`, with the `orderToken` and a `status` of **CANCELLED** appended as HTTP query parameters

<!--theme: info-->
>**Note**
>
> You, the merchant, defines the `redirectConfirmUrl` and `redirectCancelUrl` for each order in the [Create Checkout](../../reference/Checkouts.v2.yaml/paths/~1v2~1checkouts/post) call.

To implement the Redirect Method, call the following two JavaScript functions, in order:

1. `AfterPay.initialize` - This prepares the Cash App Afterpay JavaScript to start the Cash App Afterpay screenflow in the appropriate geographical region. This function accepts one required argument: an object with a required `countryCode` property. This property must contain the two-character [ISO 3166-1](https://en.wikipedia.org/wiki/ISO_3166-1) country code of the merchant account. For Cash App Afterpay, code must be US.

2. `AfterPay.redirect` - This redirects the customer's browser from your website to Cash App Afterpay. This function accepts one required argument: an object with a required `token` property. This property must contain the checkout token returned by [Create Checkout](../../reference/Checkouts.v2.yaml/paths/~1v2~1checkouts/post).

```HTML

<html>
<head>
  <script onload="initAfterPay()" src="https://portal.sandbox.afterpay.com/afterpay.js"></script>
</head>
<body>
  <p>Your HTML here</p>
  <script>
  function initAfterPay () {
    AfterPay.initialize({countryCode: "AU"});
    AfterPay.redirect({token: "YOUR_TOKEN"});
  }
  </script>
</body>
</html>
```

<!--theme: success-->
> **Recommendation** 
>
> Try using your Sandbox merchant credentials to get a token from [Create Checkout](../../reference/Checkouts.v2.yaml/paths/~1v2~1checkouts/post). Then use this token to test the Cash App  Afterpay screenflow on JSFiddle: https://jsfiddle.net/afterpay/cyd3pxfj/
> <br/><br/>Be aware that as JSFiddle loads the Cash App Afterpay screenflow inside a frameset, the login and redirect features will not work.

## Popup Method

You can use the Popup Method to open the Cash App Afterpay screenflow in a new browser window. 

For windowed applications, the merchant website is overlaid with a semi-transparent curtain, with the Cash App Afterpay window on top. For fullscreen applications, found on mobile devices, the browser switches to a new tab for the Cash App Afterpay window. 

In any case, the customer completes the Cash App Afterpay screenflow as they would if the **Redirect Method** was used. The main difference occurs when the payment is complete. A redirect to a URL on the merchant website with additional query parameters appended does not occur. Instead, Cash App Afterpay uses a `postMessage` to call a JavaScript method on the merchant's front end.

- If the customer clicks **Confirm**, Cash App Afterpay calls the `onComplete` method on the merchant website. Cash App Afterpay passes the `orderToken` and a `status` of **SUCCESS** as properties of a data object. The popup then closes

- If the customer cancels, Cash App Afterpay calls the `onComplete` method on the merchant website. Cash App Afterpay passes the `orderToken` and a `status` of **CANCELLED** as properties of a data object. The popup then closes

<!--theme: info-->
> **Note**
>
> Although this method does not redirect the customer to the `redirectConfirmUrl` or `redirectCancelUrl`, these fields are still required by [Create Checkout](../../reference/Checkouts.v2.yaml/paths/~1v2~1checkouts/post). These fields are used for context on `postMessage`.
> <br/><br/>At the time of screenflow completion, the protocol, host and port of the opening window may not match those provided in [Create Checkout](../../reference/Checkouts.v2.yaml/paths/~1v2~1checkouts/post). In this case the customer's browser will not dispatch the JavaScript event for security reasons.

```HTML
<html>
<head>
  <script type="text/javascript" src="https://portal.sandbox.afterpay.com/afterpay.js"></script>
</head>
<body>
  <button id="afterpay-button">
    Afterpay it!
  </button>
  <script type="text/javascript">
    document.getElementById("afterpay-button").addEventListener("click", function() {
      AfterPay.initialize({countryCode: "AU"});
      // To avoid triggering browser anti-popup rules, the AfterPay.open()
      // function must be directly called inside the click event listener
      AfterPay.open();
      // If you don't already have a checkout token at this point, you can
      // AJAX to your backend to retrieve one here. The spinning animation
      // will continue until `AfterPay.transfer` is called.
      // If you fail to get a token you can call AfterPay.close()
      AfterPay.onComplete = function(event) {
        if (event.data.status == "SUCCESS") {
          // The customer confirmed the payment schedule.
          // The token is now ready to be captured from your server backend.
        } else {
          // The customer cancelled the payment or closed the popup window.
        }
      }
      AfterPay.transfer({token: "YOUR_TOKEN"});
    });
  </script>
</body>
</html>
```