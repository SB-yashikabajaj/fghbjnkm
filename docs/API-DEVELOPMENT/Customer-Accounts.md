---
stoplight-id: ja09m34kc639h
---



# Customer Accounts

**How do I place test transactions within the Sandbox Environment?**

---

When checking out on the test site, use the below details to place a test Cash App Afterpay transaction.

## Test Customer Accounts

You can create test customer accounts in the Sandbox environment within your test checkout flow. 

Each Sandbox customer account requires a unique email and a unique phone number.

<!-- theme: danger -->
> **Warning**
>
> No SMS (Short Message Service) text notifications with six-digit verification codes are sent in the Sandbox. Instead, use 111111 as the verification code.

## Test Credit Cards

The Sandbox Capture response (approved / declined) is determined by the CVV value. Use `000` for approval and `051` for decline.

|Card Type|	Card Number|	Expiry	|CCV	|Response|
|---|----|--|--|--|
| Visa | 4111 1111 1111 1111 |	01/28 |	000	| Approved |
| Visa | 4111 1111 1111 1111	| 01/28	| 051	| Declined |
| Mastercard | 5215 0977 9282 6659 | 01/28 | 000 | Approved |
| Mastercard | 5215 0977 9282 6659 | 01/28 | 051 | Declined |

You can use any dummy Visa or Mastercard number and future expiry date for testing purposes in the Cash App Afterpay Sandbox. This is true provided that the number passes a mod 10 check and has not already been used by a different Sandbox customer account.

## Test Pay Monthly

The Sandbox Pay Monthly Approval response (approved/declined) is determined by the Cart Total value.

|Cart Total Value |Response |
|----|---|
|$100.00 - $399.99 USD | 3, 6, or 12 month offers |
|$400.00 - $3,999.99 USD | 6, 12, or 24 month offers|
|$4,000.00 - $10,000.00 USD | 6, 12, or 24 month offers |

