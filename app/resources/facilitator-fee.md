---
layout: twoColumn
section: resources
type: features
title:  Facilitator fee
description: The facilitator fee is a feature allowing for a flat rate amount to be removed from a payment as a fee, and sent to the creator of the Dwolla application.
---

# Facilitator fee

The facilitator fee is a feature allowing for a flat rate amount to be removed from a payment as a fee, and sent to the creator of the Dwolla application. The fee does not affect the original payment amount, and exists as a separate Transfer resource with a unique transfer ID.

#### Items to note before charging fees:

* Fees can only be applied to a transaction between two parties
* Facilitator fees can be debited from either the sending or receiving user of the payment
* The sum of fees cannot exceed 50% of the original transfer amount
* A facilitator fee must be at least $0.01
* Multiple facilitator fees can be associated with a single payment
* You must clearly communicate the fee and its payment terms to your end-user and obtain the user’s express consent to charge the fee.

### Charging fees on transfers

Fees are programmatically set on an individual transfer API request. Within a transfer request you can specify an optional `fees` request parameter, which is an array of fee objects that can represent many unique fee transfers. If your platform wishes to charge a percentage of the total transfer amount then your application will need to compute the percentage prior to initiating the transfer request. **Note:** Fees must be deducted from one of the accounts that is involved in either sending or receiving the funds for a transfer (not an alternative account).

A fee object is made up of a `_links` and an `amount` JSON object. The `_links` object contains `charge-to`, which represents the associated source or destination [Customer](https://docs.dwolla.com/#customers) or [Account](https://docs.dwolla.com/#accounts) resource that will assume the fee. The `amount` object contains `value` and `currency` keys corresponding to the fee amount and `USD` respectively.

#### A fee object:
```noselect
{  
   "_links":{  
      "charge-to":{  
         "href":"https://api-sandbox.dwolla.com/customers/d795f696-2cac-4662-8f16-95f1db9bddd8"
      }
   },
   "amount":{  
      "value":"4.00",
      "currency":"USD"
   }
}
```

#### Example transfer request:

```raw
POST https://api-sandbox.dwolla.com/transfers
Accept: application/vnd.dwolla.v1.hal+json
Content-Type: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

{  
   "_links":{  
      "source":{  
         "href":"https://api-sandbox.dwolla.com/funding-sources/707177c3-bf15-4e7e-b37c-55c3898d9bf4"
      },
      "destination":{  
         "href":"https://api-sandbox.dwolla.com/customers/07D59716-EF22-4FE6-98E8-F3190233DFB8"
      }
   },
   "amount":{  
      "value":"10.00",
      "currency":"USD"
   },
   "fees":[  
      {  
         "_links":{  
            "charge-to":{  
               "href":"https://api-sandbox.dwolla.com/customers/07D59716-EF22-4FE6-98E8-F3190233DFB8"
            }
         },
         "amount":{  
            "value":"2.00",
            "currency":"USD"
         }
      }
   ]
}
```
```php
<?php
$transfersApi = new DwollaSwagger\TransfersApi($apiClient);

$transfer = $transfersApi->create([
  '_links' => [
    'source' => [
      'href' => 'https://api-sandbox.dwolla.com/funding-sources/707177c3-bf15-4e7e-b37c-55c3898d9bf4',
    ],
    'destination' => [
      'href' => 'https://api-sandbox.dwolla.com/funding-sources/a2152a8a-b1a6-4b5e-9354-79e2bb8753ee'
    ]
  ],
  'amount' => [
    'currency' => 'USD',
    'value' => '98.00'
  ],
  'fees' => [
     [
        '_links' => [
           'charge-to' => [
              'href' => 'https://api-sandbox.dwolla.com/customers/479ce4c8-385f-4cfa-9693-262c0c3b6408'
           ]
        ],
        'amount' => [
           'value' => '2.00',
           'currency' => 'USD'
        ]
     ]
  ]
 ]);

print_r($transfer); # => "https://api-sandbox.dwolla.com/transfers/74c9129b-d14a-e511-80da-0aa34a9b2388"
?>
```
```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
request_body = {
  :_links => {
    :source => {
      :href => "https://api-sandbox.dwolla.com/funding-sources/707177c3-bf15-4e7e-b37c-55c3898d9bf4"
    },
    :destination => {
      :href => "https://api-sandbox.dwolla.com/funding-sources/a2152a8a-b1a6-4b5e-9354-79e2bb8753ee"
    }
  },
  :amount => {
    :currency => "USD",
    :value => "98.00"
  },
  :fees => [  
     {  
        :_links => {  
           :charge-to => {  
              :href => "https://api-sandbox.dwolla.com/customers/479ce4c8-385f-4cfa-9693-262c0c3b6408"
           }
        },
        :amount => {  
           :value => '2.00',
           :currency => 'USD'
        }
     }
  ]
}

transfer = app_token.post "transfers", request_body
transfer.response_headers[:location] # => "https://api.dwolla.com/transfers/74c9129b-d14a-e511-80da-0aa34a9b2388"
```
```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
request_body = {
  '_links': {
    'source': {
      'href': 'https://api-sandbox.dwolla.com/funding-sources/707177c3-bf15-4e7e-b37c-55c3898d9bf4'
    },
    'destination': {
      'href': 'https://api-sandbox.dwolla.com/funding-sources/a2152a8a-b1a6-4b5e-9354-79e2bb8753ee'
    }
  },
  'amount': {
    'currency': 'USD',
    'value': '98.00'
  },
  'fees':[  
      {  
         '_links': {  
            'charge-to': {  
               'href': 'https://api-sandbox.dwolla.com/customers/479ce4c8-385f-4cfa-9693-262c0c3b6408'
            }
         },
         'amount':{  
            "value":'2.00',
            'currency':'USD'
         }
      }
   ]
}

transfer = app_token.post('transfers', request_body)
transfer.headers['location'] # => 'https://api.dwolla.com/transfers/74c9129b-d14a-e511-80da-0aa34a9b2388'
```
```javascript
var requestBody = {
  _links: {
    source: {
      href: 'https://api-sandbox.dwolla.com/funding-sources/707177c3-bf15-4e7e-b37c-55c3898d9bf4'
    },
    destination: {
      href: 'https://api-sandbox.dwolla.com/funding-sources/a2152a8a-b1a6-4b5e-9354-79e2bb8753ee'
    }
  },
  amount: {
    currency: 'USD',
    value: '98.00'
  },
  fees: [  
     {  
        _links: {  
           charge-to: {  
              href: 'https://api-sandbox.dwolla.com/customers/479ce4c8-385f-4cfa-9693-262c0c3b6408'
           }
        },
        amount: {  
           value: '2.00',
           currency: 'USD'
        }
     }
  ]
};

appToken
  .post('transfers', requestBody)
  .then(res => res.headers.get('location')); // => 'https://api-sandbox.dwolla.com/transfers/74c9129b-d14a-e511-80da-0aa34a9b2388'
```

### Retrieve fees charged on a transfer
Once a transfer is successfully created, subsequent transfers will be created that represent the associated fees on that transfer. These fees will not be charged until the transfer processes successfully to the destination user. In the event of a `failed` or `cancelled` payment no fees will be charged.

#### Example Get a transfer’s fees request:
```raw
GET https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388/fees
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

...

{
  "transactions": [
    {
      "_links": {
        "self": {
          "href": "https://api-sandbox.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e"
        },
        "source": {
          "href": "https://api-sandbox.dwolla.com/customers/b442c936-1f87-465d-a4e2-a982164b26bd"
        },
        "destination": {
          "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b"
        },
        "created-from-transfer": {
          "href": "https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388"
        }
      },
      "id": "416a2857-c887-4cca-bd02-8c3f75c4bb0e",
      "status": "pending",
      "amount": {
        "value": "2.00",
        "currency": "usd"
      },
      "created": "2016-02-22T20:46:38.777Z"
    },
    {
      "_links": {
        "self": {
          "href": "https://api-sandbox.dwolla.com/transfers/e58ae1f1-7007-47d3-a308-7e9aa6266d53"
        },
        "source": {
          "href": "https://api-sandbox.dwolla.com/customers/b442c936-1f87-465d-a4e2-a982164b26bd"
        },
        "destination": {
          "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b"
        },
        "created-from-transfer": {
          "href": "https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388"
        }
      },
      "id": "e58ae1f1-7007-47d3-a308-7e9aa6266d53",
      "status": "pending",
      "amount": {
        "value": "1.00",
        "currency": "usd"
      },
      "created": "2016-02-22T20:46:38.860Z"
    }
  ],
  "total": 2
}
```

```php
<?php
$transferUrl = 'https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388';

$transfersApi = new DwollaSwagger\TransfersApi($apiClient);

$transferFees = $transfersApi->getFeesBySource($transferUrl);
$transferFees->total; # => "2"
?>
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
transfer_url = "https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388"

fees = app_token.get "#{transfer_url}/fees"
fees.total # => 2
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
transfer_url = 'https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388'

fees = app_token.get('%s/fees' % transfer_url)
fees.body['total'] # => 2
```

```javascript
var transferUrl = 'https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388';

appToken
  .get(`${transferUrl}/fees`)
  .then(res => res.body.total); // => 2
```
### Reconciling fees

Since a fee is a separate transfer in itself, it will show up in the transfer listing of either the [Account](https://docs.dwolla.com/#list-and-search-transfers-for-an-account) or [Customer](https://docs.dwolla.com/#list-and-search-transfers-for-a-customer) resource, depending on which party is sending or receiving the fee. To correlate a fee to the transfer that the fee was charged on, a key of `created-from-transfer` will be returned in the list of links on a unique transfer resource. The `created-from-transfer` key can also be used to differentiate a fee from other transfer types.

**Refunding fees:**
Within the Dwolla API, an endpoint does not exist to `refund` a processed transfer from the receiving user or account back to the sending party—this includes fees if any were charged.  Refunds occur by the destination user initiating a separate transfer in reverse from the funding source in which they received the funds. As a facilitator who received funds from the fee, you must determine if the charged user will incur the cost of the fee or be refunded for the original fee amount charged.

```raw
GET https://api-sandbox.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

...

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e"
    },
    "source": {
      "href": "https://api-sandbox.dwolla.com/customers/b442c936-1f87-465d-a4e2-a982164b26bd"
    },
    "destination": {
      "href": "https://api-sandbox.dwolla.com/accounts/ca32853c-48fa-40be-ae75-77b37504581b"
    },
    "created-from-transfer": {
      "href": "https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388"
    }
  },
  "id": "416a2857-c887-4cca-bd02-8c3f75c4bb0e",
  "status": "processed",
  "amount": {
    "value": "2.00",
    "currency": "usd"
  },
  "created": "2016-02-22T20:46:38.777Z"
}
```

```php
<?php
$transferUrl = 'https://api-sandbox.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e';

$transfersApi = new DwollaSwagger\TransfersApi($apiClient);

$transfer = $transfersApi->byId($transferUrl);
$transfer->_links->created-from-transfer; # => "https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388"
?>
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
transfer_url = "https://api.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e"

transfer = app_token.get transfer_url
transfer._links.created-from-transfer # => "https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388"
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
transfer_url = 'https://api-sandbox.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e'

transfer = app_token.get(transfer_url)
transfer.body['_links']['created-from-transfer'] # => 'https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388'
```

```javascript
var transferUrl = 'https://api-sandbox.dwolla.com/transfers/416a2857-c887-4cca-bd02-8c3f75c4bb0e';

appToken
  .get(transferUrl)
  .then(res => res.body._links.created-from-transfer); // => 'https://api-sandbox.dwolla.com/transfers/83eb4b5e-a5d9-e511-80de-0aa34a9b2388'
```
