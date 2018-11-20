---
layout: twoColumn
section: guides
type: guide
guide:
    name: auth
    step: '3'
title: OAuth 2.0 Access Token
description: Once your application obtains an access token in OAuth 2.0 it can be used to access protected resources in the Dwolla API.
---

# Making a request to the Dwolla API

Once your application obtains an access token, it can be used to access protected resources in the Dwolla API.

Here is an example of an API request. Note that OAuth access tokens are passed via the Authorization HTTP header:
`Authorization: Bearer {access_token_here}`

```noselect
POST https://api.dwolla.com/webhook-subscriptions
Content-Type: application/json
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer myApplicationAccessToken

{
    "url": "https://myapplication.com/webhooks",
    "secret": "sshhhhhh"
}

... or ...

GET https://api.dwolla.com/accounts/a84222d5-31d2-4290-9a96-089813ef96b3/transfers
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer myAccountAccessToken
```

Assuming the access token is valid, the Dwolla API will return a success or error response. If the access token is expired or invalid, the API will return an HTTP 401 with either a "InvalidAccessToken" or "ExpiredAccessToken" error. Learn more about making requests in our [API docs](https://docsv2.dwolla.com/#making-requests).


<nav class="pager-nav">
    <a href="./">Back: Overview</a>
</nav>
