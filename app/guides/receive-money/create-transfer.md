---
layout: twoColumn
section: guides
type: guide
guide:
    name: receive-money
    step: '3'
title:  Creating an ACH transfer
description: Create a transfer by specifying your funding source as the source and the Customer as the destination.
---
# Step 3: Create a transfer

Create a transfer by specifying the Customer's bank funding source as the  `source` and your Dwolla Master Account bank funding source as the `destination`.

You can learn more about initiating transfers in our [API Reference docs.](https://docsv2.dwolla.com/#initiate-a-transfer)

## Create a transfer

Once the customer has verified their funding source, we can transfer funds from their bank account to your Dwolla account. You’ll need to supply your access token and customer’s ID, as well as the customer’s funding source ID.

```raw
POST https://api-sandbox.dwolla.com/transfers
Accept: application/vnd.dwolla.v1.hal+json
Content-Type: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q
{
    "_links": {
        "source": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/80275e83-1f9d-4bf7-8816-2ddcd5ffc197"
        },
        "destination": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/456ef23f-d51c-4781-8fb6-dd0cb8a40192"
        }
    },
    "amount": {
        "currency": "USD",
        "value": "225.00"
    }
}

HTTP/1.1 201 Created
Location: https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
```

```ruby
request_body = {
  :_links => {
    :source => {
      :href => "https://api-sandbox.dwolla.com/funding-sources/80275e83-1f9d-4bf7-8816-2ddcd5ffc197"
    },
    :destination => {
      :href => "https://api-sandbox.dwolla.com/funding-sources/456ef23f-d51c-4781-8fb6-dd0cb8a40192"
    }
  },
  :amount => {
    :currency => "USD",
    :value => "225.00"
  },
  :metadata => {
    :foo => "bar",
    :baz => "boo"
  }
}

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
transfer = app_token.post "transfers", request_body
transfer.response_headers[:location] # => "https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388"
```

```javascript
var requestBody = {
  _links: {
    source: {
      href: 'https://api-sandbox.dwolla.com/funding-sources/80275e83-1f9d-4bf7-8816-2ddcd5ffc197'
    },
    destination: {
      href: 'https://api-sandbox.dwolla.com/funding-sources/456ef23f-d51c-4781-8fb6-dd0cb8a40192'
    }
  },
  amount: {
    currency: 'USD',
    value: '225.00'
  },
  metadata: {
    foo: 'bar',
    baz: 'boo'
  }
};

appToken
  .post('transfers', requestBody)
  .then(function(res) {
    res.headers.get('location'); // => 'https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388'
  });
```

```python
request_body = {
  '_links': {
    'source': {
      'href': 'https://api-sandbox.dwolla.com/funding-sources/80275e83-1f9d-4bf7-8816-2ddcd5ffc197'
    },
    'destination': {
      'href': 'https://api-sandbox.dwolla.com/funding-sources/456ef23f-d51c-4781-8fb6-dd0cb8a40192'
    }
  },
  'amount': {
    'currency': 'USD',
    'value': '225.00'
  },
  'metadata': {
    'foo': 'bar',
    'baz': 'boo'
  }
}

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
transfer = app_token.post('transfers', request_body)
transfer.headers['location'] # => 'https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388'
```

```php
<?php
$transfer_request = array (
  '_links' =>
  array (
    'source' =>
    array (
      'href' => 'https://api-sandbox.dwolla.com/funding-sources/80275e83-1f9d-4bf7-8816-2ddcd5ffc197',
    ),
    'destination' =>
    array (
      'href' => 'https://api-sandbox.dwolla.com/funding-sources/456ef23f-d51c-4781-8fb6-dd0cb8a40192',
    ),
  ),
  'amount' =>
  array (
    'currency' => 'USD',
    'value' => '225.00',
  )
);

$transferApi = new DwollaSwagger\TransfersApi($apiClient);
$myAccount = $transferApi->create($transfer_request);

print($xfer); # => https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
?>
```

<nav class="pager-nav">
    <a href="fetch-funding-sources.html">Back: Fetch Funding Sources</a>
    <a href="check-transfer.html">Next: Check Transfer Status</a>
</nav>
