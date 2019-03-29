---
layout: twoColumn
section: resources
type: article
title:  Business verified customer
description: A business verified Customer represents a business that intends to send or receive funds on your platform.
---
# Business Customer Verification

This article will walk through the identity verification process for [business verified Customers](https://developers.dwolla.com/resources/account-types.html) within the Dwolla API.

## The basics

A business verified Customer represents a business that intends to send or receive funds on your platform. In any transaction, at least one party—either the sender or the receiver—must complete the [identity verification](https://www.dwolla.com/updates/guide-to-cip-customer-identification-program-dwolla-payments-api/) process as outlined in this article.

### Key Terminology

* **Account Admin** - The representative creating the business verified Customer on behalf of the business and Controller.
* **Controller** - Any natural individual who holds significant responsibilities to control, manage, or direct a company or other corporate entity (i.e. CEO, CFO, General Partner, President, etc). A company may have more than one controller, but only one controller’s information must be collected.
* **Beneficial owner** - Any natural person who, directly or indirectly, owns 25% or more of the equity interests of the company.
* **Beneficial ownership certification** - An action taken by the Account Admin to confirm that the information provided is correct.
* **EIN (Employer Identification Number)** - A unique identification number that is assigned to a business entity so that they can easily be identified by the Internal Revenue Service.
* **TIN (Taxpayer Identification Number)** - An identifying number used for tax purposes in the United States. A TIN may be: a Social Security number (SSN) an Individual Taxpayer Identification Number (ITIN) an Employer Identification Number (EIN).

## Business Verified Customer Quick Guide

| My Customer's business structure | Will sign up in Dwolla as | Are they required to add beneficial owners? | Are they required to add certify beneficial ownership? |
|----------------------------------|---------------------------|---------------------------------------------|--------------------------------------------------------|
| **Sole proprietorships**         | *soleProprietorship*      | No (exempt)                                 | No (exempt)                                            |
| **Unincorporated association**   | *soleProprietorship*      | No (exempt)                                 | No (exempt)                                            |
| **Trust**                        | *soleProprietorship*      | No (exempt)                                 | No (exempt)                                            |
| **Corporation**                  | *corporation*             | Yes (if owns 25% or more)                   | Yes                                                    |
| **Public corporations**          | *corporation*             | No (exempt)                                 | Yes                                                    |
| **Non-profits**                  | *corporation* or *llc*    | No (exempt)                                 | Yes                                                    |
| **LLCs**                         | *llc*                     | Yes (if owns 25% or more)                   | Yes                                                    |
| **Partnerships, LP's,  LLP's**   | *partnership*             | Yes (if owns 25% or more)                   | Yes                                                    |

## Steps for onboarding a Business verified Customer

Reference the steps below for guidance on getting your business verified Customer in a transaction-eligible state.

1. [**Creating business verified Customer**](/resources/business-verified-customer/create-business-verified-customers.html)
 * Create the Customer record
 * Check the status of the business and Controller
2. [**Handling business verified Customer statuses**](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
 * Handle `retry`, `document`, and `suspended` statuses
3. [**Adding beneficial owner(s)**](/resources/business-verified-customer/adding-beneficial-owners.html)
 * Determine if you need to add a beneficial owner to your Customer
 * Add a beneficial owner(s) to the Customer
 * Handle `incomplete` and `document` statuses
4. [**Certifying beneficial owner(s) information**](/resources/business-verified-customer/handling-beneficial-owner-certification.html)
 * Determine if you need to certify beneficial ownership for your Customer
 * Certify beneficial ownership
5. [**Certifying beneficial owner(s) information**](/resources/business-verified-customer/frequently-asked-questions.html)
 * A reference article to answer common questions about business verified Customers


* * *

#### Next steps:

* [Creating business verified Customer](/resources/business-verified-customer/create-business-verified-customers.html)
* [Handling business verified Customer statuses](/resources/business-verified-customer/handling-controller-and-customer-statuses.html)
* [Adding beneficial owners](/resources/business-verified-customer/adding-beneficial-owners.html)
* [Certifying beneficial owner(s)](/resources/business-verified-customer/handling-beneficial-owner-certification.html)
* [Frequently Asked Questions](/resources/business-verified-customer/frequently-asked-questions.html)