---
layout: twoColumn
section: guides
type: guide
guide:
    name: send-money
    step: '3'
title:  Creating an ACH transfer
description: Create a transfer by specifying your funding source ID as the source and your Customer's funding source id as the destination.
---
# Step 3: Create a transfer

Create a transfer by specifying your Dwolla Master Account bank funding source as the `source` and the Customer bank funding source as the `destination`.

You can learn more about initiating transfers in our [API Reference docs.](https://docs.dwolla.com/#initiate-a-transfer)

#### Request and response (view schema in 'raw')

```raw
POST https://api-sandbox.dwolla.com/transfers
Accept: application/vnd.dwolla.v1.hal+json
Content-Type: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNicvoWhDbQcVSKLRUpGjIdlPSEYyrHqrDDoRnQwE7Q
{
    "_links": {
        "source": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
        },
        "destination": {
            "href": "https://api-sandbox.dwolla.com/funding-sources/3152c22b-3d72-442d-a83b-e575df3a043e"
        }
    },
    "amount": {
        "currency": "USD",
        "value": "225.00"
    }
}

...

HTTP/1.1 201 Created
Location: https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
```

```ruby
transfer_request = {
  :_links => {
    :source => {
      :href => "https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985"
    },
    :destination => {
      :href => "https://api-sandbox.dwolla.com/funding-sources/3152c22b-3d72-442d-a83b-e575df3a043e"
    }
  },
  :amount => {
    :currency => "USD",
    :value => "225.00"
  }
}

# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
transfer = app_token.post "transfers", transfer_request
transfer.response_headers[:location] # => "https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388"
```

```javascript
var transferRequest = {
  _links: {
    source: {
      href: 'https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985'
    },
    destination: {
      href: 'https://api-sandbox.dwolla.com/funding-sources/3152c22b-3d72-442d-a83b-e575df3a043e'
    }
  },
  amount: {
    currency: 'USD',
    value: '225.00'
  }
};

appToken
  .post('transfers', transferRequest)
  .then(function(res) {
    res.headers.get('location'); // => 'https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388'
  });
```

```python
transfer_request = {
  '_links': {
    'source': {
      'href': 'https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985'
    },
    'destination': {
      'href': 'https://api-sandbox.dwolla.com/funding-sources/3152c22b-3d72-442d-a83b-e575df3a043e'
    }
  },
  'amount': {
    'currency': 'USD',
    'value': '225.00'
  }
}

# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
transfer = app_token.post('transfers', transfer_request)
transfer.headers['location'] # => 'https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388'
```

```php
<?php
$transfer_request = array (
  '_links' =>
  array (
    'source' =>
    array (
      'href' => 'https://api-sandbox.dwolla.com/funding-sources/5cfcdc41-10f6-4a45-b11d-7ac89893d985',
    ),
    'destination' =>
    array (
      'href' => 'https://api-sandbox.dwolla.com/funding-sources/3152c22b-3d72-442d-a83b-e575df3a043e',
    ),
  ),
  'amount' =>
  array (
    'currency' => 'USD',
    'value' => '225.00',
  )
);

$transferApi = new DwollaSwagger\TransfersApi($apiClient);
$transfer = $transferApi->create($transfer_request);

print($transfer); # => https://api-sandbox.dwolla.com/transfers/d76265cd-0951-e511-80da-0aa34a9b2388
?>
```

<nav class="pager-nav">
    <a href="fetch-funding-sources.html">Back: Fetch funding sources</a>
    <a href="check-transfer.html">Next: Check the transfer status</a>
</nav>
