---
layout: twoColumn
section: resources
type: tool
title:  Dwolla API Change Log
description: Use this page to keep track of changes to the Dwolla API or additions to the Dwolla Platform.
---
# Upcoming

### 2019-01-07

#### Deprecating

* Deprecation of v1 API and Transfer API. Check out our [blog post](https://www.dwolla.com/updates/sunsetting-a-legacy/) for more information. 

### 2019-02-28

#### Changing

* Dwolla allows an application to request an access token using its Client Id and Client Secret by leveraging the Client Credentials OAuth grant type. Access tokens are used to make requests to the Dwolla API on behalf of an application and its users (customers).
* Previously, applications made a call to https://www.dwolla.com/oauth/v2/token and specified the application/x-www-form-urlencoded Content-Type header, passing their client credentials (App Key and App Secret) through the body of the HTTP message sent to Dwolla. 
* With this update, the token URL as well as the manner in which an application’s client credentials are sent to Dwolla, will change to be inline with OAuth spec. 
* The new Dwolla token exchange endpoint is https://accounts.dwolla.com/token
* Reference our [API Reference Docs](https://docsv2.dwolla.com/#application-authorization) to learn more

<section class="change-log">
    <h1>Completed</h1>
	<h3>2018-06-30</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Addenda support--The addenda record is used to provide additional information to the payment recipient about the payment. This value will be passed in a transfer request and can be exposed on your user’s bank statement. Addenda records provide a unique opportunity to supply your users with more information about their transactions.  </li>
		<li>Learn more on our <a href = "https://www.dwolla.com/updates/customizing-payments-businesses/"> blog post. </a></li>
	</ul>
	<h3>2018-06-30</h3>
	<h4><em>DEPRECATED</em></h4>
	<ul class="bullet">
	    <li>Dwolla will discontinue support for TLS 1.0 and TLS 1.1.
		<li>Learn more on our <a href = "https://www.dwolla.com/updates/improving-transport-layer-security/"> blog post. </a></li>
	</ul>
	<h3>2018-06-04</h3>
	<h4><em>UPDATED</em></h4>
	<ul class="bullet">
	    <li>Dwolla has discontinued support for <code>.tif</code> file upload.</li>
		<li>View dev docs commit changes on our <a href = "https://github.com/Dwolla/v2-ach-api-docs/pull/113/commits/a2fb0e48abda154e5949efab87c9f732f648cce9"> Github </a></li>
	</ul>
	<h3>2018-05-30</h3>
	<h4><em>UPDATED/ADDED</em></h4>
	<ul class="bullet">
	    <li>New webhook <code>funding_source_negative</code> and <code>customer_funding_source_negative</code></li>
		<li>Jump to our <a href = "https://docsv2.dwolla.com/#events">dev docs</a> or view the full dev docs commit changes on our <a href = "https://github.com/Dwolla/v2-ach-api-docs/pull/112"> Github</a></li>
	</ul>
	<h3>2018-05-30</h3>
	<h4><em>UPDATED - SDK - C#</em></h4>
	<ul class="bullet">
	    <li>New version of C# SDK.</li>
		<li>Breaking changes:</li>
		<li>DwollaClient no longer throws on API errors, they should be properly deserialized into RestResponse.Error instead.</li>
		<li>DwollaException, RestException, and RestResponse.Exception are removed.</li>
		<li>Use <code>EmptyResponse</code> instead of <code>object</code> in DwollaClient inteface.</li>
		<li>Check it out on our <a href = "https://github.com/Dwolla/dwolla-v2-csharp"> Github </a></li>
	</ul>
	<h3>2018-05-11</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>Change in verified business Customer creation flow across Platform. Check out our <a href = "https://developers.dwolla.com/resources/business-verified-customer.html"> developer resource article </a> to learn how to create this Customer type within the new flow.</li>
		<li>In order to comply with United States Federal law, Dwolla also requires beneficial owners to be added to a Customer. Read <a href = "https://www.dwolla.com/updates/understanding-impacts-benefits-customer-due-diligence-rule/"> our blog post </a> to learn more about why we need to comply with US customer due diligence rules.</li>
	</ul>
	<h3>2018-04-11</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>Verified business Customers creation flow has changed in sandbox. Check out our <a href = "https://developers.dwolla.com/resources/business-verified-customer.html"> developer resource article </a> to learn how to create this Customer type within the new flow.</li>
		<li>In order to comply with United States Federal law, Dwolla also requires beneficial owners to be added to a Customer. Read <a href = "https://www.dwolla.com/updates/understanding-impacts-benefits-customer-due-diligence-rule/"> our blog post </a> to learn more about why we need to comply with US customer due diligence rules.</li>
		<li>Please note that this change will go live in across platform on May 11th, 2018.</li>
	</ul>
	<h3>2018-04-11</h3>
	<h4><em>ADDED - Developer Resources Article</em></h4>
	<ul class="bullet">
        <li>Added a new Developer Resource Article that goes over the new business verified Customer creation flow with Dwolla.</li>
        <li><a href = "https://developers.dwolla.com/resources/business-verified-customer.html"> Click here </a> to view the article</li>
	</ul>
    <h3>2018-04-11</h3>
    <h4><em>UPDATED/ADDED - Dev Docs update</em></h4>
    <ul class="bullet">
        <li>Updated Customer endpoints to reflect the <a href = "https://docsv2.dwolla.com/#customers"> new business verified Customer flow change. </a></li>
        <li>Added <a href = "https://docsv2.dwolla.com/#beneficial-owners"> the new benefical owners endpoints </a> and <a href = "https://docsv2.dwolla.com/#event-topics---a-hrefbeneficial-ownersbeneficial-ownersa"> webhooks.</a></li>
	</ul>
    <h3>2018-04-03</h3>
    <h4><em>UPDATED - Dev Docs update</em></h4>
    <ul class="bullet">
        <li>Added method and URL to Documents section</li>
        <li>View commit changes on our <a href = "https://github.com/Dwolla/v2-ach-api-docs/commit/b8ccd4fe9fa0988b54843a9ed6b3d3c8799f9290"> Github </a> </li>
	</ul>
    <h3>2018-03-30</h3>
    <h4><em>UPDATED - Developer Resources Article</em></h4>
	<ul class="bullet">
	    <li>Changed screenshot to reflect the proper On-Demand Auth Language.</li>
		<li>View commit changes on our <a href = "https://github.com/Dwolla/v2-ach-api-docs/commit/https://github.com/Dwolla/open-source-developer-portal/commit/ecdb32c0770621b4ca9555efd4b6d0403cba2d1f"> Github </a> </li>
	</ul>
	<h3>2018-03-28</h3>
	<h4><em>UPDATED - Developer Resources Article</em></h4>
	<ul class="bullet">
	    <li>Updated transfer failures doc</li>
		<li>Updated verification handling doc</li>
		<li>View commit changes on our <a href = "https://github.com/Dwolla/v2-ach-api-docs/commit/https://github.com/Dwolla/open-source-developer-portal/commit/2814249bc3e4f25dff1d80bbbe8ea1b3f81521dd"> Github </a></li>
	</ul>
	<h3>2018-02-12</h3>
	<h4><em>UPDATED - Dev Docs update</em></h4>
	<ul class="bullet">
	    <li>Updated docs to reflect business name updates.</li>
		<li>View commit changes on our <a href = "https://github.com/Dwolla/v2-ach-api-docs/commit/b27ffe0abcd419cdd2ce44ef3dbd86e8ed29e492"> Github </a> </li>
	</ul>
	<h3>2017-11-16</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>Bank <a href ="https://docsv2.dwolla.com/#retrieve-a-funding-source-balance">balance check </a> functionality changing to be asynchronous and immediately return an HTTP 202. The response body for the 202 will contain a status relating to the processing of this request. Subsequent requests to this endpoint will return a 202 up until processing completes and then either return an HTTP 200 with the current balance or an HTTP 400 if there was an error (i.e. <code>UnsupportedBank</code>).</li>
	</ul>
	<h3>2017-11-16</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Added a new <code>customer_balance_inquiry_completed</code> event. Upon checking a Customer’s bank balance, Dwolla will immediately return an HTTP 202 with response body that includes a status of processing. This event will be triggered when the bank balance check has completed processing. To read more on how to trigger this event, check out our <a href="https://discuss.dwolla.com/t/check-it-out-new-events/4554"> forum post</a>.</li>
	</ul>
	<h3>2017-11-04</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Added a new <code>customer_bank_transfer_creation_failed</code> event. This event will be triggered when an attempt to initiate a transfer to a verified Customer’s bank was made, but failed. Transfers initiated to a verified Customer’s bank must pass through the verified Customer’s balance before being sent to a receiving bank. Dwolla will fail to create a transaction intended for a verified Customer’s bank if the funds available in the balance are less than the transfer amount. To read more on how to trigger this event, check out our <a href="https://discuss.dwolla.com/t/check-it-out-new-events/4554"> forum post</a>.</li>
	</ul>
	<h3>2017-06-29</h3>
	<h4><em>CHANGED/DEPRECATED</em></h4>
	<ul class="bullet">
	    <li>Changing "uat” in the subdomain of public facing and API URLs with “sandbox”. Reference <a href="https://www.dwolla.com/updates/important-sandbox-updates-subdomain-change-and-sunsetting-of-the-sandbox-console/">this blog post</a> for more information. </li>
	</ul>
	<h3>2016-05-02</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Release support for a new (optional) <code>backButton</code> and <code>subscriber</code> options for IAV within <a href="https://developers.dwolla.com/resources/dwolla-js/instant-account-verification.html">dwolla.js</a>. <b>Note:</b> Dwolla.js is a premium feature only available for Dwolla <a href="https://www.dwolla.com/platform">API</a> customers.</li>
	</ul>
	<h3>2017-04-27</h3>
	<h4><em>DEPRECATED</em></h4>
	<ul class="bullet">
	    <li>Removal of the Sandbox Console tool which exists at: <code>https://sandbox-uat.dwolla.com/</code></li>
	</ul>
	<h3>2016-12-01</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Release support for a new <code>clearing</code> request parameter when <a href="https://docsv2.dwolla.com/#initiate-a-transfer">initiating a transfer</a>. Clearing is a JSON object that supports specifying same-day and standard ACH clearing per API request. <b>Note:</b> The clearing request parameter is a premium feature available for Dwolla <a href="https://www.dwolla.com/platform">API</a> customers.</li>
	</ul>
	<h3>2016-12-01</h3>
	<h4><em>DEPRECATED</em></h4>
	<ul class="bullet">
	    <li>Remove the <code>scope</code> attribute from the <a href="https://docsv2.dwolla.com/#application-authorization"> application access token</a> response. </li>
	</ul>
	<h3>2016-12-01</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>Automatic pause of webhook subscriptions after 400 consecutive failed delivery attempts. Reference the <a href="https://docsv2.dwolla.com/#webhook-subscriptions">API docs</a> for more information. </li>
	</ul>
	<h3>2016-10-19</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>Change the <code>phone</code> request parameter from required to optional when <a href="https://docsv2.dwolla.com/#create-a-customer">creating a Customer</a>.</li>
	</ul>
	<h3>2016-10-19</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Added a new <code>bankName</code> attribute to the funding source object that is returned when retrieving a funding source of type bank.</li>
	</ul>
	<h3>2016-07-21</h3>
	<h4><em>DEPRECATED</em></h4>
	<ul class="bullet">
	    <li>Remove the <code>profileId</code> request parameter from the <a href="https://docs.dwolla.com/#checkouts">Off-Site Gateway</a>
	    in API v1.</li>
	</ul>
	<h3>2016-06-17</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Release support for an optional <code>Idempotency-Key</code> header on requests to API v2.</li>
	</ul>
	<h3>2016-06-01</h3>
    <h4><em>CHANGED/DEPRECATED</em></h4>
    <ul class="bullet">
        <li>Change in functionality for removing a funding source in API v2. The method for <a href="https://docsv2.dwolla.com/#remove-a-funding-source">removing a funding source</a>
        changes from a <code>DELETE</code> to a <code>POST</code> with the need to supply <code>{ "removed": true }</code> in the body of the request.</li>
        <li>A <code>removed</code> attribute is added to the <a href="https://docsv2.dwolla.com/#funding-source-resource">funding source object.</a></li>
        <li>A <code>removed</code> querystring request parameter is supplied when listing an <a href="https://docsv2.dwolla.com/#list-funding-sources-for-an-account">Account</a> or <a href="https://docsv2.dwolla.com/#list-funding-sources-for-a-customer">Customer's</a> funding sources. By default, all funding sources are returned from the listing unless the <code>removed</code> request parameter is set to <code>false</code></li>.
	</ul>
	<h3>2016-02-29</h3>
	<h4><em>DEPRECATED</em></h4>
	<ul class="bullet">
	    <li>Removal of the <code>description</code> field in API v2 error
	    responses. Replacing description with the <code>message</code> field which is a
	    duplication of description.</li>
	    <li>Removing the <code>X-Request-Signature</code> header from
	    webhook requests. Replacing with a
	    <code>X-Request-Signature-Sha-256</code> header which is a SHA-256
	    HMAC hash of the request body with the key being your webhook
	    secret.</li>
	</ul>
	<h3>2015-11-25</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Release endpoint in API v2: retrieve a list of business
	    classifications for a Customer. <code>POST /business-classifications</code></li>
	    <li>Release endpoint in API v2: retrieve a business classification
	    by it's id for a Customer. <code>POST /business-classifications/{id}</code></li>
	    <li>Release <code>business</code> verified Customer creation in API v2.</li>
	</ul>
	<h3>2015-11-19</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Release endpoint in API v2: generate a funding sources token
	    for a Customer. <code>POST
	    /customers/{id}/funding-sources-token</code></li>
	    <li>Release endpoint in API v2: retrieve ACH transfer failure
	    reason. <code>GET /transfers/{id}failure</code></li>
	</ul>
	<h3>2015-11-13</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
	    <li>Release endpoint in API v2: generate an IAV token for a
	    Customer. <code>POST /customers/{id}/iav-token</code></li>
	    <li>Release <code>dwolla.js</code> to the CDN.
	    <code>https://cdn.dwolla.com/1/dwolla.js</code></li>
	</ul>
	<h3>2015-11-12</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>Error changes - Introduce new <code>message</code>field in
	    error response. Errors now include a profile link in the
	    Content-Type header. Error responses with the top-level error code
	    <code>ValidationError</code> will return an <code>_embedded</code>
	    object containing a list of <code>errors</code>.</li>
	</ul>
	<h3>2015-11-02</h3>
	<h4><em>CHANGED</em></h4>
	<ul class="bullet">
	    <li>OAuth <code>redirect_uri</code> must match the OAuth Redirect URL field set
	    in Dwolla application’s settings.</li>
	</ul>
	<h3>2015-10-30</h3>
	<h4><em>ADDED</em></h4>
	<ul class="bullet">
		<li>Release endpoint in API v2: initiate or verify micro-deposits for bank verification. <code>POST
	    /funding-sources/{id}/micro-deposits</code></li>
	    <li>Launched the new developer portal!</li>
	</ul>
</section>
