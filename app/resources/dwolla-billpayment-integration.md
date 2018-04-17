---
layout: twoColumn
section: resources
type: integrations
title:  "Dwolla + Regalii"
description: "Dwolla Platform Partners utilize a tokenized solution with Regalii to integrate bill payment functionality in their application"
published: false
---
# Regalii Integration

Dwolla and Regalii have teamed up to offer a seamless tokenized solution for shared partners, looking to facilitate bill payments within their application. Interaction will occur with both the Regalii and Dwolla APIs in order to successfully create and track the status of a bill payment.

This article is focused specifically on the interaction with the Dwolla API, however, highlights a few details of the Regalii API implementation.

**Please note:** There are no instructions in this article regarding your integration with the Regalii APIs and specifically there are no details in this article about any notifications and webhooks you will receive from Regalii regarding the the final bill payment.

Please review Regalii’s documentation for more information on when Regalii will send you webhooks regarding the final bill payment [webhook details](https://www.regalii.com/api/v3/#when-are-webhooks-sent).

![Screenshot of Dwolla and Regalii Integration](/images/regalii-integration-diagram.png "Dwolla and Regalii Integration")

## Using Regalii + Dwolla

For the purposes of this walkthrough, we’ll assume you’ve familiarized yourself with the [Dwolla API](https://docsv2.dwolla.com) and understand the proper workflow for onboarding your users as [Customers](https://docsv2.dwolla.com/#create-a-customer), including how to attach [verified funding sources](https://developers.dwolla.com/resources/funding-source-verification.html) to those Customers.

In addition, you will want to familiarize yourself with the key concepts of the [Regalii API](https://www.regalii.com/apix/v3/), which includes syncing biller information and initiating the request to pay a bill.

Both Regalii and Dwolla offer fully functional sandbox environments to complete your integration without needing to interact with real user data. It is recommended to obtain API credentials from both services, as well as register a webhook URL for receiving notifications related to bills and bill payments.

## Integration Overview

Below are the steps you will take to successfully enable your bill payment integration:

1. Obtain a bill payment token and enable the integration in the Dwolla dashboard
2. Retrieve a list of billers and connect a Customer with their biller account
3. A customer authorizes and requests for your application to create a bill payment using a Dwolla funding source ID
4. Track the status of a bill payment within the Dwolla platform with transfer webhooks sent from Dwolla. You will need to interact with Regalii’s API to receive all other transfer webhooks.

The first step in enabling your bill payment integration is linking the two solutions together (Dwolla and Regalii) through obtaining a bill payment token from the Regalii API and submitting it in the Dwolla dashboard. Let’s get started!

### Step 1 - Obtain a bill payment token and enable integration in Dwolla dashboard

To configure the bill payment integration you will need to obtain a unique token from the Regalii API, which will be used by Dwolla to identify your account with Regalii. This is only performed one time as part of the initial setup process. The response from the Regalii API will include a “dwolla” JSON object that contains a billpayment_token parameter. As an example:

`{"dwolla":{"billpayment_token":"1e54f94af312f3b1c09633820e6a2ea2c16f2c0f"}}`

You will [use the Dwolla dashboard](https://dashboard-sandbox.dwolla.com/account/integrations) to enable the integration. Once the integration is enabled in the dashboard, Dwolla will exchange information with Regalii to ensure a secure connection is established.

##### Integration detail: Read-only Customer

If the token exchange from Dwolla to Regalii is successful, Dwolla will then systematically create a read-only [Customer](https://docsv2.dwolla.com/#customers) account for Regalii’s bank that will be used as the Regalii Destination Account for all bill payments. When retrieving a transfer relating to a bill payment from the Dwolla API, the read-only Customer will be visible as the destination Customer account in the transfer.

### Step 2 - Retrieve list of billers and select biller to pay

In this step you will interact with the Regalii API and provide your end-users with the ability to select from a list of billers. This list should be stored by your application and updated periodically for syncing biller information over time.

The list of billers will include information about the biller, such as address and type, as well as information that is needed for creating a bill payment request, such as `biller ID` and `mask_format`. You have to make sure the `account_number` in the request to create a bill payment transaction matches one of the `mask_formats` for a selected RPPS biller.

### Step 3 - Create a bill payment using a Dwolla Customer’s funding source ID

Now that your customer has selected the biller they want to pay, you are ready to call the Regalii API to create the bill payment transaction. There are a few fields required in order to create the bill payment transaction, which include: the Dwolla Customer’s funding source ID (identifies the end-user's bank), an `rpps_biller_id`, `account_number`, `amount`, and `currency`; as well information about the customer such as `date of birth`, `full name`, and `address` (optional).

#### Request and response

```noselect
POST https://apix.casiregalii.com/transactions
Content-MD5: {MD5}
Authorization: APIAuth { {RegaliiAPIKey}:{CHECKSUM}}
Date: Mon, 19 Mar 2018 14:20:57 GMT
Content-Type: application/json
Accept: application/vnd.regalii.v3.2+json

{
  “dwolla_funding_source_id”: “c91d6516-1855-4d36-be7c-bc78cc7c52c3”
  "account_number": "12345678998",
  "amount": "2000.0",
  "currency": "USD",
  "payer_born_on": "1991-01-05"
  "phone_number": "(714) 202-5081",
  "client_number": "805-612-0442",
  "first_name": "Jane",
  "last_name": "Doe",
  "rpps_biller_id": "12345678-de6b-4d5f-a14b-77df55ae5e55",
  "address": {
    "street": "123 Main St",
    "zip_code": "12345",
    "city": "New York"
    “state”: “NY”
  }
}
```

<ol class = "alerts">
    <li class="alert icon-alert-info">
The `client_number` is a unique identifier for the customer making the bill payment. It is recommended that a phone number is used as the value of `client_number`.
  </li>
</ol>

Upon success, the response from the Regalii API will include a transaction ID and an preliminary status of `initialized`, which represents representing that the transaction was created in the Regalii system and is pending transfer creation through Dwolla.

#### Example Response

```noselect
{
    "id": "5969ae86-8e88-4daf-8936-ad84a9d1cc30",
    "status": "initialized",
    "bill_id": null,
    "account_number": "12345678998",
    "currency": "USD",
    "amount": "88.70",
    "created_at": "2018-01-11T19:42:48.439Z",
    "updated_at": "2018-01-11T19:42:48.439Z",
    "error_code": null,
    "error_message":null
  }
```

If the bill payment through Dwolla is unsuccessful, you will see an `error_code` and `error_message` in the transaction’s response.

### Step 4 - Track the status of a bill payment with webhooks triggered from Dwolla

When a bill payment is successfully created through Dwolla, you’ll want to track the status of the transfer created from the bill payment request. Dwolla and Regalii will have different transaction statuses, so it’s important to understand the differences between those statuses and when they can be returned from created to completion.

Here is the complete list of Dwolla's transaction statuses and how they map to each other, along with the corresponding Dwolla event that’s triggered when a Dwolla transfer status changes:

| Regalii transaction status | Dwolla transfer status | Dwolla event |
|----------------------------|------------------------|--------------|
| Initialized                | N/A                    | N/A          |
| Pending                    | N/A                    | N/A          |
| Linked                     | Pending                | `customer_bill_payment_created` <br> `customer_transfer_created` |
| Confirmed                  | Processed              | `customer_bill_payment_completed` <br> `customer_transfer_completed` |
| Rejected                   | Failed                 | `customer_bill_payment_failed` <br> `customer_transfer_failed` |

As referenced above, Regalii will return a transaction id along with a status of “initialized”, which is the status prior to when any [transfer](https://docsv2.dwolla.com/#transfers) is created within the Dwolla API.

Once the transfer is successfully created within the Dwolla system, the Regalii transaction status will update to “linked”. Dwolla will then create events for `customer_bill_payment_created` and `customer_transfer_created` and deliver these events via webhooks to your [subscribed webhook endpoint](https://docsv2.dwolla.com/#create-a-webhook-subscription) which let your application know a transfer is created with a “pending” status in the Dwolla system.

There will be additional Regalii transaction statuses after the transfer leaves the Dwolla network. The transaction statuses provided by Regalii will ultimately indicate that the transfer was successfully sent to the biller.

## Correlating a Regalii transaction ID to a Dwolla transfer

For every successful bill payment request that is made, Regalii will set the value of the `correlationId` parameter to a Regalii transaction ID, which will be returned on the created transfer in Dwolla. If you have the Regalii transaction ID and want to retrieve the corresponding Dwolla transfer, you can make a request to the Dwolla API to search the transfer by `correlationId`.

#### Request and response

```noselect
https://api-sandbox.dwolla.com/customers/24839785-3c03-4205-a495-55d65c48932e/transfers?correlationId=001d66ac-0323-4d08-9c90-4dd1f4a98718
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer {accessToken}

{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/customers/24839785-3c03-4205-a495-55d65c48932e/transfers?correlationId=001d66ac-0323-4d08-9c90-4dd1f4a98718",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "transfer"
    },
    "first": {
      "href": "https://api-sandbox.dwolla.com/customers/24839785-3c03-4205-a495-55d65c48932e/transfers?correlationId=001d66ac-0323-4d08-9c90-4dd1f4a98718",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "transfer"
    },
    "last": {
      "href": "https://api-sandbox.dwolla.com/customers/24839785-3c03-4205-a495-55d65c48932e/transfers?correlationId=001d66ac-0323-4d08-9c90-4dd1f4a98718",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "transfer"
    }
  },
  "_embedded": {
    "transfers": [{
      "_links": {
        "source": {
          "href": "https://api-sandbox.dwolla.com/customers/24839785-3c03-4205-a495-55d65c48932e",
          "type": "application/vnd.dwolla.v1.hal+json",
          "resource-type": "customer"
        },
        "destination-funding-source": {
          "href": "https://api-sandbox.dwolla.com/funding-sources/09fe9ecd-be2b-4e77-9a27-a1e2b09f7896",
          "type": "application/vnd.dwolla.v1.hal+json",
          "resource-type": "funding-source"
        },
        "self": {
          "href": "https://api-sandbox.dwolla.com/transfers/a7f08026-0a2e-e811-8106-0a595ef38714",
          "type": "application/vnd.dwolla.v1.hal+json",
          "resource-type": "transfer"
        },
        "source-funding-source": {
          "href": "https://api-sandbox.dwolla.com/funding-sources/a003fbb9-4a3f-46dc-b47c-979659974acb",
          "type": "application/vnd.dwolla.v1.hal+json",
          "resource-type": "funding-source"
        },
        "destination": {
          "href": "https://api-sandbox.dwolla.com/customers/8c43b398-024b-495a-a64b-29ce4da0e3ef",
          "type": "application/vnd.dwolla.v1.hal+json",
          "resource-type": "customer"
        },
        "bill-payment": {
          "href": "https://api-sandbox.dwolla.com/bill-payments/55bdfc3a-9568-4a67-92b3-867fde741a46",
          "type": "application/vnd.dwolla.v1.hal+json",
          "resource-type": "bill-payment"
        }
      },
      "id": "fd561bb4-7833-e811-8106-0a595ef38714",
      "status": "pending",
      "amount": {
        "value": "88.70",
        "currency": "USD"
      },
      "created": "2018-03-22T19:49:37.500Z",
      "correlationId": "001d66ac-0323-4d08-9c90-4dd1f4a98718",
      "individualAchId": "IQ2242EX"
    }]
  },
  "total": 1
}
```

After searching for the Dwolla transfer by `correlationId`, Dwolla will return the transfer object in the API response which includes information on the transfer such as amount, created, and a link to the related bill payment resource. For tracking the status of the bill payment transfer through Dwolla, you can either store the link which represents the created bill payment resource or the link which identifies the created transfer.

## Retrieving a bill payment

It is recommended that your application watches for Dwolla events (e.g. bill payment and/or transfer related) within your integration and calls the Dwolla API to obtain more information about the status of a payment. Below is an illustration of what a request to retrieve a “bill payment” resource from the Dwolla API might look like:

#### Request and response

```noselect
GET https://api-sandbox.dwolla.com/bill-payments/55bdfc3a-9568-4a67-92b3-867fde741a46
Accept: application/vnd.dwolla.v1.hal+json
Authorization: Bearer {accessToken}
```

```noselect
{
  "_links": {
    "self": {
      "href": "https://api-sandbox.dwolla.com/bill-payments/55bdfc3a-9568-4a67-92b3-867fde741a46",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "bill-payment"
    },
    "transfers": {
      "href": "https://api-sandbox.dwolla.com/transfers/fd561bb4-7833-e811-8106-0a595ef38714",
      "type": "application/vnd.dwolla.v1.hal+json",
      "resource-type": "transfer"
    }
  },
  "id": "55bdfc3a-9568-4a67-92b3-867fde741a46",
  "billedFor": "Biller Name",
  "created": "2018-03-29T17:43:35.692Z",
  "status": "pending"
}
```

The bill payment object will include a status which corresponds to the status of the transfer created in the Dwolla system, as well as the biller name for the payment. In addition, there will be a relational link which points to the transfer that was created from the bill payment request.

## Handling transfer completed and failed events

As the bank transfer makes its way from the source bank account to Regalii’s bank account (which is the first half of the bill payment life cycle), there are two webhooks that you’ll want to listen for to determine the settlement of funds.

* `customer_transfer_completed`: If the first half ofthe bill payment is successful, the transfer status will be updated to processed and Dwolla will create a `customer_transfer_completed` event.
* `customer_transfer_failed`: If the first half of the bill payment fails to settle to Regalii’s bank, the transfer status will be updated to failed and Dwolla will create a `customer_transfer_failed` event. Failures occur as the result of an ACH return, and can occur either pre-settlement or post-settlement. For more information on bank transfer failures, reference our [transfer failures](https://developers.dwolla.com/resources/bank-transfer-workflow/transfer-failures.html) resource article.
