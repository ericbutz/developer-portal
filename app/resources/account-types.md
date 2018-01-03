---
layout: twoColumn
section: resources
type: article
title:  "Account types"
description: "Getting started with Dwolla's bank transfer API."
---

# Account types

When you are building your application, you’ll want to be aware of the different account types that exist on the Dwolla platform as well as their capabilities.

A Customer account is created programmatically by you, the partner, via the `Customers` endpoint. You can reference our API docs to learn more on how to [create a Customer](https://docsv2.dwolla.com/#create-a-customer). All required account information will be handled through the API and the Customer will interact directly with the you to manage their account.

Regardless of your application type, it’s important to note that in a transfer of money between two parties at least one account must be Customer Identity Program (CIP) verified. It’s your decision about which party completes this process, based on your business model, and you may want to have both parties complete CIP verification. In addition, we also require CIP verification as a part of a customer holding funds in the Dwolla network.

## Customer accounts

##### Verified Customer

This third-party-created account requires additional information to verify the identity of Customer account holder. Since this account type requires additional identity vetting by Dwolla, users need to provide standard Know Your Customer (KYC) information: name, date of birth, address, and last four digits of SSN. In addition to the above, a business account will need to provide business name, business type, and EIN. A Verified Customer account is required when the Partner’s end user needs to hold a Dwolla balance or transact with an Unverified Customer account type. Types of Verified Customers include: Personal or Business.

##### Unverified Customer

An Unverified Customer is a third-party-created account that requires a minimal amount of account data: first name, last name, email address, and IP address. **Note:** Unverified Customer accounts have a default sending transaction limit of $5000 per week. A week is defined as Monday to Sunday.

##### Receive-only Customer

Receive-only Customers are restricted to a “payouts only” business model within the API. A receive-only customer maintains limited functionality in the API and is only eligible to receive transfers to an attached bank account from the partner Dwolla account that created it.
