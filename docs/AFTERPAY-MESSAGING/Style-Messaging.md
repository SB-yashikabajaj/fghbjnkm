---
stoplight-id: vnn9u0hozzxlh
---


# Style Messaging

## Fonts

Cash App Afterpay Messaging inherits the font family that is used to style other paragraph elements on the page. If you would like to use a different font, you may specify it in a CSS (cascading Style Sheet) rule that targets `afterpay-placement`:

```CSS

afterpay-placement {
    font-family: Sans-Serif;
}
```
## Adjust the Size of Cash App Afterpay Messaging

Use the `data-size` attribute to change the font-size of the messaging and also to scale the brand logo.

Accepted values for the `data-size` attribute are: **xs**, **sm**, **md** (default), and **lg**. That is extra small, small, medium and large.

To scale the messaging elements beyond these standard options provided by the `data-size` attribute, use the following custom CSS properties:

- `--logo-badge-width`: To change the size of the brand logo only (badge)

- `--messaging-font-size`: To set the font-size of the textual part of the messaging to a custom value

See the code example below:

```CSS

afterpay-placement { 
 --messaging-font-size: 10px; 
 --logo-badge-width: 70px; /* Must be >= 64px */ 
}
```
To ensure your customizations align with our brand guidelines see our [Brand Assets](../MARKETING/Brand-Assets.md) page. 
