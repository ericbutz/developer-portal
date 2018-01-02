---
layout: twoColumn
section: guides
type: guide
guide: 
    name: receive-money
    step: overview
title:  Receive bank transfers within your application
description: Programmatically collect money from customer bank accounts with bank transfers. 
---

# Overview: Receive money from your users

In this guide, we’ll cover the key points of collecting money from your customers by utilizing the Dwolla API.

- Create a sending customer for the funds
- Associate a verified funding source (bank or credit union account) with the customer
- Transfer funds from the customer’s linked funding source (Bank Account)

### Before you begin

You need to have a [Sandbox account](/guides/sandbox-setup) already set up.

### Next step: Onboarding and Customer creation

The first step is to create senders for your transfer, along with a bank funding source where the money will be sent from. Dwolla’s Transfer experience prompts your senders for their bank or credit union account information. Otherwise, if you choose to integrate with the Access API, your application will need to capture these fields to pass through to Dwolla for secure storage.

<nav class="pager-nav">
    <a href="" style="display:none;"></a>
    <a href="/guides/receive-money/dwolla-api-onboarding.html">Get started with the Dwolla API</a>
</nav>