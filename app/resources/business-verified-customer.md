---
layout: twoColumn
section: resources
type: article
title:  "Business Verified Customer"
description: "How to create and verify a Business customer before sending a bank transfer with Dwolla's ACH API."
---
# Business Customer Verification

This article will walk through the identity verification process for business verified Customers within the Dwolla API. For more information on going live with the Dwolla Platform, please [contact sales](https://www.dwolla.com/contact).

A business verified Customer represents a business that intends to send or receive funds on your platform. In any transaction, at least one party—either the sender or the receiver—must complete the [identity verification](https://www.dwolla.com/updates/guide-to-cip-customer-identification-program-dwolla-payments-api/) process as outlined in this article.

First, you should have an active [webhook subscription](https://docsv2.dwolla.com/#webhook-subscriptions). This active webhook subscription allows information about a Customer’s `status` during the verification process to be sent asynchronously to your application.

## Procedures for Creating a Business verified Customer

Below we have outlined the verification process for creating a business verified Customer.

1. [**Creating business verified Customer**](/resources/business-verified-customer/create-business-verified-customers.html)
 * Create a business verified Customemr
 * Check the status of the business
 * Check the status of your Controller
2. [**Handling business verified Customer statuses**](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
 * Handle `retry` status
 * Handle `document` status, including document upload
 * Determine if you need to add a beneficial owner to your Customer
3. [**Adding beneficial owner(s)**](/resources/business-verified-customer/adding-beneficial-owners.html)
 * Review which business types are exempt and which are non-exempt
 * Add a beneficial owner(s) to the Customer
 * Check the status of your beneficial owner
4. [**Certifying beneficial owner(s) information**](/resources/business-verified-customer/handling-beneficial-owner-certification.html)
 * Retrieve certification statuses
 * Update certification statuses
 * Handle recertification
 * Overview of transaction abilities by status

* * *

#### Next steps:

* [Creating business verified Customer](/resources/business-verified-customer/create-business-verified-customers.html)
* [Handling business verified Customer statuses](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
* [Adding beneficial owners](/resources/business-verified-customer/adding-beneficial-owners.html)
* [Certifying beneficial owner(s)](/resources/business-verified-customer/handling-beneficial-owner-certification.html)
