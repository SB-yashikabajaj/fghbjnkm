---
stoplight-id: kfg3ya7277208
---

# Consumer Object

## Attributes


| Attribute    | Type            | Description                                                                |
|-------------|-----------------|----------------------------------------------------------------------------|
| phoneNumber | optional string | The customer's phone number. Limited to 32 Characters.                     |
| givenNames  | optional string | The customer's first name and any middle names. Limited to 128 characters. |
| surname     | optional string | The customer’s last name. Limited to 128 characters.                       |
| email       | required string | The customer’s email address. Limited to 128 characters                    |

## Error Response
Returned if a API request is unsuccessful.

| Error | Error Message                                         |
|-------|-------------------------------------------------------|
| 422   | consumer.givenNames max length of given names is 128  |
| 422   | consumer.surname max length of surname is 128         |
| 422   | consumer.email not a well-formed email address        |
| 422   | consumer.phoneNumber max length of phone number is 32 |
| 422   | consumer.email Email address required                 |