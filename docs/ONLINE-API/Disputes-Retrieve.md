---
stoplight-id: z7i6mnvep8onr
---


# Uploading and Retrieving Files

This section contains the following topics:

* [Uploading files](#uploading-files)

* [Retrieving files](#retrieving-files)

* [Errors](#errors)

* [Diffie-Hellman Key Exchange](#key-exchange)

## Uploading files

<!-- theme: warning-->
> **Warning**
>
> The maximum upload file size is 10MB.

The Merchant ID of the file is saved along with the uploaded file. 

<!-- theme: warning-->
> **Warning**
>
> The file can only be retrieved by the person who uploaded the file.

The file types that are supported by Cash App Afterpay are:

* GIF

* PDF

* JPEG

* PNG

### Upload file - endpoint

```
POST https://{afterpay_global_url}/v2/disputes/files
```
#### Connection Timeouts
| Timeout | Time (seconds) |
|------------|-----------|
| `OPEN`       | 10    | 
| `Read `       | 20    | 

#### Request Headers

| Header | Type | Example |
|------------|-----------|---------------------|
| `User-Agent`| String | `MyCashAppAfterpayModule/1.0.0 (E-Commerce Platform Name/1.0.0; PHP/7.0.0; Merchant/60032000) https://merchant.example.com` |

| Header | Type | Default Value        |
|------------|-----------|------------------|
| `Accept`   | String    | application/json |
| `Content-Type` | String | application/json|

### Request Parameters

| Field name | Data type | Status|Description                                                   |
|------------|-----------|---|------------------------------------------------------------|
| `file`       | File      | Required | The file you want to upload.                                       |
| `fileType`   | String    | Required | The type of the file, we now only support `dispute_evidence`. |

### Response

| Field name | Data type | Description                                                                      |
|------------|-----------|----------------------------------------------------------------------------------|
| `id`        | String    | The ID token of the file.                                                         |
| `createdAt`  | Datetime  | The timestamp that indicates when the file was uploaded. (Format: 2022-04-19T02:58:44.086829)            |
| `expiresAt`  | Datetime  | The timestamp that indicates when the uploaded file expires. (Format: 2022-04-19T02:58:44.086829) |

### Response example

| Field name | Data type | Example                    |
| ---------- | --------- | -------------------------- |
| `id`       | String    | fi_7wvZBQqWzoPGLxvaMkpTjX  |
| `createdAt`| Datetime  | 2023-08-18T02:05:23.121893 |
| `expiresAt`| Datetime  | 2023-08-18T02:05:23.121893 |

## Retrieving files

### Retrieve file - endpoint

```
GET https://{afterpay_global_url}/v2/disputes/files/{id}
```
#### Connection Timeouts
| Timeout | Time (seconds) |
|------------|-----------|
| `OPEN`       | 10    | 
| `Read `       | 20    | 

#### Request Headers

| Header | Type | Example        |
|------------|-----------|---------------------|
| `User-Agent`| String | `MyCashAppAfterpayModule/1.0.0 (E-Commerce Platform Name/1.0.0; PHP/7.0.0; Merchant/60032000) <https://merchant.example.com>` |

| Header | Type | Default Value        |
|------------|-----------|------------------|
| `Accept`   | String    | application/json |


### Request Parameters

| Field name | Data type | Status |Description                      |
|------------|-----------|--|--------------------------------|
| `id`         | String    | Required |File ID of the file that has to be retrieved. |

### Response

| Field name | Data type | Description                                                             |
|------------|-----------|-------------------------------------------------------------------------|
| `url`       | String    | The link of the file to be retrieved.                                                   |
| `expiresAt`  | Datetime  | The timestamp indicating the expiration of the link. (Format: 2022-04-19T02:58:44.086829) |

### Response example

| Field name | Data type | Example                    |
| ---------- | --------- | -------------------------- |
| `url`      | String    | https://dispute-attachment.s3.amazonaws.com/fi_7GciehSJnhRdUF9acxsB63|
| `expiresAt`| Datetime  | 2023-08-18T02:05:23.121893 |

## Errors

| Error Code                     | Description                                                                                     |
|--------------------------------|-------------------------------------------------------------------------------------------------|
| 401 - Unauthorized             | Invalid merchant credentials.     |
| 404 - Not Found                | The corresponding entity can’t be found for the merchant. |
| 412 - Precondition Failed      | Invalid action for the dispute case, or the refund amount is larger than the refundable amount. |
| 413 - Request Entity Too Large | The uploaded file is too large.  It must be less than 10 MB.                                                                 |
| 415 - Unsupported Media Type   | Cash App Afterpay does not support the filetype of the uploaded file. It must be one of these: GIF, PDF, JPEG, or PNG.   |
| 422 - Unprocessable Entity     | Invalid parameter in the Dispute API request.    |
| 429 - Too Many Requests        | Too many requests in a short period of time, retry later.   |

## Key exchange

### Diffie-Hellman key exchange

**Wiki page:** https://wiki.openssl.org/index.php/Diffie_Hellman

### Dependency

Openssl version = LibreSSL 2.8.3


### Steps in the key exchange process

Assume Alice and Bob are doing key exchange, Alice is working for corporation A, Bob is working for corporation B.


1. Alice generates a pem file in the current directory which contains the parameters `g` and `p` in a `DH` algorithm.

    ```
    openssl genpkey -genparam -algorithm DH -out dhp1.pem  -pkeyopt      dh_paramgen_prime_len:2048
    ```


2. Alice publicly sends the `dhp1.pem` file to Bob.

3. Alice generates a private key in her laptop, and exports the public key.
    ```
    openssl genpkey -paramfile dhp1.pem -out dhkey1.pem
    openssl pkey -in dhkey1.pem -pubout -out dhpub1.pem
    ```

4. Bob generates a private key in his laptop.
    ```
    openssl genpkey -paramfile dhp1.pem -out dhkey2.pem
    openssl pkey -in dhkey2.pem -pubout -out dhpub2.pem
    ```

5. Alice and Bob publicly exchange public keys, Alice gets the `dhpub2.pem` file, Bob gets the `dhpub1.pem` file.

6. Alice generates a secret key.

    ```
    openssl pkeyutl -derive -inkey dhkey1.pem -peerkey dhpub2.pem -out secret1
    ```

7. Bob generates a secret key.
    ```
    openssl pkeyutl -derive -inkey dhkey2.pem -peerkey dhpub1.pem -out secret2
    ```

8. Currently Alice and Bob should have the same secret key, which is completely secure. `(secret1 == secret2)`

### Encryption and decryption

1. Alice wants to send a file to Bob securely. She uses the `secret1` to encrypt the file. Assumes the origin file named text.
    ```
    openssl enc -aes-256-cbc -pass file:secret1 -in text -out     text.enc -p
    ```
2. Alice publicly sends the encrypted file `text.enc` to Bob.

3. Bob uses `secret2` to decrypt the file.
    ```
    openssl enc -aes-256-cbc -pass file:secret2 -in text.enc -out        text.origin -p -d
    ```