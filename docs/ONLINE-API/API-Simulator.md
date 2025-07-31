---
stoplight-id: jqocghgwpw2nl
internal: true
---

# API Simulator

The API Simulator allows the user to formulate an API request, and "try it" to see how the Afterpay API will respond. Each of the API endpoints in this reference document are accompanied by an API Simulator.

For example, the following screenshot demonstrates that the Simulator is capable of correctly constructing an `Authorization` header, using the Merchant ID and Secret Key.

![Get configuration](../../assets/images/get-configuration.png)
Please note that this Simulator with the example code is provided as a guide only. It may not always represent best practice, or the recommendations of Afterpay. Please refer to your Afterpay technical contact if you are unsure of the best way to integrate with Afterpay.

When using the Simulator, please keep in mind the following considerations.

## JavaScript Code Samples

JavaScript must **never** be used to communicate with an Afterpay API in a Production environment.

Like all client-side scripting languages, JavaScript runs in the end-user's browser. Using your Afterpay Online API credentials from JavaScript will expose them to the public.

![JS Samples](../../assets/images/js-sample.png)

## Ruby Code Samples

In each of these samples, the code that is automatically generates suggests disabling SSL Peer Verification. This is an important component of any secure connection and should therefore **never** be disabled.

![Ruby Code Samples](../../assets/images/ruby-samples.png)
