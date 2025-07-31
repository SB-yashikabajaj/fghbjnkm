---
stoplight-id: 7h3maff5nagtm
---

# Discount Object
## Attributes
| Attribute   | Type            | Description                                                 |
|-------------|-----------------|-------------------------------------------------------------|
| displayName | required string | A display name for the discount. Limited to 128 characters. |
| amount      | required Money  | The discount amount.                                        |

## Error Response
Returned if an API request is unsuccessful.

| Error | Error Message                                                                       |
|-------|-------------------------------------------------------------------------------------|
| 422   | discounts[0].displayName may not be empty, discounts[0].displayName may not be null |
| 422   | discounts[0].displayName may not be empty                                           |
| 422   | discounts[0].displayName max length is 128                                          |
