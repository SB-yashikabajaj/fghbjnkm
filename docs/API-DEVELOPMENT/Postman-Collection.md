---
stoplight-id: m9him0bx7ssdh
---

# Postman Collection

The following steps outline the steps to install Postman, configure your sandbox credentials and start testing the Cash App Afterpay API.

## What is Postman?

Postman is a free-to-download tool for making HTTP requests.

## Download Postman

1. Visit www.getpostman.com and download the version of Postman required for your platform.

2. Install Postman.


# Import the Cash App Afterpay Collection

1. Open Postman

2. Click Import

3. Import the Cash App Afterpay Postman Collection for your region:

**United States:** http://static-us.afterpay.com/api/sandbox/Afterpay_Online_US_API_v2.postman_collection.json

<!--focus: false -->
![Postman- Import from link](../../assets/images/postman-import-from-link.png)

## Create a Postman Test Environment

To access and use environment variables, you must configure a new [Postman environment](https://learning.postman.com/docs/postman/variables-and-environments/managing-environments/).

1. Click on the gear icon in the top-right corner.

    <!--focus: false -->
    ![Gear icon](../../assets/images/postman-gear-icon.png)

2. Click **Add** on the **MANAGE ENVIRONMENTS** modal that appears.

3. Name the environment.

    <!--focus: false -->
    ![Name the environment](../../assets/images/postman-add-env-name.png)

4. Click **Add** to save the environment, then close the window.

5. Use this environment by selecting Afterpay Online US V2 from the dropdown list.

    <!--focus: false -->
    ![Select environment](../../assets/images/postman-select-env.png)

## Add Your Merchant ID and Secret Key

1. Click on the 3 dots `...` next to the collection name and click **Edit**

    <!--focus: false -->
    ![postman-configure-auth](../../assets/images/postman-configure-auth.png)

2. Click the **Authorization** Tab.

3. Enter your Merchant ID in the **Username** field.

4. Enter your Secret Key in the **Password** field.

5. Click **Update**.