---
stoplight-id: fis6mbzpmiytn
---

# Item Object

## Attributes
| Attribute  | Type             | Description                                                                                                                                                                                             |
|------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| name       | required string  | Product name. Limited to 255 characters.                                                                                                                                                                |
| sku        | optional string  | Product SKU. Limited to 128 characters.                                                                                                                                                                 |
| quantity   | required integer | The quantity of the item, stored as a signed 32-bit integer.                                                                                                                                            |
| pageUrl    | required string  | The canonical URL for the item's Product Detail Page. Limited to 2048 characters.                                                                                                                       |
| imageUrl   | optional sting   | A URL for a web-optimised photo of the item, suitable for use directly as the src attribute of an img tag. Limited to 2048 characters.                                                                  |
| price      | required Money   | The unit price of the individual item. Must be a positive value.                                                                                                                                        |
| categories | optional Array   | An array of arrays to accommodate multiple categories that apply to the item. Each array represents a hierarchical path to a category, with the left-most category being the top-level parent category. |


## Error Response
Returned if an API request is unsuccessful.

| Error | Error Message                                                 |
|-------|---------------------------------------------------------------|
| 422   | items[0].name may not be empty, items[0].name may not be null |
| 422   | items[0].name may not be empty                                |
| 422   | items[0].name max length of item name is 255                  |
| 422   | items[0].sku max length of item sku is 128                    |
| 422   | items[0].quantity may not be null                             |
| 422   | items[0].pageUrl may not be null                              |
| 422   | items[0].price may not be null                                |
| 400   | The request contains improperly formatted JSON                |
