---
stoplight-id: zjkn6hgrobrl7
---

# Certification

**How can I get my API integration tested?**

---

When you’ve passed your internal QA testing, you are ready for Cash App Afterpay Certification. Contact your Cash App Afterpay account manager to schedule certification testing.

Testing is done on each unique environment you will have in production. The test suite includes three areas:

* Integration Standards

* Customer Experience

* Refunds

Certification ensures a great customer experience, minimizes the potential for fraudulent activity, and checks for common compliance and technical issues.

<!-- theme: info -->
> **Note**
>
> **Production Credentials:** 
>
> Your Cash App Afterpay production credentials are issued upon successful completion of the Cash App Afterpay Certification.

## Deployment

When moving your integration to your production environment, ensure the API Endpoint and Javascript URL are being loaded for Cash App Afterpay's production environment.

|Environment| API Endpoint |	Screenflow (Javascript)|
|---|---|----|
|Sandbox|	https://api.us-sandbox.afterpay.com/v1 OR https://api.us-sandbox.afterpay.com/v2	| https://portal.sandbox.afterpay.com/afterpay.js |
|Production|	https://api.us.afterpay.com/v1 OR https://api.us.afterpay.com/v2|	https://portal.afterpay.com/afterpay.js|

<!-- theme: info -->
> **Note**
>
> **Update the User-Agent Header:** 
>
> When you move to a production environment, please make sure the User-Agent Header is updated with the production Merchant ID.