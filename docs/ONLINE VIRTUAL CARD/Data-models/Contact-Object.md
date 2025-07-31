---
stoplight-id: mwlxpj40wo7wk
---

# Contact Object

## Attributes
| Attribute   | Type               | Description                                                                                    |
|-------------|--------------------|------------------------------------------------------------------------------------------------|
| name        | required string    | Full name of contact. Limited to 255 characters.                                               |
| line1       | required string    | First line of the address. Limited to 128 characters                                           |
| line2       | optional string    | Second line of the address. Limited to 128 characters.                                         |
| area1       | recommended string | AU: Suburb<br> NZ: Town or city<br> UK: Postal town <br>US: City <br>CA: City  <br><br>Limited to 128 characters       |
| area2       | optional string    | New Zealand suburb or U.K. village or local area. <br><br>Limited to 128 characters                    |
| region      | required string    | AU: State <br>NZ: Region<br> UK: County<br> US: State <br>CA: Province or Territory  <br><br>Limited to 128 characters |
| postcode    | required string    | Zip or Postal code. Limited to 128 characters.                                                 |
| countryCode | recommended string | The two-characters ISO 3166-1 Country code.                                                    |
| phoneNumber | optional string    | The phone number, in [E.123](https://en.wikipedia.org/wiki/E.123) format. Limited to 32 characters.                                   |

## Error Response
Returned if an API request is unsuccessful.

| Error | Error Message                                                                                            |
|-------|----------------------------------------------------------------------------------------------------------|
| 422   | billing.name address name is required                                                                    |
| 422   | billing.name max length of name is 255                                                                   |
| 422   | billing.line1 address line one is required.                                                              |
| 422   | billing.line1 max length of address line1 is 128                                                         |
| 422   | billing.postcode Postcode is required.                                                                   |
| 422   | shipping.postcode max length of postcode is 128                                                          |
| 422   | billing.countryCode Valid Country Code is required.                                                      |
| 422   | billing.countryCode max length of country code is 2, billing.countryCode Valid Country Code is required. |
| 422   | billing.name address name is required., billing.line1 address line one is required.                      |