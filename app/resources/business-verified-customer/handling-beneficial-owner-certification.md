---
layout: twoColumn
section: Business Verified Customer
type: article
title:  "Certifying beneficial ownership"
weight: 4
description: "How to certify your Beneficial Owners in order for your business Verified Customer to send funds in the Dwolla's ACH API."
---
# Certifying beneficial ownership

In order for your business verified Customer to send and receive funds, the individual creating the business verified Customer account must certify the beneficial owner(s). By certifying that all the information is correct, the requirements imposed by the United States Federal customer due diligence rule and Dwolla will be successfully fulfilled. Your business verified Customer will now be able to send and receive funds in the Dwolla network.

#### Possible Certification Statuses

| certification_status | Description       |
|----------------------|-------------------|
| Uncertified          | New business verified Customers. Uncertified business verified Customers are unable to transact. |
| Recertify            | Business verified Customers that are certified and change owner information, OR Business verified Customers that Dwolla needs to obtain more information from |
| Certified            | Changed to this status on certification.  |

## Update certification status

To change the certification status of your business verified Customer account, you will want to POST to the beneficial ownership endpoint. By updating your certification status to `certified`, the Account Admin creating the business verified Customer is indicating that all information is correct. After the Account Admin certifies that the information provided is accurate and the information the Account Admin provided has been verified through the identity verified process, your business verified Customer is now ready to transact within the Dwolla network.

```raw
POST https://api-sandbox.dwolla.com/customers/56502f7a-fa59-4a2f-8579-0f8bc9d7b9cc/beneficial-ownership
Accept: application/vnd.dwolla.v1.hal+json
Content-Type: application/vnd.dwolla.v1.hal+json
Authorization: Bearer pBA9fVDBEyYZCEsLf/wKehyh1RTpzjUj5KzIRfDi0wKTii7DqY

{
  "status": "certified"
}
```

```php
No example for this language yet.
```

```ruby
# Using DwollaV2 - https://github.com/Dwolla/dwolla-v2-ruby
customer_url = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909'
request_body = {
  :status => "certified"
}

app_token.post "#{customer_url}/beneficial-ownership", request_body
```

```python
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
customer_url = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909'
request_body = {
    "status": "certified"
}

app_token.post('%s/beneficial-ownership' % customer_url, request_body)

```

```javascript
# Using dwollav2 - https://github.com/Dwolla/dwolla-v2-python
customer_url = 'https://api-sandbox.dwolla.com/customers/e52006c3-7560-4ff1-99d5-b0f3a6f4f909'
request_body = {
    "status": "certified"
}

app_token.post('%s/beneficial-ownership' % customer_url, request_body)
```

## Handling `recertify` status

If you have are adding or changing beneficial owners tied to a business verified Customer account, the certification status changes to `recertify`. 

To update, you will need to remove your beneficial owner and re-add each beneficial owner, including  the necessary identity verification information.

When changing beneficial owners, your `certification_status` will change from `certified` to `recertify`. When in `recertify` status, you will have up to thirty days to update and verify your beneficial owners’ information and update your status to `certified`. If you are unable to update your status within this time, the business verified Customer will have its `certification_status` changed to `uncertified`, leaving the Customer unable to transact.