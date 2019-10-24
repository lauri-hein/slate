# TransferWise API

> Base URL Sandbox

```shell
https://api.sandbox.transferwise.tech
```

> Base URL LIVE

```shell
https://api.transferwise.com
```

Welcome to the TransferWise API documentation. You can explore the different ways to use our API and choose the right one for you below.

* [Payouts and Account Automation](#transferwise-api-payouts-and-account-automation)
* [Third-Party Payouts](#transferwise-api-third-party-payouts)
* [Banks](#transferwise-api-banks)
* [Affiliates](#transferwise-api-affiliates)
* [Connected Applications](#transferwise-api-connected-applications)
* [Receive Money](#transferwise-api-receive-money)

## Payouts and Account Automation

This lets you to automate how you use your TransferWise account. You can automate payments, connect your business tools, and create ways to manage your finances.

You can:
<ul> 
  <li>Power your cross-border and domestic payouts with a single API integration.</li>
  <li>Pay out directly to bank accounts or email recipients.</li>
  <li>Monitor payments received to your TransferWise local bank details (AUD, EUR, GBP, NZD, USD).</li> 
  <li>Get statements for balance reconciliation and accounting purposes.</li>
  <li>Fully automate transfer creation and track statuses.</li>
  <li>Always get the mid-market exchange and our low cost transparent fees.</li>
  <li>Use our platform to create and build your own tool to manage your finances.</li>
</ul>

Our [Payouts Guide](#payouts-guide) will help you get started with the technical integration.

## Third-Party Payouts

Third-Party Payouts allows marketplaces and financial institutions (banks and payment service providers) to use TransferWise as a payout option for their customers.
It’s different from Payouts since it doesn’t require your company to be the originator of payments.
Instead, TransferWise will act as a third-party to your customers when they initiate a payment through your site.  

All the above listed payouts and account automation benefits are also true for third-party payouts service. You can build payment services to your customers on top of TransferWise payment platform that enables your customers to send cross-border payouts to 40+ currencies in 70+ countries.

In addition there will also be a dedicated account manager who will be your primary contact
to solve all questions and support issues should these arise.

Please note that subscribing to third party payouts service requires your company to complete enhanced due diligence process performed by TransferWise compliance team.
Please contact [bizdev@transferwise.com](mailto:bizdev@transferwise.com) for more info how to get started.

Our [Third-Party Payouts Guide](#third-party-payouts-guide) will help you get started with the technical integration.

## Banks

Our bank integration lets banks build TransferWise payments seamlessly into their own desktop and mobile apps. Banks can also build their own native user experience directly onto our API, co-branded with TransferWise.

**What are the benefits for my bank?**

* Provide your customers faster and cheaper cross-border payments, compared to traditional SWIFT alternatives.
* Offer competitive, fair, and transparent pricing to customers at the mid-market exchange rate.
* Reduce your operational costs of cross-border payments.
* Stop losing out on cross-border revenues because your customers are finding better alternatives.

**How does it work?**

<ul>
  <li><b>Transparent and fair pricing</b> - Your customers will get the same price no matter if they make transfers via your bank integration or directly via TransferWise.</li> 
  <li><b>Same great TransferWise service</b> - Your customers get access to our 24/7 customer support without leaving your own site or app. </li>
  <li><b>Custom solution</b> - We’ll work together to find and build a solution that works for your bank. There’s no one-size-fits-all approach. Together we’ll decide:
    <ul>
      <li>How do we set up flow of funds? </li>
      <li>How do we handle customer support?</li>
      <li>How do we harmonize customer onboarding and AML processes? </li>
    </ul>  
  </li>
</ul>

**See what some of our bank partners have to say**

* [Monzo and TransferWise](https://monzo.com/blog/2018/06/25/monzo-international-transfers) in the United Kingdom
* [N26 and TransferWise](https://n26.com/en-eu/transferwise) in Germany
* [LHV and TransferWise](https://www.lhv.ee/en/transferwise) in Estonia
* [BPCE and TransferWise](https://www.bankingtech.com/2018/06/bpce-natixis-and-transferwise-team-for-affordable-cross-border-remittances) in France

<br/>

**Example: the N26 native user experience using TransferWise API**

![alt text](https://image.ibb.co/m8kXTv/tw_n26_example.png "N26 User Experience")

Please contact [banks@transferwise.com](mailto:banks@transferwise.com) to get started.

Take a look at our technical integration here – [Bank Integration Guide](https://transferwise.github.io/api-docs-banks/).

## Affiliates

When you [apply to the TransferWise affiliates program](https://transferwise.com/partnerwise) you can get access to our API to help you build your own valuable content for your customers or readers.

The TransferWise API lets you to:
<ul>
    <li>Get the real-time mid-market exchange rates for any currency route.</li>
    <li>Get up to 30 days of historical mid-market exchange rates for any currency route.</li>
    <li>Get a TransferWise quote for any supported currency route, which includes our fees and estimated delivery time.</li>
</ul>

The [Affiliates Integration Guide](#affiliates-integration-guide) helps you get started with the technical integration.

## Connected Applications

With Connected Applications, you can let your customers connect their TransferWise accounts to your product. Say you’re an accounting software – doing this could let your customers automate reconciliation. If you’re a payroll company, you could push customer payments right into TransferWise. You could even push TransferWise notifications through your app. Whatever you want to build, you likely could!

We need to take a deeper look into your application use case and the added value it will bring to our joint customers in order to authorise such an integration. So before starting the technical work please contact [bizdev@transferwise.com](mailto:bizdev@transferwise.com) for more info on how to get started.

Our [Connected Apps Guide](#connected-apps-guide) gives you an overview of required technical integration work.

## Receive Money

You can receive money to the local bank details that come with your TransferWise account (AUD, EUR, GBP, NZD and USD) and reconcile these incoming payments via the API.

## Checkout flows

We currently don’t offer the option to build TransferWise into your checkout flow as a payment option to receive money. Note though that TransferWise can be added as a payout option on your site for beneficiaries to choose to receive their payout through to an email address, directly to a bank account or any other mechanism we support in our standard product.
