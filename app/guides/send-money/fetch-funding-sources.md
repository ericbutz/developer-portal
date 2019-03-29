---
layout: twoColumn
section: guides
type: guide
guide:
    name: send-money
    step: '3'
title:  Fetch funding sources
description: After creating a Customer and associated its funding source, you can initiate your first transfer.
---
# Step 3: Retrieve funding sources

Now that you’ve created a Customer and associated its funding source, you are close to being able to initiate your first transfer. The transfer requires the following information:

* The funding source to pull the funds from (your Dwolla Master Account bank funding source)
* The funding source to push the funds to (your Customer’s linked bank funding source)

Dwolla uses URLs to represent relations between resources. Therefore, you’ll need to provide the full URL of the funding source and recipient.

## Step 3A: Fetch your Dwolla Master Account's list of Available Funding Sources

Use the [list an account’s funding sources endpoint](https://docs.dwolla.com/#list-funding-sources-for-an-account) to fetch a list of your own funding sources. You’ll need your account URL which can be retrieved by calling [the Root](https://docs.dwolla.com/#root) of the API.

#### Request and Response (view schema in `raw`)

```raw
GET https://api-sandbox.dwolla.com/accounts/4BB512E4-AD4D-4F7E-BFD0-A232007F21A1/funding-sources
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/accounts/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1/funding-sources"
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
            "href": "https://api-sandbox.dwolla.com/accounts/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1"
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
            "href": "https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
          },
          "account": {
            "href": "https://api-sandbox.dwolla.com/accounts/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1"
          }
        },
        "id": "5cfcdc41-10f6-4a45-b11d-7ac89893d985",
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
account_url = 'https://api.dwolla.com/accounts/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1'

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
funding_sources = app_token.get "#{account_url}/funding-sources"
funding_sources._embedded['funding-sources'][0].name # => "ABC Bank Checking"
```

```javascript
var accountUrl = 'https://api-sandbox.dwolla.com/accounts/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1';

appToken
  .get(`${accountUrl}/funding-sources`)
  .then(function(res) {
    res.body._embedded['funding-sources'][0].name; // => 'ABC Bank Checking'
  });
```

```python
account_url = 'https://api.dwolla.com/accounts/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1'

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
funding_sources = app_token.get('%s/funding-sources' % account_url)
funding_sources.body['_embedded']['funding-sources'][0]['name'] # => 'ABC Bank Checking'
```

```php
<?php
$accountUrl = 'https://api.dwolla.com/accounts/4BB512E4-AD4D-4F7E-BFD0-A232007F21A1';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSources = $fsApi->getAccountFundingSources($accountUrl);
# Access desired information in response object fields
print($fundingSources->_embedded) # => PHP associative array of _embedded contents in schema
?>
```

When the funding sources are successfully retrieved, you will receive a `200` HTTP response with the details of the funding sources. After retrieving the funding sources, we recommend storing the full URL for future use as it will be referenced when creating the transfer to this user’s bank account.

## Step 3B: Fetch your Customer's list of Available Funding Sources

Use the [list an Customer’s funding sources](https://docs.dwolla.com/#list-funding-sources-for-a-customer) endpoint to fetch a list of your own funding sources. You’ll need the Customer URL which can be [retrieved from the API.](https://docs.dwolla.com/#list-and-search-customers)

#### Request and Response (view schema in `raw`)

```raw
GET https://api-sandbox.dwolla.com/customers/4BB512E4-AD4D-4F7E-BFD0-A232007F21A1/funding-sources
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/customers/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1/funding-sources"
    }
  },
  "_embedded": {
    "funding-sources": [
      {
        "_links": {
          "self": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/0094b1b4-e171-4dc8-865b-cb121c2377bb"
          },
          "customer": {
            "href": "https://api-sandbox.dwolla.com/customers/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1"
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
            "href": "https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
          },
          "customer": {
            "href": "https://api-sandbox.dwolla.com/customers/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1"
          }
        },
        "id": "5cfcdc41-10f6-4a45-b11d-7ac89893d985",
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
customer_url = 'https://api.dwolla.com/customers/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1'

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
funding_sources = app_token.get "#{customer_url}/funding-sources"
funding_sources._embedded['funding-sources'][0].name # => "ABC Bank Checking"
```

```javascript
var customerUrl = 'https://api-sandbox.dwolla.com/customers/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1';

appToken
  .get(`${accountUrl}/funding-sources`)
  .then(function(res) {
    res.body._embedded['funding-sources'][0].name; // => 'ABC Bank Checking'
  });
```

```python
customers_url = 'https://api.dwolla.com/customers/4bb512e4-ad4d-4f7e-bfd0-a232007f21a1'

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
funding_sources = app_token.get('%s/funding-sources' % customer_url)
funding_sources.body['_embedded']['funding-sources'][0]['name'] # => 'ABC Bank Checking'
```

```php
<?php
$customerUrl = 'https://api.dwolla.com/customers/4BB512E4-AD4D-4F7E-BFD0-A232007F21A1';

$fsApi = new DwollaSwagger\FundingsourcesApi($apiClient);

$fundingSources = $fsApi->getCustomerFundingSources($customerUrl);
# Access desired information in response object fields
print($fundingSources->_embedded) # => PHP associative array of _embedded contents in schema
?>
```

When the funding sources are successfully retrieved, you will receive a `200` HTTP response with the details of the funding sources. After retrieving the funding sources, we recommend storing the full URL for future use as it will be referenced when creating the transfer to this user’s bank account.

<nav class="pager-nav">
    <a href="add-funding-source.html">Back: Add funding source</a>
    <a href="create-transfer.html">Next: Create a transfer</a>
</nav>
