---
layout: twoColumn
section: guides
type: guide
guide:
    name: receive-money
    step: overview
title:  Collecting From Your Users Using Dwolla's API
description: This guide covers the key points of collecting money from your customers by utilizing the Dwolla API.
---

# Receive money from your users

## Overview

This guide is designed to get you up and running quickly through creating a one-time transfer from an end user via the Dwolla API. In this guide, we’ll cover the basics of integrating this lightweight payment flow, receiving funds (also referred to as “pay-ins”), by breaking down the steps to create a bank transfer. For simplicity, we’ll represent a one-to-one transfer between two end users, where the `source` user is the individual or business that has been onboarded as a Dwolla Customer record. The `destination` user is identified as your Master Dwolla Account.

<img src="/images/funds_flow_receive.gif" width="75%" height="75%">

In this quickstart guide, you’ll learn the following key concepts involved with receiving funds from your end user’s bank account:

 1. Choosing and creating the Customer type for your sending Customer
 2. Attaching a funding source (bank account) to the Customer
 3. Fetching the available funding sources
 4. Initiating a transfer from your Customer to your Dwolla Master Account


## Before you begin

We encourage you to create a sandbox account, if you haven’t already. This will allow you to follow along with the steps outlined in this guide. Check out our [Sandbox setup guide](https://developers.dwolla.com/guides/sandbox-setup/) to learn more on creating an account.

After creating a sandbox account, you’ll obtain your API Key and Secret, which are used to obtain an OAuth access token. An access token is required in order to authenticate against the Dwolla API. Learn more about how to [obtain an access token](https://developers.dwolla.com/guides/auth/) in our guide.

Lastly, in this sandbox walkthrough, we recommend having an active webhook subscription. This will help notify your application of various events that occur within the Dwolla API. Check out our guide to [learn more](https://developers.dwolla.com/guides/webhooks/).

Let’s get started!

<nav class="pager-nav">
<a href="" style="display:none;"></a>
<a href="onboarding.html">Next: Customer Onboarding</a>
</nav>
