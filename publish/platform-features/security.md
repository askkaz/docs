# Security on the Roku Platform

### Overview

From the user experience to billing services, the Roku publishing platform is designed to protect channel's intellectual property while ensuring the audience is safe from malicious attempts.

- - -

## Channel intellectual property

In our guide on [How channels works](/develop/getting-started/how-channels-work), we outline how channels consist of code, hosted media, and design assets. An important factor of this process is that all intellectual property and code is protected by the publisher/partner/developer.

## Account and payment protection
When a new user creates a Roku acount, their billing info is recording in our secure online system. For making purchases in Roku channels, the customer can opt into a required PIN code and dialog prompt before approving a purchase.

In addition, channels are allowed to request limited information from users. When a channel is creating a new user account for their backend service, Roku OS will prompt a dialog for the user to approve the information sharing.

Available info for channels to requests includes:
* firstname
* lastname
* email
* street
* city
* state
* zip
* country
* phone

Learn more on the [channel store developer docs](https://sdkdocs.roku.com/display/sdkdoc/ifChannelStore)

### Packaging
Regarding protecting the code and media inside a channel, we require that all channels are [packaged](https://github.com/rokudev/docs/blob/master/develop/guides/packaging.md) with a secure encryption key. When channels are submitted for the Roku Channel Store, the secure package is uploaded to the developer dashboard, ensuring that only the Roku device playing content has the secure package running. [Read more about channel packaging](https://github.com/rokudev/docs/blob/master/develop/guides/packaging.md)


## Digital rights management
Roku takes copyright protection seriously. Built into every Roku device is some of the broadest support of Digital Rights Managment (DRM) formats. From streaming protocols to authenticated SSL connections, publishers can bring their content to the Roku platform with the proper security standards in place.

For a full list of our DRM support, please see our [DRM details](https://github.com/rokudev/docs/blob/master/develop/specifications/content-protection.md#drm)


## Content copy protection
The Roku OS supports High-bandwidth Digital Content Protection (HDCP) for content copy protection between the Roku player's HDMI port and the connected display. In addition, Roku 4k devices support the Trusted Execution Environment (TEE) protection.

For more details, review our guide on [content copy protection](https://github.com/rokudev/docs/blob/master/develop/specifications/content-protection.md#copy-protection)

**Related resources**

* [How channels works](/develop/getting-started/how-channels-work)
* [Channel packaging](https://github.com/rokudev/docs/blob/master/develop/guides/packaging.md)
* [DRM details](https://github.com/rokudev/docs/blob/master/develop/specifications/content-protection.md#drm)
* [content copy protection](https://github.com/rokudev/docs/blob/master/develop/specifications/content-protection.md#copy-protection)
