
![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/Y292ZXItMTQ2NDgzMjQyMTgzNw==.png)
<h2>Overview</h2>
Roku Billing Services is the payment processing technology for all channels on the Roku platform. It enables developers to integrate directly with our billing infrastructure, reduce customer support costs and effectively monetize channels.<!--more-->

The following guide outlines the specifics on what’s required for channel billing, revenue shares, and a walk-through sample for using Roku Billing Services.

<b>Note: </b>To use Roku Billing services, please activate the following:
<ul>
    <li>A Roku developer account: <a href="http://developer.roku.com/enrollment/standard">developer.roku.com/enrollment/standard</a></li>
    <li>Enroll in Roku Billing Services: <a href="https://developer.roku.com/enrollment/billing">developer.roku.com/enrollment/billing</a></li>
</ul>
<b>Roku Billing Services offers two pricing models: </b>
<ul>
    <li><b>Pay-to-install: </b>Very simple to setup and useful for specific types of applications such as themes or screensavers.</li>
    <li><b>In-channel purchases: </b>Great for allowing users to preview offerings without committing beforehand. This model also grants additional features such as free trials and multiple purchasing options per channel.</li>
</ul>
<b>Revenue share with Roku</b>

For purchasing and payments, Roku’s revenue share program is 20% of revenue received (net of credits, refunds, etc.) for channels.
<h2>Features of Roku Billing Services</h2>
Roku handles the following operations and transactional processing for the following services:
<h3>Customer payment detail</h3>
Customers have billing information stored securely with Roku

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwNi0xNDY0ODE4ODczODMw.png)

<h3>Sales Activity reports</h3>
Developers can view all recent channel payments and purchases from their channels. The sales info can also be exported into a .CSV file as tabular data.
<a href="https://developer.roku.com/reports">https://developer.roku.com/reports</a>

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwMC0xNDY0ODE5MDk0MTEw.png)

<h3>Transaction details</h3>
Full list of transactions for channel including individual purchases, amounts, and dates for those items.
<a href="https://developer.roku.com/transactions">https://developer.roku.com/transactions</a>

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwNC0xNDY0ODE5MTU0OTU5.png)

<h3>Manage subscriptions</h3>
Users can view all purchased channels in addition to unsubscribing from the services.
<a href="https://my.roku.com/account/subscriptions">https://my.roku.com/account/subscriptions</a>

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwNy0xNDY0ODE5MTg2MTYy.png)

<h3>Developer payments</h3>
Remittances are delivered with Paypal and/or wire transfers

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwMi0xNDY0ODE5MjIzODE4.png)

<h3>Customer receipts</h3>
Payment details are sent to customer directly from Roku via email

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwOC0xNDY0ODE5MjUwNjM1.png)

<h3>Supported currencies</h3>
Roku Billing is offered in all our Channel Store regions. Please note that both customer purchases and developer payments are made in the currency types listed below:
<ul>
    <li>United States -&gt; USD</li>
    <li>Mexico -&gt; USD</li>
    <li>Canada -&gt; CAD</li>
    <li>United Kingdom -&gt; GBP</li>
    <li>Ireland -&gt; EUR</li>
    <li>France -&gt; EUR</li>
    <li>Rest of World -&gt; EUR</li>
</ul>
When your Paypal account receives currencies listed above, Paypal offers conversion options for your preferred currency (fees may apply). <a href="https://www.paypal.com/us/cgi-bin/webscr?cmd=p/sell/mc/mc_receive-outside">More info on Paypal multiple currencies</a>
<h2>Standard billing flow for a channel</h2>
It’s important to think through the flow and user experience when presenting billing and purchasing decisions to your audience. The following diagram is the standard flow of a Roku channel with integrated billing:

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jun/aW1hZ2UwMy0xNDY0ODE5MjkyNTc3.png)

<b>Note: </b>Some channels may have varying user flows depending on factors such as revenue model, channel architecture, and interface design.