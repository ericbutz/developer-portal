---
layout: twoColumn
section: guides
type: guide
guide:
    name: webhooks
    step: overview
title: Webhooks issue notifications
description: A webhook is a means of notifying a third-party application of the occurrence of an event with some relevant information.
---

# Overview: Webhooks

A webhook is a means of notifying a third-party application of the occurrence of an event with some relevant information. In the Dwolla API, webhooks are currently triggered by the following resources:

- Customers
- Beneficial Owners
- Documents
- Funding Sources
- Transfers
- Mass Payments

Each webhook sent by the Dwolla API contains an `Event` with `_links` to: the associated resource, account associated with the event, and the customer associated with the event (if applicable). It is important to note that a single API request can trigger multiple webhooks to be fired. For example, initiating a transfer between two different `Customers` can create `customer_transfer_created` webhooks for both customers involved in the transaction.

<ol class = "alerts">
    <li class="alert icon-alert-alert">
      Webhooks are sent asynchronously and are not guaranteed to be delivered in order. We recommend that applications protect against duplicated events by making event processing idempotent.
    </li>
</ol>

### Example webhook payload
```jsonnoselect
{
  "id": "bb6531a2-5b13-4815-a83d-ed7a1fc70bd8",
  "resourceId": "6c57f372-e9a0-47d4-91f3-ab2b3aae56f0",
  "topic": "customer_created",
  "created": "2019-02-04T14:58:45.144Z",
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/events/bb6531a2-5b13-4815-a83d-ed7a1fc70bd8"
    },
    "account": {
      "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
    },
    "resource": {
      "href": "https://api-sandbox.dwolla.com/customers/6c57f372-e9a0-47d4-91f3-ab2b3aae56f0"
    },
    "customer": {
      "href": "https://api-sandbox.dwolla.com/customers/6c57f372-e9a0-47d4-91f3-ab2b3aae56f0"
    }
  }
}
```

<nav class="pager-nav">
    <a href="" style="display:none;"></a>
    <a href="obtain-authorization.html">Next: Obtain authorization</a>
</nav>
