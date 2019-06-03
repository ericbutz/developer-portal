---
layout: twoColumn
section: guides
type: guide
guide:
    name: receive-money
    step: '2'
title:  Fetch funding sources
description: After creating a Customer and associated its funding source, will need to fetch the funding sources.
---
# Step 2: Fetch funding sources

Now that you’ve created a Customer and associated its funding source, you are almost ready to initiate your first transfer. The transfer requires the following information:

- The funding source to pull the funds from (your Customer's linked bank account)
- The recipient to push the funds to (your Dwolla Master Account bank account)

Dwolla uses URLs to represent relations between resources. Therefore, you’ll need to provide the full URL of the funding source and recipient.

## Fetch your Customer's list of available funding sources

Use the [list an Customer's funding sources](https://docs.dwolla.com/#list-funding-sources-for-a-customer) endpoint to fetch a list of your own funding sources. You'll need the Customer URL which can be [retrieved from the API.](https://docs.dwolla.com/#list-and-search-customers)

#### Request and response (view schema in 'raw')

```raw
GET https://api-sandbox.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254/funding-sources
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q

{
    "_links": {
        "self": {
            "href": "https://api-sandbox.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254/funding-sources?removed=false",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "funding-source"
        },
        "customer": {
            "href": "https://api-sandbox.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "customer"
        }
    },
    "_embedded": {
        "funding-sources": [
            {
                "_links": {
                    "transfer-from-balance": {
                        "href": "https://api-sandbox.dwolla.com/transfers",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "transfer"
                    },
                    "self": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/acb5689c-3905-408d-bf0f-e50e951692dc",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "funding-source"
                    },
                    "remove": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/acb5689c-3905-408d-bf0f-e50e951692dc",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "funding-source"
                    },
                    "initiate-micro-deposits": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/acb5689c-3905-408d-bf0f-e50e951692dc/micro-deposits",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "micro-deposits"
                    },
                    "customer": {
                        "href": "https://api-sandbox.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "customer"
                    },
                    "transfer-receive": {
                        "href": "https://api-sandbox.dwolla.com/transfers",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "transfer"
                    }
                },
                "id": "acb5689c-3905-408d-bf0f-e50e951692dc",
                "status": "unverified",
                "type": "bank",
                "bankAccountType": "checking",
                "name": "Jane Doe - Checking",
                "created": "2019-05-31T16:07:38.564Z",
                "removed": false,
                "channels": [
                    "ach"
                ],
                "bankName": "SANDBOX TEST BANK",
                "fingerprint": "562b8325748e1e3ca482ede7cd36e9a1a7635e7c0f4f30630658fccea9bcc772"
            },
            {
                "_links": {
                    "self": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/e5b8223f-08f7-4a7e-b952-88a773c0df61",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "funding-source"
                    },
                    "balance": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/e5b8223f-08f7-4a7e-b952-88a773c0df61/balance",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "balance"
                    },
                    "transfer-send": {
                        "href": "https://api-sandbox.dwolla.com/transfers",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "transfer"
                    },
                    "with-available-balance": {
                        "href": "https://api-sandbox.dwolla.com/funding-sources/e5b8223f-08f7-4a7e-b952-88a773c0df61",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "funding-source"
                    },
                    "customer": {
                        "href": "https://api-sandbox.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "customer"
                    },
                    "transfer-receive": {
                        "href": "https://api-sandbox.dwolla.com/transfers",
                        "type": "application/vnd.dwolla.v1.hal+json",
                        "resource-type": "transfer"
                    }
                },
                "id": "e5b8223f-08f7-4a7e-b952-88a773c0df61",
                "status": "verified",
                "type": "balance",
                "name": "Balance",
                "created": "2019-05-30T21:30:09.568Z",
                "removed": false,
                "channels": []
            }
        ]
    }
}
```

```ruby
customer_url = 'https://api.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254'

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
funding_sources = app_token.get "#{customer_url}/funding-sources"
funding_sources._embedded['funding-sources'][0].name # => "ABC Bank Checking"
```

```javascript
var customerUrl = 'https://api-sandbox.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254';

appToken
  .get(`${accountUrl}/funding-sources`)
  .then(function(res) {
    res.body._embedded['funding-sources'][0].name; // => 'ABC Bank Checking'
  });
```

```python
customers_url = 'https://api.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254'

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
funding_sources = app_token.get('%s/funding-sources' % customer_url)
funding_sources.body['_embedded']['funding-sources'][0]['name'] # => 'ABC Bank Checking'

```

```php
<?php
$customerUrl = 'https://api.dwolla.com/customers/ad5f2162-404a-4c4c-994e-6ab6c3a13254';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSources = $fsApi->getCustomerFundingSources($customerUrl);
# Access desired information in response object fields
print($fundingSources->_embedded) # => PHP associative array of _embedded contents in schema
?>
```

## Fetch your Dwolla Master Account's list of available funding sources

Use the [list an account's funding sources](https://docs.dwolla.com/#list-funding-sources-for-an-account) endpoint to fetch a list of your own funding sources. You'll need your account URL which can be retrieved by calling [the Root](https://docs.dwolla.com/#root) of the API.

#### Request and response (view schema in 'raw')

```raw
GET https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b/funding-sources
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b/funding-sources"
    }
  },
  "_embedded": {
    "funding-sources": [
      {
        "_links": {
          "self": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/0094b1b4-e171-4dc8-865b-cb121c2377bb"
          },
          "account": {
            "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b"
          },
          "with-available-balance": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/0094b1b4-e171-4dc8-865b-cb121c2377bb"
          }
        },
        "id": "0094b1b4-e171-4dc8-865b-cb121c2377bb",
        "status": "verified",
        "type": "balance",
        "name": "Balance",
        "created": "2013-09-07T14:42:52.000Z"
      },
      {
        "_links": {
          "self": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/b5e68264-7d4d-42a9-88d4-5616c77c6baa"
          },
          "account": {
            "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b"
          }
        },
        "id": "b5e68264-7d4d-42a9-88d4-5616c77c6baa",
        "status": "verified",
        "type": "bank",
        "name": "ABC Bank Checking",
        "created": "2014-09-04T23:19:19.543Z"
      }
    ]
  }
}
```

```ruby
account_url = 'https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b'

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
funding_sources = app_token.get "#{account_url}/funding-sources"
funding_sources._embedded['funding-sources'][0].name # => "ABC Bank Checking"
```

```javascript
var accountUrl = 'https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b';

appToken
  .get(`${accountUrl}/funding-sources`)
  .then(function(res) {
    res.body._embedded['funding-sources'][0].name; // => 'ABC Bank Checking'
  });
```

```python
account_url = 'https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b'

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
funding_sources = app_token.get('%s/funding-sources' % account_url)
funding_sources.body['_embedded']['funding-sources'][0]['name'] # => 'ABC Bank Checking'

```

```php
<?php
$accountUrl = 'https://api.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSources = $fsApi->getAccountFundingSources($accountUrl);
# Access desired information in response object fields
print($fundingSources->_embedded) # => PHP associative array of _embedded contents in schema
?>
```


<nav class="pager-nav">
    <a href="/guides/receive-money/onboarding.html">Back: Customer onboarding</a>
    <a href="/guides/receive-money/create-transfer.html">Next: Create a transfer</a>
</nav>
