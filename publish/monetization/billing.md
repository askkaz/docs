# Roku Billing Services

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/Y292ZXItMTQ2NDgzMjQyMTgzNw==.png)

### Overview

Roku Billing Services is the payment processing technology for all channels on the Roku platform. It enables developers to integrate directly with our billing infrastructure, reduce customer support costs and effectively monetize channels.

Roku Billing Services offers two pricing models:
* **Pay-to-install**: Simple to setup and useful for specific types of applications such as themes and screensavers.
* **In-channel purchases**: Great for allowing users to preview offerings without committing beforehand. This model also grants additional features such as free trials and multiple purchasing options per channel.

For purchasing and payments, Roku’s revenue share program is 20% of revenue received (net of credits, refunds, etc.) for channels.

> :information_source: To use Roku Billing services, please activate the following:
* A Roku developer account: [developer.roku.com/enrollment/standard](http://developer.roku.com/enrollment/standard)
* Enroll in Roku Billing Services: [developer.roku.com/enrollment/billing](https://developer.roku.com/enrollment/billing)

**Sections:**
* [Customer payment details](#customer-payment-details)
* [Sales Activity reports](#sales-activity-reports)
* [Transaction details](#transaction-details)
* [Subscription management](#subscription-management)
* [Developer payments](#developer-payments)
* [Customer invoices](#customer-invoices)
* [Supported currencies](#supported-currencies)
* [Standard user flow](#standard-user-flow)

---

## Features
Roku handles many operations and transactional processing to minimize the number of services a developer would need to host using a third party system.

The core services include:

## Customer payment details
Customers have billing information stored securely with Roku. Payment information is not shared between parties and developers only need to prompt for payment and customers only need to authorize payments.

![](../../images/billing-payment-info.png)

## Sales Activity reports
Developers can view all recent channel payments and purchases from their channels. The sales info can also be exported into a `.csv` file as tabular data.

https://developer.roku.com/reports

![](../../images/billing-sales-activity.png)

## Transaction details

Full list of transactions for channels including individual purchases, amounts, and dates for those items.

https://developer.roku.com/transactions

![](../../images/billing-transaction-details.png)

## Subscription management

Customers can view all active subscriptions in addition to unsubscribing from the services.

https://my.roku.com/account/subscriptions

![](../../images/billing-sub-management.png)

## Developer payments
Remittances are delivered through Paypal.

![](../../images/billing-remittances.png)

## Customer invoices

Purchase details are sent to customers directly from Roku via email.

![](../../images/billing-invoices.png)

## Supported currencies

Roku Billing is offered in all Channel Store regions. Customer purchases and developer payments are made in the currency types listed below:

| Country       | Currency |
| ------------- | -------- |
| United States | USD
| Mexico        | USD
| Canada        | CAD
| United Kingdom| GBP
| Ireland       | EUR
| France        | EUR
| Rest of World | EUR

> :information_source: When your Paypal account receives currencies listed above, Paypal offers conversion options for your preferred currency (fees may apply). [More info on Paypal currencies](https://www.paypal.com/us/cgi-bin/webscr?cmd=p/sell/mc/mc_receive-outside)

## Standard user flow
It’s important to think about the flow and user experience when presenting billing and purchasing decisions to your audience. The following diagram is the standard flow of a Roku channel with integrated billing:

![](../../images/billing-user-flow.png)

> :information_source: Some channels may have varying user flows depending on factors such as revenue model, channel architecture, and interface design.
