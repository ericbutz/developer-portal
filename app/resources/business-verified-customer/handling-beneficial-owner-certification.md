---
layout: twoColumn
section: Business Verified Customer
type: article
title:  "Certifying beneficial ownership"
weight: 4
description: "How to certify your Beneficial Owners in order for your business Verified Customer to send funds in the Dwolla's ACH API."
---
# Certifying beneficial ownership

In order for your business verified Customer to be eligible to send and receive funds, the individual creating the business verified Customer account must certify beneficial owner(s). By certifying that all beneficial owner information is correct, the requirements imposed by the United States Federal customer due diligence rule and Dwolla will be successfully fulfilled.

Certification of beneficial owners should be included as part of the Customer account registration and immediately following the creation of the business Verified Customer and the addition of all owners (unless exempt).

#### Certification Statuses

| certification_status | Description       |
|----------------------|-------------------|
| uncertified          | New business verified Customers that are not exempt are initially placed in an uncertified status. Uncertified business verified Customers are unable to transact. |
| recertify            | Business verified Customers that are certified and change owner information, OR Business verified Customers that Dwolla needs to obtain more information from relating to beneficial owners are placed in a recertify status. |
| certified            | Confirms the certification of beneficial owners. |

## Certify ownership

To change the certification status of your business verified Customer account, you will want to POST to the beneficial ownership endpoint. By updating the certification status to `certified`, the Account Admin creating the business verified Customer is indicating that all information is correct. After the Account Admin certifies that the information provided is accurate and the information the Account Admin submitted has been verified through the identity verified process, your business verified Customer is now ready to transact within the Dwolla network.

```raw
POST https://api-sandbox.dwolla.com/customers/56502f7a-fa59-4a2f-8579-0f8bc9d7b9cc/beneficial-ownership
Accept: application/vnd.dwolla.v1.hal+json
Content-Type: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

{
  "status": "certified"
}

...

{
    "_links": {
        "self": {
            "href": "https://api-sandbox.dwolla.com/customers/56502f7a-fa59-4a2f-8579-0f8bc9d7b9cc/beneficial-ownership",
            "type": "application/vnd.dwolla.v1.hal+json",
            "resource-type": "beneficial-ownership"
        }
    },
    "status": "certified"
}
```
```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
customer_url = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909'
request_body = {
  :status => "certified"
}

app_token.post "#{customer_url}/beneficial-ownership", request_body
```
```javascript
var customerUrl = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909';
var requestBody = {
  status: 'certified'
};

appToken.post(`${customerUrl}/beneficial-ownership`, requestBody);
```
```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
customer_url = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909'
request_body = {
    "status": "certified"
}

app_token.post('%s/beneficial-ownership' % customer_url, request_body)
```
```php
<?php
$customersApi = new DwollaSwagger\CustomersApi($apiClient);
$customerId = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909';
$certifyCustomer = $customersApi->changeOwnershipStatus(['status' => 'certified' ], $customerId);
?>
```

## Handling `recertify` status

If you are adding, removing, or updating information of beneficial owners tied to a business verified Customer account, the certification status will change to `recertify`.

Instances that you will see your `certified` business verified Customer change to `recertify` are as follows:

* Adding a beneficial owner
* Removing a beneficial owner
* Updating a beneficial owner in `incomplete` status
* Uploading a document to a beneficial owner

When a Customer has a `recertify` beneficial ownership status, they will have up to thirty days to update and verify their beneficial owners’ information and update their status to `certified`. If the certification status isn't updated within this timeframe, the business verified Customer will have its `certification_status` changed to `uncertified`, leaving the Customer unable to transact.

* * *

#### Review previous steps

* [Creating business verified Customer](/resources/business-verified-customer/create-business-verified-customers.html)
* [Handling business verified Customer statuses](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
* [Adding beneficial owner(s)](/resources/business-verified-customer/adding-beneficial-owners.html)
