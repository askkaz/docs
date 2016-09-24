#Roku Search

Roku Search provides another way to convert Roku users into customers of your VOD channel, besides the Roku Channel Store. Roku Search is located on the main menu of the Roku home screen, and allows Roku users to search for a particular movie, TV show/special, or actor/actress/director. Roku Search then allows users to see a list of providers and launch the provider's channel and go directly to the selected piece of content.

By participating in the Roku Search program, all of your content that matches any search, and your channel, is offered automatically to all Roku users who use Roku Search and can use your channel. (Search results are not shown outside the country specified and TVEverywhere (TVE) results are not returned to those who don't have the specific TVE channel installed.)

After completing a search, the user can also add the results to My Feed, which provides updates on the content they have expressed an interest in previously.

Roku Search is only available in English, and only available in the U.S., Canada (English only), Ireland and the U.K. Roku Search only supports full-length movies and TV series, episodes, and specials. Roku Search does not support short-form or clip content.

## Roku Search Algorithm
The algorithm for Roku Search is:

1. A user selects Search from the Roku home-screen main menu.
2. The user is presented with a keypad to enter a search string and a panel of search results. Initially the user also is presented with a list of previous search results. The user does have the option of clearing their search history.
3. As the user enters the search string, suggested search results from the Roku Search database matching the string are presented. The user can select any search result at any time.
4. After the user selects an actor or a director, a list of content titles that were done by that person appear.
5. After the user selects a title then a content details screen will appear. The user can also select a title directly in step #3\. This screen has a list of providers.
6. If the title is a series then a list of seasons appears. Once the user selects a season then a list of providers will appear.
7. Once the user selects a provider, that provider's channel is launched and you go directly to a spring board screen for the selected piece of content.
8. If the user does not have the provider's channel installed it will prompt the user to install the channel.

### Content Details Screen

The content details screen includes:

* artwork, such as DVD cover art, or TV show banners
* content information, such title, description, rating, actors, director, run time, production year, genre
* a selectable list of content provider items for the movie or TV show, including an option to add the movie or TV show to the personal My Feed of the user

Each item in the content provider list includes:

* the logo of the content provider
* the terms to acquire the movie or TV show
* an indication if the movie or TV show is available in HD
* the number of episodes available for TV shows
* a checkmark if the user has installed the content provider VOD channel on their Roku Media Player

Each item, when selected by the user, will "deep link" into the content provider VOD channel. The link could be to a content provider movie details screen, TV season episode list screen, or TV episode details screen, or other screen, depending on the content selected, the content provider, and whether the user has installed the content provider VOD channel.

### Content Provider List Order

Content providers are listed on the content details screen in the following order*

1. Whether or not the channel is installed (represented by the checkmark icon)
2. By price (Free, Authenticated or Subscription, Purchase/Rental price)

Search results for TV episodes results are ordered by:

1. Whether or not the channel is installed (represented by the check mark icon)
2. Whether the channel has the latest episode
3. By number of episodes available

When more than one content provider meets the same criteria, the order is randomized.
> :information_source: There are a very few exceptions.

### Content Meta-Data Database

User search strings are compared to a master database of content meta-data maintained by Roku. Content providers who participate in the Roku Search program must supply Roku with an XML file listing their currently-available content and content meta-data, which is then incorporated into the Roku master database four times a day. Currently content is pulled at 1:00am, 7:00am, 1:00pm and 7:00pm. However the process of reconciling all of the data sources is quite long so we ask you to give us 24 hours for changes to propagate to production.

## Integrating Your VOD Channel Content Into Roku Search

This is what you need to do to participate in the Roku Search program:

* Create an up-to-date XML feed of your currently available content. – see below
* Create search artwork (store and list artwork) – see below
* Create a private channel with the name SearchBeta where  is the name of your production channel. When I say "name" I mean the channel name used when you upload the channel. Not the name in the manifest.
* Submit an up-to-date XML feed of your available content to Roku using the correct XML schema. Here is the URL: [https://developer.roku.com/search/feed_validator](https://developer.roku.com/search/feed_validator). We do not accept feeds which do not pass the validator.
* Send email to dl.searchsubmit@roku.com with your private channel code, your feed URL, and your icons. Tell us if you think your deeplinking already works.
* We will configure your XML feed to your private channel and then you can test deep linking. Because private channels publish automatically you can rapidly iterate to get the feature working.
* Once the private channel is ready send mail to dl.searchsubmit@roku.com or your account manager. If you require a new version of your public channel you will have to go through both channel cert and search cert but they can be done together.
* Make sure you have infrastructure in place to keep the search feed up-to-date.

### Search Artwork

You must provide artwork to display in the Roku Search interface. The artwork you provide for the Roku Channel Store (and on the Roku homescreen, once installed) is used in the Roku Search screen to show the content providers participating in the Roku Search program, in a scrollable randomized horizontal list. You must separately provide a small icon of your logo for your item in the content providers list on the content details screen. This artwork should look similar to the artwork used to represent your channel in the Roku Channel Store, with your logo and brand colors. The following describes the requirements and usage of the artwork used in Roku Search.

#### Channel Store Artwork

This should be the similar artwork used to represent your channel in the Roku Channel Store, and the portion of the Roku home-screen that lists installed channels. For Roku Search, it is resized as follows:

* PNG format only
* Square corners
* artwork size
  * FHD 147w x 113h pixels
  * HD: 95w x 75h pixels
  * SD: 63w x 50h pixels

#### Content Provider List Artwork
The artwork for the content providers list items in the content details screen should incorporate your channel logo and brand colors. The artwork is used in the default Scene Graph list configuration (see [LabelList](/display/sdkdoc/LabelList)), so it must have specific size and appearance features to be incorporated into the list item. The artwork must conform to the following:

* PNG format only
* rounded corners
* artwork size
  * FHD: 165w x 60h pixels
  * HD: 110w x 40h pixels
  * SD: 73w x 27h pixels
* use an inner shadow effect to conform to the default Scene Graph list item focus appearance
* if a gradient is applied to the artwork, use a gradient with the light source at the top of the artwork

This illustrates the requirements of the content provider list artwork:

#### Search Artwork Templates

The following PSD templates can be used in an illustration tool to create the Roku Search artwork.
* **Channel Store Artwork, HD:** [searchProviderTile_HD.psd](/download/attachments/3737679/searchProviderTile_HD.psd?version=1&modificationDate=1449093525933&api=v2)
* **Channel Store Artwork, SD:** [searchProviderTile_SD.psd](/download/attachments/3737679/searchProviderTile_SD.psd?version=1&modificationDate=1449093571755&api=v2)
* **Content Provider List Item Artwork, HD:** [partnerLogo_template_HD.psd](/download/attachments/3737679/partnerLogo_template_HD.psd?version=2&modificationDate=1449093693712&api=v2)
* **Content Provider List Item Artwork, SD:** [partnerLogo_template_SD.psd](/download/attachments/3737679/partnerLogo_template_SD.psd?version=1&modificationDate=1449093750417&api=v2)
### XML feeds and Deep Linking
Your channel will need to be updated to support deep linking with the play IDs provided in your feed. Deep linking works by sending command line arguments, via the roAssociativeArray named "args", your channel. They should be parsed by the channel launch time. Just launching the channel will not pass certification.
**Play IDs and Deep Linking Example**
[?](#)
`Function` `Main(args as Dynamic) as void `
`if (args  invalid)`
`contentID = args.contentID`
`contentType = args.mediatype`
`LaunchSource = args.source`
`... `
`End` `Function`
**A tricky item. **In your feed there is a tag called **PlayID** which gets passed into the channel as** ContentID. **
**A 2nd tricky item. **If you select a series, then a season, it will not send you the PlayID for the series. It will send you one of the PlayIDs for one of the episodes in the selected season. You can not search for episodes of a show just seasons of a show.
It is up to the the channel developer to write brightscript code to use this information to launch the correct springboard or episodic picker screen. Here is a snippet from a working XML feed:
**Feed snippit**
[?](#)
``
`The Adventures of Chris Fable`
``
``
`us`
`bbtv:``//vod/asset_id/2dd3cf6fcf644453a0792cd1a60c3be2`
``
``
`SD`
`rental`
```1.99```
`USD`
``
``
``
``
``
Here is what shows up in args when I launch this piece of content:
**content of args**
[?](#)
`splashTime:` `1973`
`source: meta-search`
`contentid: bbtv:``//vod/asset_id/2dd3cf6fcf644453a0792cd1a60c3be2`
`instant_on_run_mode: foreground`
`mediatype: movie`
`action: display`
`lastExitOrTerminationReason: EXIT_UNKNOWN`
## Testing your channel for search
There are two ways to test. The first one is to manually trigger the deep link via an ECP command. This boils down to a "curl" to the ECP port where you specify the ContentID and the MediaType as parameters to the URL. See [External Control Guide#3.3ImplementingDeepLinkinginaChannel](/display/sdkdoc/External+Control+Guide#ExternalControlGuide-3.3ImplementingDeepLinkinginaChannel)
The other way is test with the live system. This is the purpose of the PrivateSearchBeta channel that we asked you to create above. We configure your feed to point to this channel when we test it. Because private channels are published automatically you can make changes, upload them, update your system, and see your changes in production. This is a little bit harder working with a side loaded channel because you don't have a serial port but you can draw text to the screen and see what is going on.
### XML Feed Schemas
You must provide an up-to-date XML feed web location for your VOD channel. This XML feed location can be secured with basic username and password authentication. Your XML feed should contain content meta-data for each title in your catalog, as described in [Search Meta-Data](#RokuSearch-SearchMeta-Data). The XML files from your feed location will be uploaded and incorporated into the Roku Search master database four times a day. You should update your search meta-data XML file as often as needed, but not more than four times a day.
There are two schemas used for XML feeds to the Roku master database:
* Schemas Using the Gracenote TMS Database
* Schemas Without the TMS Database
The two differ in the amount of meta-data you must supply, and whether you need to supply a TMS ID that corresponds to the deep-link playID(s) of your content item(s).
#### Schemas Using the TMS Database
One schema incorporates meta-data from the Gracenote TMS database, a database of movies and TV shows. To use this database, you must supply the minimal data required to allow Roku users to purchase and play your content items, such as playID, pricing, and so forth. You must also identify the TMS ID for the corresponding content item(s) you make available to Roku users.
The TMS ID is a 14-character scheme used to uniquely identify movie and TV show content (for example, MV123456780000). These IDs are used to match titles in your currently-offered content catalog back to specific title entries in the master Roku Search database.
The first two characters in the ID represent the unique ID domain applied to the program record:
ID
Domain
MV
Movie (theatrical, made-for-television, direct-to-video)
SH
TV Show
EP
TV Episode
The next 12 characters will be the unique numeric value within that database. This implies that the numeric sequence could be the identical across the four ID domains.
By using the TMS IDs, Roku only needs limited information from you to display full content meta-data. Please contact Gracenote directly about acquiring IDs for your content.
If the minimum meta-data you provide for a title appears to match a title we already have in our database, we will display only the TMS meta-data.
#### Schemas Without the TMS Database
The second schema requires you to provide as much content meta-data as possible to at least match the depth of meta-data found in the TMS database, for the maximum probability that user searches will have your content items in the search results. For this schema, you still must supply the data required for Roku users to purchase and play your content items, with your own unique playID for each item.
#### XML Validation
Roku cannot incorporate your XML files into the master database unless it conforms to the correct XML schema. Refer to [Search Meta-Data](#RokuSearch-SearchMeta-Data) for details on the required and optional meta-data for Roku Search. The following are two sample XML files, one that uses the TMS database, the other without the TMS database:
* TMS: [roku-parter-content-feed-example-tms-id_2015-06-01.xml](/download/attachments/3737679/roku-parter-content-feed-example-tms-id_2015-06-01.xml?version=1&modificationDate=1447970388341&api=v2)
* No TMS: [roku-partner-content-feed-example-non-tms-id-2015-06-02.xml](/download/attachments/3737679/roku-partner-content-feed-example-non-tms-id-2015-06-02.xml?version=1&modificationDate=1447970351510&api=v2)
Make sure to validate your XML feed against one of the two following XML schema (`.xsd`) files before submitting it to Roku:
* TMS: [partner-feed-tms-validator.xsd](/download/attachments/3737679/partner-feed-tms-validator.xsd?version=1&modificationDate=1455755354024&api=v2)
* No TMS: [partner-feed-validator.xsd](/download/attachments/3737679/partner-feed-validator.xsd?version=1&modificationDate=1455755361836&api=v2)
## Search Meta-Data
The following tables describe the required and optional meta-data fields used in the XML feed files for Roku Search.
Although many fields are optional, the more meta-data you include, the greater the probability your content will be returned in the user search results.
### Movie Meta-Data (TMS)
Field
Required
Description
movies/movie/@tmsId
Required
Gracenote TMS ID for a specific movie.
... movie/title
Optional
Optional, but very helpful
… movie/videos/video
Required
The videos element lists all the video content items corresponding to the specific movie identified by the movie/@tmsId attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing and other specifics about that specific video content item available on your channel.
… video/playId
Required
A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see [Play IDs and Deep Linking](#RokuSearch-PlayIDsandDeepLinking)).
… video/region
Optional
Can be one of the following 2-character ISO codes (can be either uppercase or lowercase):
* us (default)
* US (default)
* gb
* GB
* ca
* CA
* ie
* IE
… video/viewOptions/option
Required
Used to provide video viewing options.
… option/quality
Required
The resolution of the video content item. Must be one of the following (can either be uppercase or lowercase):
* sd
* SD
* hd
* HD
* hd+
* HD+
… option/license
Required
The type of license terms for the video content item. Must be one of the following (can either be initial capitalization or all lowercase):
* free
* Free
* rental
* Rental
* purchase
* Purchase
* subscription
* Subscription
… option/price
Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free
Price, that must include two decimal point places, such as "1.90", "1.99", or "2.00". If the price is "0.00", set option/license to "subscription" or "free" rather than setting option/price to "0.00", and option/price will be set to "0.00" by default.
… option/currency
Optional
The type of currency that denominates the price. Must be one of the following (can either be uppercase or lowercase):
* usd (default)
* USD (default)
* gbp
* GBP
* cad
* CAD
### Movie Meta-Data (no TMS)
Field
Required
Description
movies/movie/@id
Required
Your immutable reference ID for that movie.
Once assigned to a content item, you cannot change the reference ID or use it for another content item in the Roku Search meta-data.
... movie/titles/title
Required
Movie title. We use this value for matching. Please don’t include extra information like year, version label, and so forth.
… title/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… movie/images/image
Optional
Although this is optional, we recommend that you include it for items where you unsure about whether we can or cannot match your content.
… image/url
Required
`http://your_domain/your_image_path`
Image dimensions must be 360 x 270 pixels.
… image/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… image/@category
Required
Must one of the following:
* Poster Art
* Box Art
… movie/descriptions/description
Required
You must provide a movie description that does not exceed 60 characters. You should (though are not required) to also provide longer descriptions not to exceed 500 characters (the maximum length is set by the description/@length attribute).
… description/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… description/@length
Optional
Maximum character value for the short/long description. Must be one of the following:
* 60 (default)
* 100
* 250
* 500
… movie/runTime
Required
Runtime in seconds
… movie/releaseYear
Required
Year initially released or first aired
… movie/crew/person,
… movie/cast/person
Optional
Used to provide a list of cast and crew members.
We recommend that you provide this if there’s a chance that we can’t match your data.
… cast/person/role
Required if a cast person is provided
Must be one of the following:
* Actor
* Anchor
* Host
* Narrator
* Voice
… crew/person/role
Required if a crew person is provided
Must be one of the following:
* Director
* Host
… person/firstName
Required if person provided
First Name or abbreviation
… person/middleName
Optional
Middle Name or abbreviation
… person/lastName
Required if person provided
Last Name
… person/birthDate
Required if person provided
`_YYYY_-_mm_-_dd_`
… person/deathDate
Optional
`_YYYY_-_mm_-_dd_`
… person/image
Optional
`http://your_domain/your_image_path`
Image dimensions must be 270 x 360 pixels.
… movie/ratings/rating
Optional
Localized parental rating of movie
… rating/rating
Required if rating provided
Must be a value found in [Acceptable Parental Ratings](#RokuSearch-AcceptableParentalRatings)
… rating/source
Required if rating provided
Must be either:
* British Board of Film Classification
* Canadian Home Video Rating System
* Canadian Parental Rating
* Motion Picture Association of America
* UK Content Provider
* USA Parental Rating
… movie/keywords/keyword
Optional
Keywords used to describe movie
… keyword/type
Required only if keyword
Must be:
* Character
* General
* Mood
* Setting
* Subject
* Theme
* Time Period
… keyword/word
Optional
Users cannot search by keyword, however our meta-data structure supports them. For example, here are keywords for the movie **_Argo_** by keyword type:
**Mood**
* Brutal
* Tense
* Suspenseful
**Theme**
* Rescue
* Escape
**Subject**
* Iran hostage crisis
* On the run
* Political intrigue
* Schemes
**Time Period**
* 1970s
**Setting**
* Tehran, Iran
* CIA office
* Canada
* United States
**Character**
* CIA agent
* Specialist
* Hostage
* Revolutionary
* Ambassador
* Wife
… keyword/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… movie/genres/genre
Optional
Must be found in [Acceptable Genres](#RokuSearch-AcceptableGenres).
… movie/videos/video
Required
The videos element lists all the video content items corresponding to the specific movie identified by the movie/@id attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing and other specifics about that specific video content item available on your channel.
… video/playId
Required
A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see [Play IDs and Deep Linking](#RokuSearch-PlayIDsandDeepLinking)).
… video/region
Optional
Can be one of the following 2-character ISO codes (can be either uppercase or lowercase):
* us (default)
* US (default)
* gb
* GB
* ca
* CA
* ie
* IE
… video/viewOptions/option
Required
Used to provide video viewing options.
… option/quality
Required
The resolution of the video content item. Must be one of the following (can either be uppercase or lowercase):
* sd
* SD
* hd
* HD
* hd+
* HD+
… option/license
Required
The type of licensing terms for the video content item. Must be one of the following (can either be initial capitalization or all lowercase):
* free
* Free
* rental
* Rental
* purchase
* Purchase
* subscription
* Subscription
… option/price
Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free
Price, that must include two decimal point places, such as "1.90", "1.99", or "2.00". If the price is "0.00", set option/license to "subscription" or "free" rather than setting option/price to "0.00", and option/price will be set to "0.00" by default.
… option/currency
Optional
The type of currency denominated by price. Must be one of the following (can be either uppercase or lowercase):
* usd (default)
* USD (default)
* gbp
* GBP
* cad
* CAD
### TV Meta-Data (TMS)
Field
Required
Description
seriesItems/series/@tmsId
Required
Gracenote TMS ID for a specific TV series.
... series/title
Optional
Optional, but very helpful
… series/episodes/episode
Required
At least one episode must be included for a series
episode/@tmsId
Required
Gracenote TMS ID for a specific TV episode.
... episode/title
Optional
Optional, but very helpful
… episode/videos/video
Required
The videos element lists all the video content items corresponding to the specific TV episode identified by the episode/@tmsId attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing, and other specifics about that specific video content item available on your channel.
… video/playId
Required
A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see [Play IDs and Deep Linking](#RokuSearch-PlayIDsandDeepLinking)).
… video/region
Optional
Can be one of the following 2-character ISO codes (can be either uppercase or lowercase):
* us (default)
* US (default)
* gb
* GB
* ca
* CA
* ie
* IE
… video/viewOptions/option
Use the free [table generator](http://divtable.com/generator/) to create the perfect HTML spreadsheets for your website!
Required
Used to provide video viewing options.
… option/quality
Required
The resolution of the video content item. Must be one of the following (can be either uppercase or lowercase):
* sd
* SD
* hd
* HD
* hd+
* HD+
… option/license
Required
The type of licensing terms for the video content item. Must be one of the following (can be either initial capitalization or all lowercase):
* free
* Free
* rental
* Rental
* purchase
* Purchase
* subscription
* Subscription
… option/price
Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free
Price, that must include two decimal point places, such as "1.90", "1.99", or "2.00". If the price is "0.00", set option/license to "subscription" or "free" rather than setting option/price to "0.00", and option/price will be set to "0.00" by default.
… option/currency
Optional
The type of currency denominated by price. Must be one of the following (can be either uppercase or lowercase):
* usd (default)
* USD (default)
* gbp
* GBP
* cad
* CAD
### TV Meta-Data (no TMS)
Field
Required
Description
seriesItems/series/@id
Required
Your immutable reference ID for that TV series.
Once assigned to a content item, you cannot change the reference ID or use it for another content item in the Roku **Search** meta-data.
… series/titles/title
Required
Used for providing titles. We use this field for matching.
… title/@language
Options
Default: en
(Roku **Search** is currently only available in English.)
… series/images/image
Optional
Used to provide images for this tv series. Optional but highly recommended if you’re not confident that we can match your data.
… image/url
Required
http://your_domain/your_image_path
Image dimensions must be 360 x 270 pixels.
… image/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… series/descriptions/description
Required
You must provide a movie description that does not exceed 60 characters. You should (though are not required) to also provide longer descriptions not to exceed 500 characters (the maximum length is set by the description/@length attribute).
… description/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… description/@length
Optional
The maximum character value for the short/long description.
Must be one of the following:
* 60 (default)
* 100
* 250
* 500
… series/originalAirDate
Optional
Optional but very important. We recommend that you provide this.
… series/crew/person,
… series/cast/person
Optional
Used to identify cast and crew members
… cast/person/role
Required if a cast person is provided
Must be one of the following::
* Actor
* Anchor
* Host
* Narrator
* Voice
… crew/person/role
Required if a crew person is provided
Must be one of the following:
* Director
* Host
… person/firstName
Required if person provided
First Name or abbreviation. Used for matching.
… person/middleName
Optional
Middle Name or abbreviation
… person/lastName
Required if person provided
Last Name. Used for matching.
… person/birthDate
Required if person provided
`_YYYY_-_mm_-_dd_`
Used for matching.
… person/deathDate
Optional
`_YYYY_-_mm_-_dd_`
… person/image
Optional
http://your_domain/your_image_path
Image dimensions must be 270 x 360 pixels.
… series/seasons/season
Required
Used to include data for seasons
… season/seasonNumber
Required
Sequential season number
… season/images/image/url
Required
http://your_domain/your_image_path
Image dimensions must be 360 x 270 pixels.
… season/images/image/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… season/episodes/episode
Required
At least one episode must be included for a series
… episode/@id
Required
Your immutable reference ID for episode.
Once assigned to a content item, you cannot change the reference ID or use it for another content item in the Roku Search meta-data.
… episode/episodeNumber
Required
Sequential episode number
… episode/airDate
Optional
Optional but recommended. This is helpful for matching and such.
… episode/titles/title
Required
Series title
… title/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… episode/images/image
Optional
Image used for episode
… image/url
Required
`http://your_domain/your_image_path`
Image dimensions must be 360 x 270 pixels.
… image/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… episode/descriptions/description
Required
You must provide a movie description that does not exceed 60 characters. You should (though are not required) to also provide longer descriptions not to exceed 500 characters (the maximum length is set by the description/@length attribute).
… description/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… description/@length
Optional
Must be the maximum character value for the short/long description:
* 60 (default)
* 100
* 250
* 500
… episode/crew/person,
… episode/cast/person
Optional
A cast or crew member.
Roku recommends that you provide complete data for this if you’re not sure that we can match the episode.
… cast/person/role
Required if a cast person is provided
Must be one of the following:
* Actor
* Anchor
* Host
* Narrator
* Voice
… crew/person/role
Required if a crew person is provided
Must be one of the following:
* Director
* Host
… person/firstName
Required if person provided
First Name or abbreviation. Used for matching.
… person/middleName
Optional
Middle Name or abbreviation
… person/lastName
Required if person provided
Last Name. Used for matching.
… person/birthDate
Required if person provided
`_YYYY_-_mm_-_dd_`
Used for matching.
… person/deathDate
Optional
`_YYYY_-_mm_-_dd_`
… person/image
Optional
http://your_domain/your_image_path
Image dimensions must be 360 x 270 pixels.
… episode/ratings/rating
Optional
Localized parental rating of movie
… rating/rating
Required if rating provided
Must be a value from [Acceptable Parental Ratings](#RokuSearch-AcceptableParentalRatings)
… rating/source
Required if rating provided
Must be either:
* British Board of Film Classification
* Canadian Home Video Rating System
* Canadian Parental Rating
* Motion Picture Association of America
* UK Content Provider
* USA Parental Rating
… episode/keywords/keyword
Optional
Keywords used to describe movie
… keyword/type
Required only if keyword
Must be:
* Character
* General
* Mood
* Setting
* Subject
* Theme
* Time Period
… keyword/word
Optional
Users cannot search by Keyword, however our meta-data structure supports them. For example, here are keywords for the movie **_Argo_** by keyword type:
**Mood**
* Brutal
* Tense
* Suspenseful
**Theme**
* Rescue
* Escape
**Subject**
* Iran hostage crisis
* On the run
* Political intrigue
* Schemes
**Time Period**
* 1970s
**Setting**
* Tehran, Iran
* CIA office
* Canada
* United States
**Character**
* CIA agent
* Specialist
* Hostage
* Revolutionary
* Ambassador
* Wife
… keyword/@language
Optional
Default: en
(Roku Search is currently only available in English.)
… episode/videos/video
Required
The videos element lists all the video content items corresponding to the specific TV episode identified by the episode/@id attribute. Each child video element must have a unique play ID, and provide meta-data indicating availability, pricing, and other specifics about that specific video content item available on your channel.
… episode/genres/genre
Optional
Must be found in [Acceptable Genres](#RokuSearch-AcceptableGenres).
… video/playId
Required
A value you provide for each title in your XML feed that we will pass back to your channel when a user selects your service as a provider for a specific title (see [Play IDs and Deep Linking](#RokuSearch-PlayIDsandDeepLinking)).
… video/region
Optional
Must be one of the following 2-character ISO codes (can be either uppercase or lowercase):
* us (default)
* US (default)
* gb
* GB
* ca
* CA
* ie
* IE
… video/viewOptions/option
Required
You must provide at least one option.
… option/quality
Required
The resolution of the video content item. Must be one of the following (can be either uppercase or lowercase):
* sd
* SD
* hd
* HD
* hd+
* HD+
… option/license
Required
The type of licensing terms for the video content item. Must be one of the following (can be either initial capitalization or all lowercase):
* free
* Free
* rental
* Rental
* purchase
* Purchase
* subscription
* Subscription
… option/price
Required if option/license is set to purchase or rental, defaults to 0.00 if option/license is set to subscription or free
Price, that must include two decimal point places, such as "1.90", "1.99", or "2.00". If the price is "0.00", set option/license to "subscription" or "free" rather than setting option/price to "0.00", and option/price will be set to "0.00" by default.
… option/currency
Optional
The currency that denominates price. Must be one of the following (can either be uppercase or lowercase):
* usd (default)
* USD (default)
* gbp
* GBP
* cad
* CAD
## Acceptable Genres
All acceptable genres may have either initial capitalization of the first word, or all lower-case.
* action
* action sports
* adventure
* aerobics
* agriculture
* animals
* animated
* anime
* anthology
* archery
* arm wrestling
* art
* arts/crafts
* auction
* auto
* auto racing
* aviation
* awards
* badminton
* ballet
* baseball
* basketball
* beach soccer
* beach volleyball
* biathlon
* bicycle
* bicycle racing
* billiards
* biography
* blackjack
* boat
* boat racing
* bobsled
* bodybuilding
* bowling
* boxing
* bullfighting
* bus./financial
* canoe
* card games
* cheerleading
* children
* children-music
* children-special
* children-talk
* collectibles
* comedy
* comedy drama
* community
* computers
* consumer
* cooking
* cricket
* crime
* crime drama
* curling
* dance
* dark comedy
* darts
* debate
* diving
* docudrama
* documentary
* dog racing
* dog show
* dog sled
* drag racing
* drama
* educational
* entertainment
* environment
* equestrian
* erotic
* event
* exercise
* fantasy
* fashion
* fencing
* field hockey
* figure skating
* fishing
* football
* fundraiser
* gaelic football
* game show
* gaming
* gay/lesbian
* golf
* gymnastics
* handball
* health
* historical drama
* history
* hockey
* holiday
* holiday music
* holiday music special
* holiday special
* holiday-children
* holiday-children special
* home improvement
* horror
* horse
* house/garden
* how-to
* hunting
* hurling
* hydroplane racing
* indoor soccer
* interview
* intl soccer
* kayaking
* lacrosse
* law
* luge
* martial arts
* medical
* military
* miniseries
* mixed martial arts
* motorcycle
* motorcycle racing
* motorsports
* mountain biking
* music
* music special
* music talk
* musical
* musical comedy
* mystery
* nature
* news
* newsmagazine
* olympics
* opera
* outdoors
* parade
* paranormal
* parenting
* performing arts
* playoff sports
* poker
* politics
* polo
* pool
* pro wrestling
* public affairs
* racquet
* reality
* religious
* ringuette
* rodeo
* roller derby
* romance
* romantic comedy
* rowing
* rugby
* running
* sailing
* science
* science fiction
* self improvement
* shooting
* shopping
* sitcom
* skateboarding
* skating
* skeleton
* skiing
* snooker
* snowboarding
* snowmobile
* soap
* soap special
* soap talk
* soccer
* softball
* special
* speed skating
* sports talk
* squash
* standup
* sumo wrestling
* surfing
* suspense
* swimming
* table tennis
* talk
* technology
* tennis
* theater
* thriller
* track/field
* travel
* triathlon
* variety
* volleyball
* war
* water polo
* water skiing
* watersports
* weather
* weightlifting
* western
* wrestling
* yacht racing
## Acceptable Parental Ratings
* 12
* 12A
* 14+
* 14A
* 15
* 18
* 18+
* 18A
* A
* AA
* C
* C8
* E
* G
* NC-17
* PG
* PG-13
* R
* R18
* TV14
* TVG
* TVMA
* TVPG
* TVY
* TVY14
* TVY7
* U
* Uc
* UNRATED
* No labels
Content edited with [the HTML G online editor program](https://htmlg.com/html-editor/). Please purchase a license to stop adding similar ads to the edited documents.
