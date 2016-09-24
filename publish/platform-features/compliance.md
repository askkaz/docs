# Compliance

All channel developers must consider the laws and legislation for the countries their content is being streamed. The following guide covers the most common compliance factors to consider for channels on the Roku platform in addition to Roku OS features designed to assist in your legal compliance.

- - - -

## CVAA
Video programming delivered over the internet must comply with the 21st Century Communications and Video Accessibility Act (CVAA). Specifically, CVAA is the FCC's requirements governing cpationing of audio information and video description of visual information.

For traditional broadcast TV, closed captioning and visual description laws have been in place since the 1990's. For OTT (Over the Top Transmission) content, channels are required to provide closed captioning for all video content.

**Roku and CVAA** - For channels on the Roku Publishing Platform, we have several tools to assist in compliance:

* **Closed captioning** - Make sure to provide closed captioning for your video content. Read our guide to learn more ([Closed captioning docs](https://github.com/rokudev/docs/blob/master/develop/specifications/closed-captioning.md))
* **SceneGraph Audio Hinting** - Using the [SceneGraph XML framework](https://github.com/rokudev/docs/tree/master/develop/sdk-development), channels built in SceneGraph will have built in support for Text to speech. When text elements such as lists, grids, posters, labels, etc are active - Roku OS will speak the text values on the TV. This will ensure the majority of new channels will comply.
* **Text to Speech APIs** - Roku provides low level text to speech support in channels via the [roTextToSpeech](https://sdkdocs.roku.com/display/sdkdoc/ifTextToSpeech) and [roTextToSpeechEvent](https://sdkdocs.roku.com/display/sdkdoc/roTextToSpeechEvent) components. This is useful for custom voiceover prompts in channels.

## COPPA
The [Children's Online Privacy Protection Rule (COPPA)](https://www.ftc.gov/enforcement/rules/rulemaking-regulatory-reform-proceedings/childrens-online-privacy-protection-rule), imposes certain requirements for online streaming content directed to children under 13 years of age or services in addition to restrictions for knowingly collecting personal information from a child under 13 years of age.

**Advertisers and COPPA** - On July 1, 2013 - FTC expanded the COPPA requirements to ad networks and online plugin services. It's important for all ads streamed and tracking to be COPPA compliant, please refer to the FTC's site for full details: [FTC's site for Children's Privacy](https://www.ftc.gov/tips-advice/business-center/privacy-and-security/children%27s-privacy)

## Specific Country Legal Requirements
Channels must adhere to leglislation in countries their content is availble in. For Roku related documents, please review each country at [roku.com/legal](https://www.roku.com/legal)


**Related resources:**

* [Closed captioning docs](https://github.com/rokudev/docs/blob/master/develop/specifications/closed-captioning.md)
* [SceneGraph XML framework](https://github.com/rokudev/docs/tree/master/develop/sdk-development)
* [roTextToSpeech](https://sdkdocs.roku.com/display/sdkdoc/ifTextToSpeech)
* [roTextToSpeechEvent](https://sdkdocs.roku.com/display/sdkdoc/roTextToSpeechEvent)
* [Children's Online Privacy Protection Rule (COPPA)](https://www.ftc.gov/enforcement/rules/rulemaking-regulatory-reform-proceedings/childrens-online-privacy-protection-rule)
* [roku.com/legal](https://www.roku.com/legal)
