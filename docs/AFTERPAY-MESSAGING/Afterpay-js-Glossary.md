---
stoplight-id: gep3h3ipkfznq
---

# Afterpay.js Glossary

## Constants

<CONSTANT_NAME> | Values|
---------|----------|
`currency`| `USD` |
`locale` | `EN_GB` |
`logoType`| `BADGE`, `LOCKUP` |
`modalLinkStyle` | `CIRCLED_INFO_ICON`, `LEARN_MORE_TEXT`, `MORE_INFO_TEXT`, `CIRCLED_QUESTION_ICON`, `NONE` |
`placementTypes` | `PRICE_TABLE`
`size` | `XS`, `SM`, `MD`, `LG`
`mobileViewLayout` | `FOUR_BY_ONE`, `TWO_BY_TWO`
`theme.`**badge** | `BLACK_ON_MINT`, `BLACK_ON_WHITE`, `MINT_ON_BLACK`, `WHITE_ON_BLACK`
`theme.`**lockup** | `BLACK`, `WHITE`, `MINT`
`theme.`**modal** | `WHITE`
`theme.`**priceTable** | `BLACK`, `WHITE`

### Using Cash App Afterpay Constants

Constants are exposed to the window through the Cash App Afterpay object Afterpay.\<constant_name>.

See some examples below:

```javascript
console.log(Afterpay.locale.EN_US) //  "en_US" 
console.log(Afterpay.theme.lockup) //  "{"BLACK":"black","WHITE":"white","MINT":"mint"}"
console.log(Afterpay.theme.lockup.BLACK) //  "black"
```

## Functions

Name | Description |
---------|----------|
`createPlacements` | Adds one or more placements to the page using the `targetSelector` attribute.|
`launchModal` | Dynamically open the Clearpay Modal. |
`ready`| Custom Window Event dispatched when `Afterpay.js` is successfully initialized. |
`modalRenderComplete` | Custom Window Event dispatched when the `<afterpay-modal>` finishes rendering.

## Window Events

Name | Description |
---------|---------|
`ready` | Custom Window Event dispatched when `Afterpay.js` is successfully initialized. |
`modalRenderComplete` | Custom Window Event dispatched when the `<afterpay-modal>` finishes rendering |