---
layout: twoColumn
section: Bank transfer workflow
type: article
title:  "Transfer failures"
weight: 1
description: "How to handle transfer failures in a bank transfer API to programmatically send money online."
---

# Bank transfer workflow

## Transfer failures

There are several reasons bank transfers can fail, a few of which are outlined below. When a transfer fails it is usually a result of an ACH failure which is assigned an ACH return code after being rejected from the financial institution. A few common failure cases include:

- **Insufficient Funds (R01):** Pending transfers can fail due to insufficient funds from the source bank account.
- **No Account/Unable to Locate Account (R03):** The recipient of a transfer has closed their bank account or has incorrectly entered their bank account/routing number when attaching their funding source.
- **Customer Advises Not Authorized (R10):** The owner of a bank account has told their bank that this transfer was unauthorized.

### What occurs in the Dwolla system when a bank transfer fails?

When a bank transfer failure occurs there is a subset of systematic actions Dwolla may take on the Customer and/or the funding source based on the ACH return code. It is recommended to have an active [webhook subscription](https://docsv2.dwolla.com/#create-a-webhook-subscription), which is used to listen for events relating to any Customer or funding source state change. Please refer to the table below to understand the systematic actions that Dwolla may take for Customer and funding source resources, as well as the events that are created.

### Why does Dwolla automatically take these actions?

Being able to catch and take action errors can be beneficial on many levels. For instance, if your Customer initiates a transaction which fails with an R10 (Customer Advises Not Authorized) return code, Dwolla will automatically put the suspected Customer in a `deactivated` status, thereby not allowing them to initiate or receive more transfers. This gives you the ability investigate the Customer to determine if they are a valid party without worrying about them sending funds. Other return codes may only affect bank funding sources in which Dwolla may automatically unverify or remove a bank in response to various return codes.

#### Systematic actions taken against the Customer

| Customer action | Description | Webhook Event |
|-----------------|-------------|---------------|
| None            | No action taken against the Customer account as result of transfer failure | N/A |
| Deactivated     | Customer account has been deactivated                | `customer_deactivated`|

#### Systematic actions taken against the bank funding source

| Funding Source action | Description | Webhook Event |
|-----------------------|-------------|---------------|
| None                  | No action taken against the Customer bank funding source     | N/A |
| Unverified            | A Customer's bank has been unverified, but not removed       | `customer_funding_source_unverified` |
| Removed               | A Customer's bank has been removed                           | `customer_funding_source_removed` |


### Retrieving the reason for a failed bank transfer

When a bank transfer is unable to be completed, its status will be updated to `failed`. If your application is subscribed to webhooks, you’ll receive either the `transfer_failed` event if the transfer belongs to a Dwolla account or the `customer_transfer_failed`/`customer_bank_transfer_failed`(*Verified Customer only*) event if the transfer belongs to an API Customer. The event contains a links to the associated account as well as the transfer resource. To obtain more information on the transfer failure, you’ll first retrieve the transfer by its ID. The response from the API when retrieving the transfer should contain a `"failure"` link that your application will follow to [retrieve the transfer failure reason](https://docsv2.dwolla.com/#retrieve-a-transfer-failure-reason). Upon success, the response will contain information on the ACH return code and description, as well as `_links` to the Funding Source and Customer that triggered the bank transfer failure.

#### Request and response (view schema in 'raw')
```raw
GET https://api-sandbox.dwolla.com/transfers/8997ebed-69be-e611-80ea-0aa34a9b2388/failure
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

{
    "_links": {
        "self": {
            "href": "https://api.dwolla.com/transfers/8997ebed-69be-e611-80ea-0aa34a9b2388/failure",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "failure"
        },
        "failed-funding-source": {
            "href": "https://api.dwolla.com/funding-sources/285ea6f4-c45d-4e15-ad33-21f51461f437",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "funding-source"
        },
        "customer": {
            "href": "https://api.dwolla.com/customers/be2d2322-fdee-4361-8722-4289f5601604",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "customer"
        }
    },
    "code": "R03",
    "description": "No Account/Unable to Locate Account",
    "explanation": "The account number does not correspond to the individual identified in the entry or a valid account."
}
```
```ruby
transfer_url = 'https://api-sandbox.dwolla.com/transfers/8997ebed-69be-e611-80ea-0aa34a9b2388'

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
failure = app_token.get "#{transfer_url}/failure"
failure.code # => "R01"
```
```php
<?php
$transfer = '8997ebed-69be-e611-80ea-0aa34a9b2388';

$TransfersApi = new DwollaSwagger\TransfersApi($apiClient);

$failureReason = $TransfersApi->failureById($transfer);
print($failureReason->code); # => "R01"
?>
```
```python
transfer_url = 'https://api-sandbox.dwolla.com/transfers/8997ebed-69be-e611-80ea-0aa34a9b2388'

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
failure = app_token.get('%s/failure' % transfer_url)
failure.body['code'] # => 'R01'
```
```javascript
var transferUrl = 'https://api-sandbox.dwolla.com/transfers/8997ebed-69be-e611-80ea-0aa34a9b2388';

appToken
  .get(`${transferUrl}/failure`)
  .then(res => res.body.code); // => 'R01'
```

### List of possible return codes, descriptions, and actions

Below is a table of the most common return codes we see involved in transactions. For a full list of return codes, you can check out the [official NACHA Return Reason Code Guide](https://www.nacha.org/products/return-reason-code-guide).

**Note:** As a best practice, we recommend handling any systematic actions (Customer or bank funding source state change events) that are triggered as a result of a transfer failure. Rather than relying on the specific actions as referenced below. We do not recommend building a workflow around each individual return code in the table below. This table is a meant to be a reference for you to be aware of the actions Dwolla takes on common transfer failures.

| Return Code | Description | Customer Deactivated | Bank Unverified | Bank Removed |
|-------------|-------------|----------------------|-----------------|--------------|
| R01 | Insufficient Funds                                           | No | No | No |
| R02 | Bank Account Closed                                          | No | Yes | Yes |
| R03 | No Account/Unable to Locate Account                          | No | Yes | Yes |
| R04 | Invalid Bank Account Number Structure                        | No | Yes | Yes |
| R06 | Returned per ODFI’s Request                                  | No | No | No |
| R07 | Authorization Revoked by Customer                            | Yes | Yes | Yes |
| R08 | Payment Stopped                                              | Yes | Yes | Yes |
| R09 | Uncollected Funds                                            | No | Yes | Yes |
| R10 | Customer Advises Not Authorized, Improper, or Ineligible     | Yes | Yes | Yes |
| R16 | Bank Account Frozen                                          | No | No | No |
| R20 | Non-Transaction Account                                      | No | Yes | Yes |
| R23 | Credit Entry Refused by Receiver                             | No | Yes | Yes |
| R29 | Corporate Customer Advises Not Authorized                    | Yes | Yes | Yes |