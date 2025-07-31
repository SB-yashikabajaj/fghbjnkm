---
stoplight-id: 36htjb7upirq4
---


# Release Notes

## May 21, 2025
### 🚀 New

This release introduces a new API endpoint which can be used together with the Smart Upload feature to fetch localized extract guidance based on the selected accounting package (connector) and data scope. It helps guide users through downloading the correct reports from their accounting systems by providing tailored instructions. This ensures users have the right files prepared before proceeding with their upload, improving accuracy and reducing friction during the data import process.

- Introduced API endpoint to retrieve localized extract guidance per connector and scope.
- Implemented fallback to default guidance when package-specific content is missing.
- Guidance supports multiple locales: en-GB, en-US, en-CA, fr-FR, fr-CA.
- Multi-scope requests return package-specific or default guidance as applicable.
- Guidance records require structured metadata including ID, connector, scope, update date, source, and localized HTML content.


## January 21, 2025
### 🚀 New

We’ve introduced a **powerful new feature** that allows clients to seamlessly upload files from **any accounting system** (e.g., Sage, QuickBooks, etc.) directly into our API via the newly added **Connections API** endpoints.

Our **AI-driven Smart Upload** feature supports **common file formats** like **CSV, XLS, and XLSX** (up to **100MB per file**) and automatically extracts, transforms, and maps your financial data into meaningful reports - eliminating manual data entry and providing **faster, more accurate financial insights**.

**New Smart Upload Endpoints (Connections API)**
- **Perform a smart upload** – Upload financial data files for processing.
- **Get smart upload details** – Retrieve status and details of an uploaded file.
- **Get smart upload original files** – Download the original files from a smart upload.
- **Get connectors** – Fetch available accounting system integrations.

Expanded Functionality in the Accounting API

We’ve also enhanced financial data access by adding new endpoints to the Accounting API:
- **Aged receivables** 
- **Aged payables**

With these enhancements, you can streamline financial workflows, gain real-time visibility into your data, and improve decision-making efficiency. 🚀

### 🛠 Fixes and Improvements
#### Accounting API

``Journals``, ``Payable items``, ``Receivable items``, ``Suppliers``and ``Engagement customers`` - added new response body property **totalElements**, **totalPages**, **number**, and **numberOfElements**. This addition will improve clients data retrieval efficiency and ensure smoother handling of large datasets


## September 19, 2024
### 🚀 New

``Get connectors`` - added new response body property **uploadTypes**. This addition has been made to assist clients in identifying the upload extraction modes provided by our API

### 🛠 Fixes and Improvements
#### Companies API

``Create engagement``, and ``Update engagement`` - added allowed value for request body property **sme.type**. This is to enhance the clarity of our API and ensure clients know the exact values to provide

## July 18, 2024
### 🚀 New

``List receivable items``, and ``List payable items`` - added new response body property **sourceIdentifier**. This addition will enable clients to uniquely identify transactions originating from the accounting package


### 🛠 Fixes and Improvements
#### Companies API

- ``Create multiple engagements`` - **engagements[].sme.contacts** request body property is now optional


## June 19, 2024
### 🚀 New

Introduced a new beta endpoint ``Delete multiple engagements`` to the **Companies API**.  
This endpoint allows a Validis customer to delete one or more engagements

## May 17, 2024
### 🚀 New

Introduced a new beta endpoint ``Create multiple engagements`` to the **Companies API**.  
This endpoint offers enhanced functionality for creating one or more engagements for a Validis customer

## April 4, 2024
### 🛠 Fixes and Improvements
#### Companies API

- ``Delete engagement`` - added missing query parameter **fullRemoving** to the documentation

- ``Update engagement`` - removed request body properties **createdAt**, **id**, **reminderFrequency**, **status**, **sme.id**, and **sme.locale**. These properties have been removed to streamline the API request as they cannot be updated

#### Connections API

- ``Perform an upload`` - removed query parameter **mandatoryRedirectUrl**


## February 15, 2024
### 🚀 New 

Enhancing the functionality and scope of financial data access of our users, we added new endpoints to the **Reports API** 

  - ``Generate additional data``

  - ``Generate passthrough``


### 🛠 Fixes and Improvements 
#### Reports API
- ``Generate general ledger``, ``Generate accounts payable``  and ``Generate accounts receivable`` - added new parameters **includeFutureYears** and **format**. These additions offer enhanced customization options, allowing users greater control over their data generation process

#### Connections API

- ``Perform an upload`` - query parameter **mandatoryRedirectUrl** is now a required parameter




