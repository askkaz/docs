<h2>Publishing Channels</h2>

<h3>Overview</h3>
Once a Roku channel has been designed, developed and thoroughly tested - the final step is publishing on the Roku platform. The following guide goes over the channel distribution models available on the Roku platform and how to:

1. Create a public channel
2. Create a private channel
3. Update an existing channel

<b>Public channels</b>
Channels in the Roku Channel Store are certified before they are made available to the public. 
Some of the key benefits for public channels are:

* Featured in the New category for 30 days after publication
* Displayed in a Channel Store category (chosen during the submission process)
* Searchable by channel name in Roku Search

Channels with deep linking and have submitted a Roku Search feed can also support:

* Home screen banner promotions<sup>1</sup>
* Roku Search by content or person(s)

<b>Private channels</b>
Private channels are another way to distribute channels on the Roku platform. They are not listed in the Channel Store and can only be installed using the channel access and/or vanity code(s). Private channels are not subject to the channel certification process. The main uses for private channels are:

* Testing Roku-billed in-channel transactions (all purchases are treated as $0.00 transactions)
* QA and beta testing

<sup>1</sup> Contact [advertising@roku.com]() for more details.

<hr/>

<h2>1. Create a public channel</h2>
On the <b>[Developer Dashboard](https://developer.roku.com/developer)</b>, select <b>[Manage My Channels](https://developer.roku.com/apps)</b> and <b>[Add Public Channel](https://developer.roku.com/apps/create/public)</b> on the following page.

<h3>Channel Properties</h3>
On the <b>Channel Properties page</b>, select any monetization models that apply and click <b>Continue</b>.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxMC0xNDY5MTUyMTYwNDcz.png)

Fill out the channel properties:

* Channel Stores: regions the channel will be available in
* Languages: Languages to localize the Channel Store icons, descriptions and screenshots for
* Required Features:
 * USB Support: Select this only if the channel requires a Roku with a USB port to function
 * Screensaver: Select this only if the channel is/contains a screensaver
 * Roku Game Remote: Select this only if the channel requires a remote with A & B buttons to function
* Classification: Select the option that best describes the channel type
* Internet Connection Required: Yes/No
* Parental Hint: Select the best rating for the content in the channel. If unsure, select Content Not Rated.
* Vanity Access Code: Add a unique string of characters to make sharing the channel easier (ex. https://my.roku.com/add/myrokuchannel). The Vanity access code is only available after a channel has been published.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxNi0xNDY5MTUyNDQxMjE2.png)

<h3>Channel Pricing / pay-to-install</h3>
If <b>Customers will pay before installing my channel</b> was selected on the monetization questionnaire and you’ve enrolled in Roku Billing Services, the <b>Channel Pricing</b> page will be presented.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxMy0xNDY5MTUyNTM3NTAw.png)

On this page, the type of pay-to-install model (one-time, monthly subscription or yearly subscription) and a corresponding price tier can be selected. 

<h3>Channel Descriptions</h3>
On the <b>Channel Descriptions</b> page, fill in: name of the channel, descriptions, keywords for channelstore.roku.com, preferred Channel Store categories and upload the Channel Store icons.

<i>Note: If multiple languages were selected on the Channel Properties page, the Channel Descriptions page will have a separate section for each language for locale-specific descriptions and Channel Store icons.</i>

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwMS0xNDY5MTUyNjQ2OTI2.png)

<h3>Screenshots</h3>
On the next page, upload any screenshots for display in the Channel Store. Up to 6 HD (1280x720) and 6 FHD (1920x1080) images can be uploaded for each locale.

Refer to the <b>[Channel Packaging Developer Tutorial](https://blog.roku.com/developer/2016/05/24/tutorial-channel-packaging/)</b> for instructions on how to take screenshots.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwOS0xNDY5MTUyNzMzODU0.png)

Once the screenshots have been uploaded, select <b>Continue</b>.

<h3>Support Information</h3>
Before we proceed with the package submission, click on <b>Support Information</b> and fill in all required fields.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxOC0xNDY5MTUyODA2OTUz.png)

<h3>Package Submission</h3>
On the <b>Package Submission</b> page, select:

* Channel Version
* Minimum firmware version required to run the channel
* Application Package: Select signed package for publication

and then click on <b>Save Changes</b>.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwMC0xNDY5MTUyODk5Mzg0.png)

After the package has been uploaded, there should now be an <b>Access Code</b> available and the <b>Submit</b> button should also be selectable.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwOC0xNDY5MTUyOTY5NDUx.png)

Before submitting, make sure the channel has been thoroughly tested and reviewed against the <b>[pre-certification channel checklist](https://sdkdocs.roku.com/download/attachments/3737121/Roku-Channel-Certification-Checklist_v2.0.xlsx?version=8&modificationDate=1467219288542&api=v2)</b>.

<h3>Key Dates</h3>
Click <b>Submit</b> and fill in any key publishing dates.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwMi0xNDY5MTUzMDg3NzU4.png)

Select <b>Continue</b> to return to the <b>Package Submission</b> page.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxMi0xNDY5MTUzMTU0ODQ4.png)

Once the channel has been submitted, it will be reviewed by Roku and: 

* published if it has passed certification 
* or receive a list of issues that need to be addressed before publication

<h2>2. Create a private channel</h2>
On the <b>[Developer Dashboard](https://developer.roku.com/developer)</b>, select <b>[Manage My Channels](https://developer.roku.com/apps)</b> and <b>[Add Private Channel](https://developer.roku.com/apps/create/private)</b> on the following page.

Likewise with public channels, select the monetization method(s).

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxNy0xNDY5MjE1Mzk2MDU5.png)

Fill out the channel properties, descriptions and Channel Store icons as needed.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwMy0xNDY5MjE1NDU4ODgy.png)

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwNy0xNDY5MjE1NDg1OTMx.png)

<i>Note: Screenshots can be omitted for private channels.</i>

On the screenshots page, click <b>Continue</b>. On the <b>Package Submission</b> page, <b>Select</b> the signed package for publication and click on <b>Save Changes</b>.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwNS0xNDY5MjE1NzQwMTgy.png)

After the package has been uploaded, there should now be an <b>Access Code</b> available and the <b>Submit</b> button should also be selectable.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxMS0xNDY5MjE1ODI4Njky.png)

Select <b>Submit</b> to successfully publish the channel. 

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxNC0xNDY5MjE1ODczMTE5.png)

The package details will be shown on the right and the status will update to Published.

<h2>3. Update an existing channel</h2>
Updating a channel follows many of the same steps as submitting a new channel. On the <b>[Developer Dashboard](https://developer.roku.com/developer)</b>, select <b>[Manage My Channels](https://developer.roku.com/apps)</b> and select the channel that needs to be updated.

If none of the Channel Properties or Descriptions need to be updated, click on <b>Edit Channel</b> to go directly to the <b>Package Submission</b> page.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UwNC0xNDY5MjE2MTg4MDg0.png)

On the <b>Package Submission</b> page, select:

* Channel Version
* Minimum firmware required to run the channel
* Application Package: Select signed package for publication

and then click on <b>Save Changes</b>.

<i>Note: Be sure to increment the channel’s major, minor, and build versions in the manifest as well as on the Roku Developer Portal for each package submitted.</i>

Public channels: Click <b>Submit</b> to display the <b>Key Dates</b> page. In addition, there is also a section for <b>Release Notes</b>. Being as detailed as possible will help with the certification process.

![](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/aW1hZ2UxNS0xNDY5MjE2MzAyNjI5.png)

Select <b>Continue</b> to finalize the submission and return to the Package Submission page. As with first time submissions, public channel updates will be reviewed by Roku and: 

* published if it has passed certification
* or receive a list of issues that need to be addressed before publication

Private channels do not go through Roku certification and can be auto-published if it does not use pay-to-install Roku Billing. Private channels using in-channel products can also be auto-published but purchases will remain as $0.00 test transactions.

