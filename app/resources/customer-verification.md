---
layout: twoColumn
section: resources
type: archive
title:  Customer Verification within the Dwolla API
description: A Customer is an individual or business that intends to send or receive funds on your platform and in any transaction, one party must complete identity verification. 
---

# Customer Verification

These articles will walk through the identity verification process for verified Customers within the Dwolla API. For more information on going live with the Dwolla API, please [contact sales](https://www.dwolla.com/contact).

A `Customer` represents an individual or business that intends to send or receive funds on your platform. In any transaction at least one party—either the sender or the recipient—must complete the [identity verification](https://www.dwolla.com/updates/guide-to-cip-customer-identification-program-dwolla-payments-api/) process as outlined in this article. In cases where a Customer is only sending funds to or receiving funds from your full Dwolla account, the Customer is not required to complete the process set out below.

First, you should have an active [webhook subscription](https://docsv2.dwolla.com/#webhook-subscriptions). This active webhook subscription allows information about a Customer’s `status` in the verification process to be sent asynchronously to your application.

## Quick overview

Click on a Customer to learn more on the verification process for both `personal` and `business` Customers.

1. [Personal verified Customer](/resources/personal-verified-customer.html)
 * &#8226; Create a personal verified Customer
 * &#8226; Check the status of the personal Customer
 * &#8226; Handle verification statuses
2. [Business verified Customer](/resources/business-verified-customer.html)
 * &#8226; Create a business verified Customer
 * &#8226; Check the status of the business Customer
 * &#8226; Add beneficial owner
 *
* * *

#### View:

* [Personal verified Customers](/resources/personal-verified-customer.html)
* [Business verified Customers](/resources/business-verified-customer.html)
