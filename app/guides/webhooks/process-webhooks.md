---
layout: twoColumn
section: guides
type: guide
guide:
    name: webhooks
    step: '4'
title: Processing webhooks
description: From the event we can retrieve the transfer and then take a look at the links object and retrieve the customers that need to be notified.
---

# Processing webhooks: an example scenario

Let's assume that you have a webhook subscription and Dwolla has just delivered the following payload to your specified endpoint:

##### Sample Payload

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

For illustrative purposes, let's assume you are using Ruby on Rails with a controller defined to handle the POST request from Dwolla's servers. Your application logic will look a little something like this:

##### Ruby

```rubynoselect
require 'dwolla_swagger'

if params[:topic] == 'transfer_completed'
  transfer = DwollaSwagger::TransfersApi.by_id(params[:links][:resource][:href])

  transfer._embedded.each do |k, v|
    # Retrieve customer info from your database
    # or from Dwolla here, and then send notifications
  end
elsif params[:topic] == 'another_event'
  "..."
end
```

Let's recap. From the event we can retrieve the `transfer` and then take a look at the `_links` object and retrieve the `customers` that need to be notified. From here, you can make a call to `customers/{id}` to retrieve their e-mail addresses (or to your own database) so that you can send your notification message.

That's it! You’ve learned the basics of webhooks.

<nav class="pager-nav">
    <a href="./validating-webhooks.html">Back: Validating webhooks</a>
    <a href="" style="display:none;"></a>
</nav>
