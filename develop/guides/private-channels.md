# Private Channels

_Test your channels as private channels before publishing in the Channel Store_

![Private Channel channel properties screenshot](../../images/private-channel-properties.png)

### Overview
The Roku platform supports both public and private channels. Public channels are published in the Roku Channel Store and discoverable from the Search feature on the Roku home page. Private channels, however, are used for QA and beta testing purposes and can only be installed using the channel’s dedicated access code.

This guide provides an overview of how private channels work.

**Sections:**

1. [Purpose of private channels](#purpose-of-private-channels)
2. [Publishing a private channel](#publishing-a-private-channel)
3. [Updating an existing channel](#updating-an-existing-channel)
4. [Installing private channels](#installing-private-channels)

- - -

## Purpose of private channels

### QA process
Private channels are for testing and staging your channels before submitting to begin the Roku Channel Store certification process. Given the hidden nature of private channels, they can be administered to QA testers without damaging the brand by having a bug-filled channel seen by the public.

### Auto-publishing
Private channels that do not use pay-to-install Roku Billing are exempt from the certification process. This enables developers to quickly test multiple revisions and bug patches without being blocked by certification’s wait time.

### Roku Billing testing
All in-channel products purchased before a developer has enrolled in Roku Billing Services are treated as $0.00 test transactions. Developers can use this feature to test that Roku Billing has been properly integrated without making excess money transfers or having to reimburse their testing team.

### Internal use
In some instances, private channels are used to distribute a finished channel to a dedicated group, such as a corporate training video or promotional videos displayed in retail stores.

### Small circulation
As stated, private channels are intended for small circulation — they are not designed for broad audience development. It is important to note that **a private channel that upgrades to a public channel will _not_ retain all of its previous downloads**. Roku users who’ve installed a private channel will need to re-download the channel once it is made public.

Developers should not attempt to grow their audience or promote their channel until after it has been made public.

## Publishing a private channel

To publish a private channel, start on the [**Developer Dashboard**](https://developer.roku.com/developer) and select [**Manage My Channels**](https://developer.roku.com/apps) followed by [**Add Private Channel**](https://developer.roku.com/apps/create/private).

Select the monetization method(s).

![Private channel monetization screenshot](../../images/private-channel-monetize.png)

Fill out the channel properties:

*   **Channel Stores:** Regions the channel will be available in. This does not apply to private channels.
*   **Languages:** Languages to localize the Channel Store icons, descriptions and screenshots for
*   **Required Features:**
    *   **USB Support:** Select this _only_ if the channel requires a Roku with a USB port to function
    *   **Screensaver:** Select this _only_ if the channel is/contains a screensaver
    *   **Roku Game Remote:** Select this _only_ if the channel requires a remote with A &amp; B buttons to function
*   **Classification:** Select the option that best describes the channel type
*   **Internet Connection Required:** Yes/No
*   **Parental Hint:** Select the best rating for the content in the channel. If unsure, select _Content Not Rated_.
*   **Vanity Access Code:** Add a unique string of characters to make sharing the channel easier (ex. _https://my.roku.com/add/mychannel_). The vanity access code is only available after a channel has been published.

![Private channel channel properties screenshot](../../images/private-channel-properties.png)

Next you’ll need to provide some information about the channel along with channel poster images for various resolutions.

![Private channel channel descriptions screenshot](../../images/private-channel-descriptions.png)

Click **Continue** on the screenshots page, as screenshots can be omitted for private channels.

On the **Package Submission** page, **Select** the signed package for publication and click on **Save Changes**.

![Sample channel package submission screenshot](../../images/private-channel-package-upload.png)

After the package has been uploaded, there should now be an **Access Code** available and the **Submit** button should also be selectable.

![Sample channel package submission — submit](../../images/private-channel-submit.png)

Select **Submit** to successfully publish the channel.

![Sample channel package submission — uploaded](../../images/private-channel-published.png)

The package details will be shown on the right and the status will update to Published. Since private channels are not searchable in the Roku Channel Store, it is the developer’s own responsibility to share the channel access and/or vanity code(s) as desired.

## Updating an existing channel
Updating a channel follows many of the same steps as submitting a new channel. On the [**Developer Dashboard**](https://developer.roku.com/developer), select [**Manage My Channels**](https://developer.roku.com/apps) and select the channel that needs to be updated.

If none of the Channel Properties or Descriptions need to be updated, click on **Edit Channel** to go directly to the **Package Submission** page.

![Update example channel](../../images/dev-dashboard-edit-channel.png)

On the **Package Submission** page, select:

*   Channel Version
*   Minimum firmware required to run the channel
*   Application Package: Select signed package for publication

and then click on **Save Changes**.

Be sure to increment the channel’s major, minor, and build versions in the manifest as well as on the Roku Developer Portal for each package submitted.

Remember that private channels do not go through Roku certification and will be auto-published if they do not use pay-to-install Roku Billing.

## Installing private channels

Since private channels are not searchable in the Roku Channel Store, they can only be installed directly from their vanity access code URL. As stated above, a memorable vanity code can be provided during the channel publishing process, or you can use the random access code generated when the channel is published.

To install a channel using a vanity code:

*   Login to your Roku account
*   Enter https://my.roku.com/account/add?channel=VANITY_CODE into your browser
*   Replace VANITY_CODE with your channel’s vanity code
*   Click "Yes, Add Channel."

Finally, you will need to update your Roku OS before the channel will appear on your home screen. To update your OS, launch your Roku device and navigate to Settings > System > System Update > Check Now.
