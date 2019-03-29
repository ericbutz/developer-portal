---
layout: twoColumn
section: resources
type: article
title:  Balance Funding Source
description: The Dwolla balance is made available for account types that have completed “KYC” requirements, which encompasses customers of Dwolla as well as their end user’s on-boarded as Verified Customers.
---
# The Dwolla Balance

## Overview

There are two types of [Funding Sources](https://docs.dwolla.com/#funding-sources) available within the Dwolla Platform which include a bank or a balance. A bank account is commonly used as the source or destination for ACH transfers. A `balance` is a Funding Source that can be utilized like a “wallet” for holding a stored value of USD funds. The Dwolla balance is made available for account types that have completed [“KYC” requirements](https://www.dwolla.com/updates/guide-customer-identification-program-payments-api/), which includes customers of Dwolla and their end users that have been on-boarded as [Verified Customers](https://developers.dwolla.com/resources/account-types.html#verified-customer).
  
What makes the Dwolla balance useful in relation to the platform is that the funds live within the Dwolla network. This means the Dwolla balance acts as a funding source associated directly with each Customer within your application.  This funding source can only be accessed within your application by the end user, and you must provide an easily accessible and accurate summary of the transfer history for the Customer’s balance.

## Functionality and Benefits

The Dwolla balance allows for greater flexibility for your desired funds flow and delivers another efficient method to move funds.

### Transfers

As a funding source, you can use the balance to:

* Receive funds from a bank funding source into the Dwolla Balance
* Send funds from the Dwolla Balance into a bank funding source
* Make instant payment transfers between two Dwolla Balance funding sources
* Hold funds in a Dwolla Balance

To learn more about how to initiate transfers with the Dwolla API, check out [our API Reference Docs](https://docs.dwolla.com/#transfers)

### Balance Transfer Timing

In production, transfer timing will vary depending on whether the balance is specified as the `source` or `destination` of the bank transfer. If transferring between two balance funding sources, the funds will settle instantly. 

| Bank to Balance   | Balance to Bank   | Balance to Balance |
|-------------------|-------------------|--------------------|
| 3-4 Business Days | 1-2 Business Days | Instant            |

## Viewing and Displaying the Balance

### Retrieving the Balance Funding Source

The balance Funding Source can be accessed when an account has successfully completed the identity verification process and has a status of `verified`. Since this funding source exists within the Dwolla Network you can obtain the details by utilizing the Dwolla API to retrieve the account’s list of funding sources.

#### Retrieve Dwolla Master Account Balance Funding Source

Check out our API Reference Docs to learn more about retrieving the balance funding source for [your Dwolla Master Account](https://docs.dwolla.com/#list-funding-sources-for-an-account).

##### Example request and response

```raw
GET https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b/funding-sources
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

...
{
    "_links": {
        "self": {
            "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b/funding-sources",
            "resource-type": "funding-source"
        }
    },
    "_embedded": {
        "funding-sources": [
            {
                "_links": {
                    "self": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/04173e17-6398-4d36-a167-9d98c4b1f1c3",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "funding-source"
                    },
                    "account": {
                        "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "account"
                    }
                },
                "id": "04173e17-6398-4d36-a167-9d98c4b1f1c3",
                "status": "verified",
                "type": "bank",
                "bankAccountType": "checking",
                "name": "My Account - Checking",
                "created": "2017-09-25T20:03:41.000Z",
                "removed": false,
                "channels": [
                    "ach"
                ],
                "bankName": "First Midwestern Bank"
            },
            {
                "_links": {
                    "self": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/b268f6b9-db3b-4ecc-83a2-8823a53ec8b7",
                    },
                    "account": {
                        "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b",
                    },
                    "with-available-balance": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/b268f6b9-db3b-4ecc-83a2-8823a53ec8b7",
                    },
                    "balance": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/b268f6b9-db3b-4ecc-83a2-8823a53ec8b7/balance",
                    }
                },
                "id": "b268f6b9-db3b-4ecc-83a2-8823a53ec8b7",
                "status": "verified",
                "type": "balance",
                "name": "Balance",
                "created": "2017-08-22T18:21:51.000Z",
                "removed": false,
                "channels": []
            }
        ]
    }
}
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
account_url = 'https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b'

funding_sources = app_token.get "#{account_url}/funding-sources"
funding_sources._embedded['funding-sources'][1].name # => "Balance"
```

```javascript
var accountUrl = 'https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b';

appToken
  .get(`${accountUrl}/funding-sources`)
  .then(res => res.body._embedded['funding-sources'][1].name); // => 'Balance'
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
account_url = 'https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b'

funding_sources = app_token.get('%s/funding-sources' % account_url)
funding_sources.body['_embedded']['funding-sources'][1]['name'] # => 'Balance'
```

```php
<?php
$accountUrl = 'https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSources = $fsApi->getAccountFundingSources($accountUrl);
$fundingSources->_embedded->{'funding-sources'}[1]->name; # => "Balance"
?>
```

#### Retrieve a Customer's Balance Funding Source

Check out our API Reference Docs to learn more about retrieving the balance funding source for [your Verified Customers](https://docs.dwolla.com/#list-funding-sources-for-a-customer).

##### Example request and response

```raw
GET https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733/funding-sources
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

...

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733/funding-sources"
    },
    "customer": {
      "href": "https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733"
    }
  },
  "_embedded": {
    "funding-sources": [
      {
        "_links": {
          "self": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/ab9cd5de-9435-47af-96fb-8d2fa5db51e8"
          },
          "customer": {
            "href": "https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733"
          },
          "with-available-balance": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/ab9cd5de-9435-47af-96fb-8d2fa5db51e8"
          }
        },
        "id": "ab9cd5de-9435-47af-96fb-8d2fa5db51e8",
        "status": "verified",
        "type": "balance",
        "name": "Balance",
        "created": "2015-10-02T21:00:28.153Z",
        "removed": false,
        "channels": []
      },
      {
        "_links": {
          "self": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/98c209d3-02d6-4bee-bc0f-61e18acf0e33"
          },
          "customer": {
            "href": "https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733"
          }
        },
        "id": "98c209d3-02d6-4bee-bc0f-61e18acf0e33",
        "status": "verified",
        "type": "bank",
        "bankAccountType": "checking",
        "name": "Jane Doe’s Checking",
        "created": "2015-10-02T22:03:45.537Z",
        "removed": false,
        "channels": [
            "ach"
        ],
        "fingerprint": "4cf31392f678cb26c62b75096e1a09d4465a801798b3d5c3729de44a4f54c794"
      }
    ]
  }
}
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
customer_url = 'https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733'

funding_sources = app_token.get "#{customer_url}/funding-sources"
funding_sources._embedded['funding-sources'][0].name # => "Balance"
```

```javascript
var customerUrl = 'https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733';

appToken
  .get(`${customerUrl}/funding-sources`)
  .then(res => res.body._embedded['funding-sources'][0].name); // => 'Balance'
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
customer_url = 'https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733'

funding_sources = app_token.get('%s/funding-sources' % customer_url)
funding_sources.body['_embedded']['funding-sources'][0]['name'] # => 'Balance'
```

```php
<?php
$customerUrl = 'https://api-sandbox.dwolla.com/customers/5b29279d-6359-4c87-a318-e09095532733';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSources = $fsApi->getCustomerFundingSources($customerUrl);
$fundingSources->_embedded->{'funding-sources'}[0]->name; # => "Balance"
?>
```

### Check the Balance Amount

The Dwolla balance also entails a feature in which you can check the value of the balance at any given time. Being able to know the amount of funds in your balance is necessary information to have prior to sending funds. You must also be able to show the available balance at all times within your application to your Customers.
Check out our [API Reference Docs to learn more](https://docs.dwolla.com/#retrieve-a-funding-source-balance).

##### Example request and response

```raw
GET https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418/balance
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418/balance",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "balance"
    },
    "funding-source": {
      "href": "https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "funding-source"
    }
  },
  "balance": {
    "value": "4616.87",
    "currency": "USD"
  },
  "lastUpdated": "2017-04-18T15:20:25.880Z"
}
```

```ruby
funding_source_url = 'https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418'

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
funding_source = app_token.get "#{funding_source_url}/balance"
```

```javascript
var fundingSourceUrl = 'https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418';

appToken
  .get(`${fundingSourceUrl}/balance`)
  .then(res => res.body.balance.amount);
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
funding_source_url = 'https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418'

funding_source = app_token.get('%s/balance' % funding_source_url)
```

```php
<?php
$fundingSourceUrl = 'https://api-sandbox.dwolla.com/funding-sources/c2eb3f03-1b0e-4d18-a4a2-e552cc111418';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSource = $fsApi->getBalance($fundingSourceUrl);
?>
```

## Transfer failures

The amount in a Dwolla balance can be adjusted when a bank transfer failure occurs. In a transaction, if funds fail to process to a destination bank, they will be sent back to a Dwolla Balance.

### Transfer failure example

Let’s illustrate a transfer failure with an example:

* Source - Dwolla Master Account’s Bank Funding Source
* Destination  - Receive-only User’s Bank Funding Source

In this example, our Receive-only User closes down their bank account while the transaction is still in-flight and in a `pending` status.

Rather than the funds clearing to their now-closed bank account, an ACH return will be triggered which pushes these funds back to the Dwolla Master Account  balance funding source. It is then up to you on whether your application will  prompt your user to add another bank, or to return the funds to the source party’s bank account.

For more information on possible transfer failure scenarios and the Return Codes associated with each, check out our [Transfer Failures](https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html) developer resources article.
