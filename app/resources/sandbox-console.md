---
layout: twoColumn
section: resources
type: tool
title:  "Sandbox Console"
description: "Set up bank transfers with Dwolla's ACH API in our developer sandbox environment."
---

# What is a Sandbox Console?

Whether you intend to create traditional test accounts, view and manage programmatically created Access API Customers, or manipulate the status of transfers initiated by your application, the Sandbox Console helps simplify your development experience.

There are two consoles designed to support the specific needs of a developer’s application. The key distinction between each console—Access API vs. Standard—is the type of test user associated with your application.

Access the Sandbox Console at: [https://sandbox-uat.dwolla.com](https://sandbox-uat.dwolla.com)

<ol class="alerts">
    <li class="alert icon-alert-info">If you are new to application development with Dwolla, we recommend you review our <a href="/guides/sandbox-setup">Sandbox Setup Guide</a>.</li>
</ol>

### Access API Console vs. Standard Console
Depending on how you interact with test users, you will access the console specific to your application, either the Access API Console or Standard Console. As a developer, determine if you intend to manage the entire end-user experience (Access API) or if you want to leverage the Dwolla Co-branded user experience and associated Dwolla account (Standard). Read our [Account Types article](/resources/account-types.html) for more information on the differences between Access API Customers and traditional Dwolla accounts. **Note:** The Access API is a premium solution and you will need to work directly with Sales prior to activating in production. For more information about the Access API, please [contact sales](https://www.dwolla.com/contact).

![Screenshot of sandbox home](/images/sandbox-console-home.png "Sandbox Console home screen")

## Managing test users

#### Access API Console - Customer
The Access API Console allows you to manage the Customers and transfers associated with the Customers that were generated by your application. Once your application has created its Customers you can access the Access API Console to validate that the request was recorded properly in our test environment. 

![Screenshot of Access API Console](/images/sandbox-console-wl.png "Access API Console")

#### Standard Console - Traditional accounts
Unlike an Access API solution, you are unable to create test accounts from your application. To simplify the testing process, the Standard Console allows you to create test Dwolla accounts and associate funding sources. Once the test accounts have been created, your application can facilitate a transfer of funds to, from, or between test accounts. 

![Screenshot of Standard Console](/images/sandbox-console-standard.png "Standard Console")

## Managing test transfers
In either the Access API or Standard Console, you can view and trigger transfer outcomes of your application. The ability to manage transfers remains the same, whether you are using the Access API or Standard Console. 

#### Transfer behavior in the Sandbox

Unlike balance sourced transfers, which are processed instantaneously, bank-sourced transfers exist in the pending state for a few business days until they are `processed`, `failed`, `cancelled`, or `reclaimed`.

The Sandbox environment does not replicate any ACH processes, so a `pending` transfer will not clear or fail automatically after a few business days as it would in production. It will simply remain in the `pending` state indefinitely.

#### Manipulation

![Screenshot of transfer manipulation](/images/sandbox-console-manipulation.gif "Transfer status manipulation")

The Sandbox Console interface allows you to immediately trigger any of the four possible outcomes for a given transfer: `processed`, `failed`, `cancelled`, `reclaimed`. If subscribed to [webhooks](/guides/webhooks), when a transfer outcome is triggered a webhook will be sent to your server which includes the corresponding created event.

For more information on transfer statuses, read the [bank transfer workflow](/resources/bank-transfer-workflow.html) article.