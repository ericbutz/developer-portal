---
layout: twoColumn
section: resources
type: tool
title:  "Token Generator"
description: "Generate an OAuth access token for Dwolla's bank transfer API."
---

# Token generator

The Dwolla API requires an OAuth access token for authorization. When getting started with the Dwolla API in the sandbox environment, sometimes you just need an access token for your own account without needing to interact with the API to obtain one.

### Generate an access token for your own Dwolla account

For Sandbox, visit [https://dashboard-sandbox.dwolla.com/applications](https://dashboard-sandbox.dwolla.com/applications).

<img src="/images/token-generator.png" alt="Sandbox Token Generator" style="width: 500px;"/>

Press the **create token** button located beneath an application to generate a token that is issued to that application.

**Important:** Keep in mind that Dwolla’s implementation of the [OAuth 2.0](https://tools.ietf.org/html/rfc6749) standard uses short-lived access tokens. The access token will expire one hour after it’s generated and you will have to generate a new one. Eventually, you'll need to implement a refresh strategy.
