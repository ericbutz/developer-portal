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
  "id": "fe869b23-097b-4c95-9891-cb59c753a895",
  "resourceId": "ac84655e-8d28-e911-8115-c4a646b43d5b",
  "topic": "customer_transfer_completed",
  "created": "2019-02-04T14:58:45.144Z",
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/events/fe869b23-097b-4c95-9891-cb59c753a895"
    },
    "account": {
      "href": "https://api-sandbox.dwolla.com/accounts/ad5f2162-404a-4c4c-994e-6ab6c3a13254"
    },
    "resource": {
      "href": "https://api-sandbox.dwolla.com/transfers/ac84655e-8d28-e911-8115-c4a646b43d5b"
    },
    "customer": {
      "href": "https://api-sandbox.dwolla.com/customers/6c57f372-e9a0-47d4-91f3-ab2b3aae56f0"
    }
  }
}
```

For illustrative purposes, let's assume you are using Ruby on Rails with a controller defined to handle the POST request from Dwolla's servers. Your application logic will look a little something like this:

##### Ruby

```rubynoselect
require 'dwolla_v2'

if params[:topic] == 'customer_transfer_completed'
  transfer = app_token.get (params[:links][:resource][:href])

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
