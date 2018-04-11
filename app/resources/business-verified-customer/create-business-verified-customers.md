---
layout: twoColumn
section: Business Verified Customer
type: article
title:  "Creating Business verified Customers"
weight: 1
description: "How to create a business customer before sending a bank transfer with Dwolla's ACH API."
---
# Creating Business verified Customers

## The basics

To create a business verified Customer, use the [Create a Customer](https://docsv2.dwolla.com/#create-a-customer) endpoint. A business verified Customer is determined by setting the value of the `type` of request parameter to `business` and including any additional fields required for identifying the business, as well as the Controller of the business.

#### Key Terms

* **Beneficial owner** - Any natural person who, directly or indirectly, owns 25% or more of the equity interests of the company.
* **Controller** - Any natural individual who holds significant responsibilities to control, manage, or direct a company or other corporate entity (i.e. CEO, CFO, General Partner, President, etc). A company may have more than one controller, but only one controller’s information must be collected.
* **Rep** - The representative creating the business verified Customer on behalf of the business and Controller.
* **EIN** - Employer Identification Number - A unique identification number that is assigned to a business entity so that they can easily be identified by the Internal Revenue Service.
* **TIN** - Taxpayer Identification Number - An identifying number used for tax purposes in the United States. ... A TIN may be: a Social Security number (SSN) an Individual Taxpayer Identification Number (ITIN) an Employer Identification Number (EIN)
* **VCR** - Verified Customer - A Customer that is created in the Dwolla network and is identity verified

## Events

As a developer, you can expect these events to be triggered when a business verified Customer is successfully created and systematically verified:

1. `customer_created`
2. `customer_verified`

## Create a Business Verified Customer

### Request Parameters - Create a business verified Customer and controller

In order to create a business verified Customer, Dwolla requires information on both the business and the controller. Your business verified Customer Rep will act as the authorized representative of the business. When going through the Customer creation flow, your business verifed Customer Rep will only need information on one controller to successfully complete the signup flow.

| Parameter | Required | Type | Description |
| ---------------|--------------|--------|----------------|
| firstName | yes | string | The legal first name of the Rep or individual signing up the business verified Customer |
| lastName | yes | string | The legal last name of the Rep or individual signing up the business verified Customer |
| email | yes | string | email |
| ipAddress | no | string | ipAddress is recommended |
| businessName | yes | string | Registered business name. |
| doingBusinessAs | no | string | Alternative business name. |
| businessType | yes | string | Business structure. Possible values are `corporation`, `llc`, `partnership`, and `soleProprietorship`. |
| businessClassification| yes | string | The industry classification Id that corresponds to Customer’s business. [Reference our Dev Docs](https://docsv2.dwolla.com/#list-business-classifications) to learn how to generate this Id. |
| ein | yes | string | Employer Identification Number. **Note:** If the `businessType` is `soleProprietorship`, then ein can be omitted from the request. |
| address1 | yes | string | Street number, street name of business’ physical address. |
| address2 | no | string | Apartment, floor, suite, bldg. # of business’ physical address |
| city| yes | string | City of business’ physical address. |
| state| yes | string | Two-letter US state or territory abbreviation code of business’ physical address. For two-letter abbreviation reference, check out the [US Postal Service guide](https://pe.usps.com/text/pub28/28apb.htm). |
| postalCode | yes| string | Business’ US five-digit ZIP or ZIP + 4 code. |
| website | no | string | Businesss’ website |
| controller | conditional | object | A controller JSON object. Controllers are not required if `businessType` is `soleProprietorship`|

### Controller JSON object

| Parameter | Required | Type | Description |
| ---------------|--------------|--------|----------------|
| firstName | yes  |  String |  The legal first name of the controller. |
| lastName | yes  |  String |  The legal last name of the controller. |
| title | yes | String | Job title of the Customer’s Controller.  IE - Chief Financial Officer |
| dateOfBirth | yes  |  String |  The date of birth of the controller. Formatted in YYYY-MM-DD format. Must be 18 years or older. |
| SSN | conditional  |  String | Last four-digits of Controller’s social security number. Required for Controllers who reside in the United States  |
| address | yes | object | An address JSON object. Full address of the controller's physical address. |
| passport | contidtional | object | An optional passport JSON object. Required for non-US individuals. Includes passport identification number and country. |

### Controller address JSON object

| Parameter | Required | Type | Description |
| ---------------|--------------|--------|----------------|
| address1 | yes | string | Street number, street name of Controller’s physical address. |
| address2 | no | string | Apartment, floor, suite, bldg. # of Controller’s physical address. |
| address3 | no | string | Third line of the street address of the Controller's physical address. |
| city | yes | string | City of Controller’s physical address. |
| stateProvinceRegion | yes | string | Two-letter US state or territory abbreviation code of controller’s physical address. For two-letter abbreviation reference, check out the [US Postal Service guide](https://pe.usps.com/text/pub28/28apb.htm). |
| postalCode | no | string | Controller’s’ US five-digit ZIP or ZIP + 4 code. |
| country | yes | string | Country of Controller’s physical address |

### Controller passport JSON object

| Parameter | Required | Type | Description |
| ---------------|--------------|--------|----------------|
| number | conditional | string | Required for a non-U.S. person who has no Social Security number. |
| country | conditional | string | Country of issued passport. |

Once you submit this request, Dwolla will perform some initial validation to check for formatting issues such as an invalid date of birth, invalid email format, etc. If successful, the response will be a HTTP 201/Created with the URL of the new Customer resource contained in the Location header.

#### Request and response

```raw
POST https://api-sandbox.dwolla.com/customers
Content-Type: application/vnd.dwolla.v1.hal+json
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer 0Sn0W6kzNic+oWhDbQcVSKLRUpGjIdl/YyrHqrDDoRnQwE7Q

{
    "firstName": "Jane",
    "lastName": "Merchant",
    "email": "mybusiness@email.com",
    "ipAddress": "143.156.7.8",
    "type": "business",
    "address1": "99-99 33rd St",
    "city": "Some City",
    "state": "NY",
    "postalCode": "11101",
    "dateOfBirth": "1980-01-01",
    "controller": {
        "firstName": "John",
        "lastName": "Controller",
        "title": "CEO",
        "dateOfBirth": "02/19/1990",
        "ssn": "123-45-6789"
        "address": {
            "address1": "1749 18th st",
            "address2": "apt 12",
            "city": "Des Moines",
            "stateProvinceRegion": "IA",
            "postalCode": "50266",
            "country": "United States"
        }
    }
    "phone": "5554321234",
    "businessClassification": "9ed3f670-7d6f-11e3-b1ce-5404a6144203",
    "businessType": "llc",
    "businessName":"Jane Corp",
    "ein":"00-0000000"
}

HTTP/1.1 201 Created
Location: https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5
```

```php
<?php
$customersApi = new DwollaSwagger\CustomersApi($apiClient);

$new_customer = $customersApi->update([
  'firstName' => 'Jane',
  'lastName' => 'Merchant',
  'email' => 'janeMerchant@email.com',
  'type' => 'business',
  'address1' => '99-99 33rd St',
  'city' => 'Some City',
  'state' => 'NY',
  'postalCode' => '11101',
  'controller' {
      'firstName' => 'John',
      'lastName'=> 'Controller',
      'title' => 'CEO',
      'dateOfBirth' => '02/19/1990',
      'ssn': '1234'
      'address' {
          'address1' => '18749 18th st',
          'address2' => 'apt 12',
          'city' => 'Des Moines',
          'stateProvinceRegion' => 'IA',
          'postalCode' => '50265',
          'country' => 'United States'
      }
  }
  'phone': '5554321234',
  'businessClassification': '9ed3f670-7d6f-11e3-b1ce-5404a6144203',
  'businessType': 'llc',
  'businessName':'Jane Corp',
  'ein':'00-0000000'
], $customerUrl);
print($new_customer); # => https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5
?>
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
request_body = {
  :firstName => 'Jane',
  :lastName => 'Merchant',
  :email => 'janeMerchant@email.com',
  :type => 'business',
  :address1 => '99-99 33rd St',
  :city => 'Some City',
  :state => 'NY',
  :postalCode => '11101',
  :controller => {
      :firstName => 'John',
      :lastName => 'Controller',
      :title => 'CEO',
      :dateOfBirth => '02/19/1990',
      :ssn => '1234'
      :address => {
        :address1 => '1749 18th st',
        :address2 => 'apt 12',
        :city => 'Des Moines',
        :stateProvinceRegion => 'IA',
        :postalCode => '50266',
        :country => 'United States',
      }
  }
  :phone => '5554321234',
  :businessClassification => '9ed38155-7d6f-11e3-83c3-5404a6144203',
  :businessType => 'llc',
  :businessName => 'Jane Corp',
  :ein => '12-3456789'
}

customer = app_token.post "customers", request_body
customer.response_headers[:location] # => "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5"
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
request_body = {
  'firstName': 'Jane',
  'lastName': 'Merchant',
  'email': 'janeMerchant@email.com',
  'type': 'business',
  'address1': '99-99 33rd St',
  'city': 'Some City',
  'state': 'NY',
  'postalCode': '11101',
  'controller': {
      'firstName': 'John',
      'lastName': 'Controller',
      'title': 'CEO',
      'dateOfBirth': '02/19/1990',
      'ssn': '1234'
      'address': {
        'address1': '1749 18th st',
        'address2': 'apt12',
        'city': 'Des Moines',
        'stateProvinceRegion': 'IA',
        'postalCode': '50266',
        'country': 'United States'
      }
  }
  'phone': '5554321234',
  'businessClassification': '9ed38155-7d6f-11e3-83c3-5404a6144203',
  'businessType': 'llc',
  'businessName': 'Jane Corp',
  'ein': '12-3456789'
}
customer = app_token.post('customers', request_body)
customer.headers['location'] # => 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5'
```

```javascript
var requestBody = {
  firstName: 'Jane',
  lastName: 'Merchant',
  email: 'janeMerchant@email.com',
  type: 'business',
  address1: '99-99 33rd St',
  city: 'Some City',
  state: 'NY',
  postalCode: '11101',
  controller: {
      firstName: 'John',
      lastName: 'Controller',
      title: 'CEO',
      dateOfBirth: '02/19/1990',
      ssn: '1234'
      address: {
        address1: '1749 18th st', 
        address2: 'apt 12',
        city: 'Des Moines',
        stateProvinceRegion: 'IA',
        postalCode: '50266',
        country: 'United States'
      }
  }
  phone: '5554321234',
  businessClassification: '9ed38155-7d6f-11e3-83c3-5404a6144203',
  businessType: 'llc',
  businessName: 'Jane Corp',
  ein: '12-3456789'
};
appToken
  .post('customers', requestBody)
  .then(res => res.headers.get('location')); // => 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5'
```

## Check the status of the business Customer

You have created a business verified Customer; however, the successful creation of a business verified Customer and Controller doesn’t necessarily mean the Customer is verified. Businesses may need to provide additional information to help verify their identity. It is important to immediately check the status of the business Customer to determine if additional documentation is needed.

#### Request and response

```raw
GET https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

{
    "_links": {
        "deactivate": {
            "href": "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "customer"
        },
        "self": {
            "href": "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "customer"
        },
        "receive": {
            "href": "https://api-sandbox.dwolla.com/transfers",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "transfer"
        },
        "edit-form": {
            "href": "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5",
            "type": "application/vnd.dwolla.v1.hal+json; profile=\"https://github.com/dwolla/hal-forms\"",
            "resource-type": "customer"
        },
        "edit": {
            "href": "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "customer"
        },
        "funding-sources": {
            "href": "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5/funding-sources",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "funding-source"
        },
        "transfers": {
            "href": "https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5/transfers",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "transfer"
        },
        "send": {
            "href": "https://api-sandbox.dwolla.com/transfers",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "transfer"
        }
    },
    "id": "62c3aa1b-3a1b-46d0-ae90-17304d60c3d5",
    "firstName": "Jane",
    "lastName": "Merchant",
    "email": "janeMerchant@email.com",
    "type": "business",
    "status": "verified",
    "created": "2017-12-11T15:17:44.683Z",
    "address1": "99-99 33rd St",
    "city": "Some city",
    "state": "NY",
    "postalCode": "11101",
    "businessName": "Jane Corp"
}
```

```php
<?php
$customerUrl = 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5';

$customersApi = new DwollaSwagger\CustomersApi($apiClient);

$customer = $customersApi->getCustomer($customerUrl);
$customer->status; # => "verified"
?>
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby (Recommended)
customer_url = 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5'

customer = app_token.get customer_url
customer.status # => "verified"
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python (Recommended)
customer_url = 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5'

customer = app_token.get(customer_url)
customer.body['status']
```

```javascript
var customerUrl = 'https://api-sandbox.dwolla.com/customers/62c3aa1b-3a1b-46d0-ae90-17304d60c3d5';

appToken
  .get(customerUrl)
  .then(res => res.body.status); // => 'verified'
```

You will want to ensure that both your Controller and your Business have been verified, as the Customer will be unable to send or receive funds until then. If your controller or the business is in `retry` or `document`, head to our next article to learn how to handle this status.

* * *

#### Next steps

* [Handling business verified Customer statuses](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
* [Adding beneficial owner(s)](/resources/business-verified-customer/adding-beneficial-owners.html)
* [Certifying beneficial owner(s)](/resources/business-verified-customer/handling-beneficial-owner-certification.html)
