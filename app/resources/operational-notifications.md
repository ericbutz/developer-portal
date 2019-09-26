---
layout: twoColumn
section: resources
type: features
title:  Operational Notifications
description: Operational notifications are direct communications sent to a user when there is activity on their account.
---

# Operational Notifications

When using Dwolla’s white-label API, your application is responsible for all interactions to your end users. You decide how to customize the payments experience end-to-end, which includes taking on the required delivery of notifications to end users for their account and payment activity. By default, Dwolla provides functionality via Operational Notifications and sends email notifications to your end users on your behalf. When actions occur within the Dwolla Network on a resource (Customers, Transfers, etc.), events are created to record those changes. Dwolla systematically delivers an email using the email address tied to the [creation of a Customer](https://docs.dwolla.com/#customers) when an applicable event occurs.

## Operational Notification Events

Email notifications are sent to your end users when they complete the activities focused on the following key functions in your application (powered by the Dwolla Platform) or via the Dwolla Dashboard:

+ Customer creation
+ Bank account management and validation
+ Money added to a balance
+ Money withdrawn from a balance
+ Money sent to another end user (or your company)
+ Money received from another end user (or your company)
+ Customer verification and suspension

A full list of events are listed below. Please review to ensure you know when your users will receive notifications via Operational Notifications. In addition to the email notifications listed in this article, further communications, per Dwolla’s requirements and your own application’s functionality, will need to be sent by you to your end users. Please contact your Integration Manager with questions specific to your integration and recommended (or required) emails.

## Customization

When configuring Operational Notifications, there are several items that can be customized to your business. Below is a list of the items that you can currently customize:

| Item                      | Required? | Description |
|---------------------------|-----------|-------------|
| <strong>Account Name</strong> | Yes | The name that will display in the **From** section, defaults to the name on your Dwolla account or specified DBA name.<br> Example: <code>Your Business Name</code>|
| <strong>From Email Address</strong> | Yes | The email address that will display in the [From] address, only the local-part can be customized.<br> Example: <code>yourbusinessname@dwolla.com</code>|
| <strong>Reply-to Email Address</strong> | Yes | The email address your company will specify to receive replies.<br> Example: <code>support@yourbusinessname.com</code>|
| <strong>Logo</strong>| No | The branded image for your company, to be displayed at the top of the email content. The upload file format must be: .jpg, .png, or .gif. |
| <strong>Logo Link</strong> | No | The link that when the logo is clicked on, will redirect the receiver.<br> Example: <code>www.yourbusinessname.com</code> |
| <strong>Support Address | Yes | The physical address that will display in the email footer, defaulted to the address on the account.<br> Example: <code>123 Main Street, Des Moines, IA 50309</code> |
| <strong>Support phone</strong> | Conditional | An optional item. Required if a <code>Support email</code> isn't provided. The phone number that will show up in the support section, defaulted to the account phone number.<br> Example: <code>"If you have any questions or concerns please contact support at 555-555-5555."</code> |
| <strong>Support Email Address</strong> | Conditional | An optional item. Required if a <code>Support phone</code> isn't provided. The email address that will show up in the support section, optional and defaults to the account email address.<br> Example: <code>"If you have any questions or concerns please contact support at support@yourbusinessname.com."</code> |

#### Example Email Template

An example email template is shown below for a payment initiated email. At the present time, only the information listed  in the customization section can be edited. Emails are viewable within the Dwolla Dashboard upon delivery attempt to your customers.

<img src="/images/email-template.png">

## List of Emails by Type

Dwolla will systematically deliver emails for a subset of events existing in the API. As API enhancements are made, Dwolla may add new emails at any point in the future.

### Customer account Emails

##### Customers

<table>
  <thead>
    <tr>
      <th>Email Topic Name</th>
      <th>Email Subject and Body</th>
    </tr>
  </thead>

  <tbody>

    <tr>
      <td>customer_created</td>
      <td><p><strong>Subject:</strong> Account Created </p>
        <button class="accordion"></button>
        <div class="email-content">
          <pre>
          Hello {CustomerName},

          Congrats! Your {AccountName} account was successfully created.

          By creating a {AccountName} account you have also agreed to the <a href="https://www.dwolla.com/legal/tos">Dwolla Terms of Service</a> and <a href="https://www.dwolla.com/legal/privacy">Privacy Policy</a>,
          and opened a Dwolla account.
          </pre>
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_verified</td>
      <td><p><strong>Subject:</strong> Account Verified </p>
        <button class="accordion"></button>
        <div class="email-content">
          <pre>
          Hello {CustomerName},

          Your account has been successfully verified!

          </pre>
        </div>
      </td>
    </tr>

    <tr>
      <td>customer_suspended</td>
      <td><p><strong>Subject:</strong> Account Suspended </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Your account has been suspended.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_needed</td>
      <td><p><strong>Subject:</strong> Verification Document Required </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Additional documentation is required to verify your account. Please login to upload a document.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_uploaded</td>
      <td><p><strong>Subject:</strong> Verification Document Uploaded </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Your document was successfully uploaded. You will receive another email when the document has been reviewed.
            It will either be approved or rejected.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_approved</td>
      <td><p><strong>Subject:</strong> Verification Document Approved </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            The document you uploaded for account verification was approved.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_verification_document_failed</td>
      <td><p><strong>Subject:</strong> Verification Document Failed </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            A document you uploaded for account verification was rejected. Please login to your account and upload another document.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_reverification_needed</td>
      <td><p><strong>Subject:</strong> Verification Required </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Thank you for choosing {AccountName}. While you have started to create an account, more information is needed in order
            to verify your account. Please visit the {AccountName} application to complete your account registration.
            </pre>
          </div>
      </td>
    </tr>

  </tbody>
</table>

##### Funding Sources

<table>
  <thead>
    <tr>
      <th>Email Topic Name</th>
      <th>Email Subject and Body</th>
    </tr>
  </thead>

  <tbody>

    <tr>
      <td>customer_funding_source_added</td>
      <td><p><strong>Subject:</strong>  Funding Source Added </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            "{BankAccountNickName}" was added to your {AccountName} account. Here are the details:

            Bank Name: {FinancialInstitutionName}
            Account: {BankAccountNickName}
            Date: {Timestamp}

            {#OnDemandAuthPresent}
              You've agreed that future payments initiated through {AccountName}'s application will be processed by the
              Dwolla payment system using the bank account identified above and, if you want to cancel this, please
              contact support at {SupportEmail} or {#SupportPhone}.
            {/OnDemandAuthPresent}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_funding_source_verified</td>
      <td><p><strong>Subject:</strong> Funding Source Verified </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            "{BankAccountNickName}" was verified on {Timestamp}.
            </pre>
          </div>
      </td>
    </tr

    <tr>
      <td>customer_funding_source_removed</td>
      <td><p><strong>Subject:</strong> Funding Source Removed </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            "{BankAccountNickName}" was removed from your {AccountName} account on {Timestamp}.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_microdeposits_added</td>
      <td><p><strong>Subject:</strong> Micro-deposits Initiated </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Two micro-deposits were initiated to your bank account. Here are the details:

            Bank Name: {FinancialInstitutionName}
            Account: {BankAccountNickName}
            Date: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_microdeposits_completed</td>
      <td><p><strong>Subject:</strong> Micro-deposits Completed </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Two micro-deposits were successfully processed. Here are the details:

            Bank Name: {FinancialInstitutionName}
            Account: {BankAccountNickName}
            Date: {Timestamp}

            Please check your bank account for two, less than $.20, micro-deposit amounts.
            You can complete the verification process within the {AccountName} application.
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_microdeposits_failed</td>
      <td><p><strong>Subject:</strong> Micro-deposits Failed </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            The transfer of two micro-deposits sent to your bank account failed. Here are the details:

            Bank Name: {FinancialInstitutionName}
            Account: {BankAccountNickName}
            Date: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

  </tbody>
</table>

##### Transfers


<table>
  <thead>
    <tr>
      <th>Email Topic Name</th>
      <th>Email Subject and Body</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>customer_money_sent</td>
      <td><p><strong>Subject:</strong> Payment Initiated </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            A payment was initiated to {OtherPartyName}. Here are the details of this payment:

            Source: {FundingSource}
            Recipient: {OtherPartyName}
            Amount: {Amount}
            Date Initiated: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_sent_failed</td>
      <td><p><strong>Subject:</strong>  Payment Unsuccessful </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Your payment to {OtherPartyName} was unsuccessful. Here are the details of this payment:

            Source: {FundingSource}
            Recipient: {OtherPartyName}
            Amount: {Amount}
            Date Failed: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_sent_cancelled</td>
      <td><p><strong>Subject:</strong> Payment Cancelled </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            Your payment to {OtherPartyName} was cancelled. Here are the details of this payment:

            Source: {FundingSource}
            Recipient: {OtherPartyName}
            Amount: {Amount}
            Date Cancelled: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_received</td>
      <td><p><strong>Subject:</strong> Payment Pending </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            A payment was initiated from {OtherPartyName}. Here are the details of this payment:

            Source: {OtherPartyName}
            Destination: {FundingSource}
            Amount: {Amount}
            Date Initiated: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_received_completed</td>
      <td><p><strong>Subject:</strong> Payment Successful </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            A payment from {OtherPartyName} has completed. Here are the details of this payment:

            Source: {OtherPartyName}
            Destination: {FundingSource}
            Amount: {Amount}
            Date Completed: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_received_cancelled</td>
      <td><p><strong>Subject:</strong> Payment Cancelled </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            A payment from {OtherPartyName} was cancelled. Here are the details of this payment:

            Source: {OtherPartyName}
            Destination: {FundingSource}
            Amount: {Amount}
            Date Cancelled: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_received_failed</td>
      <td><p><strong>Subject:</strong> Payment Unsuccessful </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            A payment from {OtherPartyName} was unsuccessful. Here are the details of this payment:

            Source: {OtherPartyName}
            Destination: {FundingSource}
            Amount: {Amount}
            Date Failed: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_added</td>
      <td><p><strong>Subject:</strong> Money Added </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer was initiated into your {AccountName} balance. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Initiated: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_add_completed</td>
      <td><p><strong>Subject:</strong>  Add to Balance Completed </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer into your {AccountName} balance has cleared. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Cleared: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_add_cancelled</td>
      <td><p><strong>Subject:</strong> Add to Balance Cancelled </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer into your {AccountName} balance was cancelled. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Cancelled: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_add_failed</td>
      <td><p><strong>Subject:</strong> Add to Balance Failed </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer failed to clear into your {AccountName} balance. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Failed: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_withdrawn</td>
      <td><p><strong>Subject:</strong> Money Withdrawn </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer was initiated out of your {AccountName} balance. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Initiated: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_withdrawal_cancelled</td>
      <td><p><strong>Subject:</strong> Withdrawal Cancelled </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer out of your {AccountName} balance was cancelled. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Cancelled: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>

    <tr>
      <td>customer_money_withdrawal_failed</td>
      <td><p><strong>Subject:</strong> Withdrawal Failure </p>
        <button class="accordion"></button>
          <div class="email-content">
            <pre>
            Hello {CustomerName},

            An ACH transfer out of your {AccountName} balance was unsuccessful. Here are the details of this payment:

            Source: {FundingSource}
            Destination: {Destination}
            Amount: {Amount}
            Date Failed: {Timestamp}
            </pre>
          </div>
      </td>
    </tr>
  </tbody>
</table>
