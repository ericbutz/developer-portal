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
- Documents
- Funding Sources
- Transfers
- Mass Payments

Each webhook sent by the Dwolla API contains an `Event` with `_links` to: the associated resource, account associated with the event, and the customer associated with the event (if applicable). It is important to note that a single API request can trigger multiple webhooks to be fired, e.g. initiating a transfer from an Account to Customer can create the events `transfer_created` and `customer_transfer_created`.

<ol class = "alerts">
    <li class="alert icon-alert-alert">
      Webhooks are sent asynchronously and are not guaranteed to be delivered in order. We recommend that applications protect against duplicated events by making event processing idempotent.
    </li>
</ol>

### Example webhook payload
```jsonnoselect
{
  "_links": {
      "event": {
          "href": "https://api-sandbox.dwolla.com/events/1097f604-1741-49e0-8f79-6884fee980d1",
          "resource-type": "event",
          "type": "application/vnd.dwolla.v1.hal+json"
      },
      "retry": {
          "href": "https://api-sandbox.dwolla.com/webhooks/2923bcd6-401d-4178-9bbc-ea6dfd7ebbfd/retries",
          "resource-type": "retry",
          "type": "application/vnd.dwolla.v1.hal+json"
      },
      "self": {
          "href": "https://api-sandbox.dwolla.com/webhooks/2923bcd6-401d-4178-9bbc-ea6dfd7ebbfd",
          "resource-type": "webhook",
          "type": "application/vnd.dwolla.v1.hal+json"
      },
      "subscription": {
          "href": "https://api-sandbox.dwolla.com/webhook-subscriptions/affd581a-2206-44ad-8492-ff5350e4991e",
          "resource-type": "webhook-subscription",
          "type": "application/vnd.dwolla.v1.hal+json"
      }
  },
  "accountId": "0ee84069-47c5-455c-b425-633523291dc3",
  "eventId": "1097f604-1741-49e0-8f79-6884fee980d1",
  "id": "2923bcd6-401d-4178-9bbc-ea6dfd7ebbfd",
  "subscriptionId": "affd581a-2206-44ad-8492-ff5350e4991e",
  "topic": "customer_created",
  "attempts": []
}
```

<nav class="pager-nav">
    <a href="" style="display:none;"></a>
    <a href="obtain-authorization.html">Next: Obtain authorization</a>
</nav>
