<h1>Developer Tutorial — Deep linking in Roku OS</h1>

<em>Navigate directly to channel content by deep linking</em>

<a href="https://blog.roku.com/developer/files/2016/05/image03.jpg"><img class="aligncenter size-large wp-image-1234" src="https://blog.roku.com/developer/files/2016/05/image03-1024x576.jpg" alt="Banner ads deep link initiator" width="1024" height="576" /></a>
<h2>Overview for the platform</h2>
On Roku devices, <b>deep linking</b> describes the process of launching channels and media content through an ad, a search result, or the My Feed feature. In order to support the global search interface and advertising initiatives, all Roku channels with indexed content are required to respond to deep link requests. The following guide details how to integrate deep linking on your Roku channel.<!--more-->

<b>The primary sections are:</b>
<ol>
    <li>How deep linking works in Roku OS</li>
    <li>Modifying a channel to support deep linking</li>
    <li>Testing deep linking</li>
</ol>
<h2>Deep linking use cases on Roku OS</h2>
<h3>Global Search</h3>
The Roku search directory provides a great example of how deep linking works.

<a href="https://blog.roku.com/developer/files/2016/05/image00.jpg"><img class="aligncenter size-large wp-image-1231" src="https://blog.roku.com/developer/files/2016/05/image00-1024x576.jpg" alt="Global Search" width="1024" height="576" /></a>
<h3>Search Results</h3>
As you enter your desired target content in the input field, you’ll be met by a list of all related results ranked by relevancy — movies, TV shows, actors, directors, channel names, games, and so forth.

<a href="https://blog.roku.com/developer/files/2016/05/image01.jpg"><img class="aligncenter size-large wp-image-1232" src="https://blog.roku.com/developer/files/2016/05/image01-1024x576.jpg" alt="Search Results" width="1024" height="576" /></a>
<h3>Utilizing Deep Linking</h3>
Once you find your desired content, you’ll see a list of all available channels from which it can be streamed. Selecting one of these options will launch a deep link directly to the intended content — namely, the series, season, or episode’s <i>description page</i> — as opposed to simply opening the <i>channel’s main landing page</i>. This dive straight into the description page is an example of deep linking at its finest.

<a href="https://blog.roku.com/developer/files/2016/05/image02.jpg"><img class="aligncenter size-large wp-image-1233" src="https://blog.roku.com/developer/files/2016/05/image02-1024x576.jpg" alt="Search results deep link initiator" width="1024" height="576" /></a>
<h3>Deep linking banner ads from the Roku home screen</h3>
Another common use case is advertisement. Channel developers can work with the Roku Audience Development team to craft banner ads that link directly to content within an application.

<a href="https://blog.roku.com/developer/files/2016/05/image03.jpg"><img class="aligncenter size-large wp-image-1234" src="https://blog.roku.com/developer/files/2016/05/image03-1024x576.jpg" alt="Banner ads deep link initiator" width="1024" height="576" /></a>

Banner advertisements leverage deep links to open the specified content in the channel. To explore this opportunity, visit <a href="https://www.roku.com/advertising">roku.com/advertising</a>.
<h2>Modifying a channel to support deep linking</h2>
<h3>Accepting deep linking parameters in Main()</h3>
The first step is to modify the Main method to accept the deep linking parameters in BrightScript:
<pre><code>Function Main (args as Dynamic) as Void
</code></pre>
<h3>Parsing deep linking parameters</h3>
Next, account for the different parameters that can be expected:
<pre><code>if (args.reason = “ad”) then

    if (args.AdID &lt;&gt; invalid) then

        fireAdBeacon(args.AdID)

    else

        fireAdBeacon(“unspecified”)

    end if

end if
</code></pre>
<ul>
    <li><code>Args.reason</code> - is a required parameter and states why the channel was launched.</li>
    <li><code>Args.AdID</code> - is an optional parameter that is passed when the channel is launched from an ad. This parameter can be used to determine which ad launched the channel.</li>
    <li><code>fireAdBeacon()</code> - is a function for any tracking beacons that need to be fired.
<ul>
    <li><b>Note:</b> This is a function that the developer has to write. It is not a Roku SDK function.</li>
</ul>
</li>
</ul>
<strong>You must check if the user has access to the content:</strong>
<pre><code>if (user_validated() = true) then

    do_validate_flow(screen)

end if
</code></pre>
The <code>user_validated()</code> method determines if the user has signed up for the channel.
<h3>Required Parameters</h3>
The following parameters are required to support ads or universal search:
<table style="height: 458px;" width="539">
<tbody>
<tr>
<td><b>Parameter</b></td>
<td><b>Description</b></td>
<td><b>Example</b></td>
</tr>
<tr>
<td>contentID</td>
<td>Partner-defined unique identifier for a specific piece of content</td>
<td>contentID=12345, and so forth</td>
</tr>
<tr>
<td>mediaType</td>
<td>Parameter to give context to the type of contentID passed</td>
<td>"series," "episode," "movie," "shortform," and "live"

&nbsp;

The parameters "track" and "playlist" can also be used for music. Roku does not intend on supporting those in the OS, but you could extract them from an Ad.</td>
</tr>
</tbody>
</table>
When creating a deep link for content, two additional parameters must be set:
<ul>
    <li><code>args.contentID</code> and</li>
    <li><code>args.MediaType</code></li>
</ul>
<pre><code>if (args.contentID &lt;&gt; invalid AND args.mediaType &lt;&gt; invalid) then

    do_deeplink(args.contentID, args.mediaType, screen)

end if
</code></pre>
Once finished, don’t forget to initialize the home screen:
<pre><code>    do_Homescreen(screen)
</code></pre>
<b>Note:</b> It is also possible to deep link from one channel to another via the <a href="https://sdkdocs.roku.com/display/sdkdoc/roUrlTransfer">roUrlTransfer</a> component and the launch command. See the <a href="https://sdkdocs.roku.com/display/sdkdoc/External+Control+Guide">External Control Protocol (ECP)</a> documentation for more details.
<h3>User experience for deep linking</h3>
Developers need to consider the experience for Roku users when deep linking to different types of content such as episodes, movies, short form, etc.

To pass channel certification, developers are required to implement episode selection screens (aka “episodic pickers”) when deep linking to a series.

Specifically, here are the main guidelines to follow:
<ul>
<ul>
    <li><b>Series: </b>When deep linking to a series, there must be a episode selection screen (“episode picker”) for easily selecting a specific episode in addition to the main item in focus.</li>
    <li><b>Episodes:</b> When deep linking into a specific episode, it’s important to provide a springboard experience that includes an episode picker for different episodes. The behavior should keep the selected episode in focus with details while providing an ability to select other episodes within that view.</li>
    <li><b>Movies: </b>There are two main ways a deep link should respond:
<ul>
    <li><b>When a movie has been purchased previously or is free:</b> the content should play automatically.</li>
    <li><b>If a purchase is required to watch: </b>a purchase screen or a “Buy Now” option on a springboard should be presented prior to playback.</li>
</ul>
</li>
    <li><b>Short form: </b>Content should play automatically.</li>
    <li><b><b>Live: </b>Content should play automatically.</b></li>
</ul>
</ul>
<pre><code>if (args.mediaType = “movie” )

    doSpringBoard(ContentID, Screen)

else if (args.mediaType = “short form” or args.mediaType = “Live” or mediaType = “episode”) then

    playMedia(ContentID, Screen)

else if (args.mediaType = “series”)

    doEpisodicPicker(ContentID, Screen)

else

    Print “Unknown media type “, args.mediaType

end if
</code></pre>
The <code>user_validated() </code>method determines if the user is entitled to have access to the content.

<code>PlayMedia() </code>takes a contentID and a screen and plays the media directly.

<code>doEpisodicPicker()</code> is used when a user selects a series or season and a provider (specifically, your channel). The contentID of the episode and season will be passed to your channel. Use that information to display the correct episode picker. <i>This can easily be done by using the contentID to store multiple parameters</i>.

<code>contentID</code> is a unique identifier for a specific piece of content. Since there is no predetermined format, you can have multiple parameters encoded in it (ex. “SeriesID | SeasonID | episodicID”). You can then parse the contentID for the following information:
<pre><code>Myargs=args.ContentID.split(“|”)

Series_ID = myargs[0]

Season_code = myargs[1]
</code></pre>
<h2>Testing deep linking</h2>
Deep linking can be tested by invoking the appropriate ECP command using command line tools such as <a href="https://curl.haxx.se/download.html">cURL</a>. By entering the curl command from the command line (terminal for mac users), you can launch the channel on the Roku device.

For deep linking purposes, you only need the IP address of your Roku device and the ContentID of the content where you’d like to deep link. A ChannelID may be needed if the channel is not previously installed on the Roku player.

<i>Be aware that deep linking is triggered by an http post to port 8060 with the channelID and contentID.</i>

<b>Sample command to launch a Roku channel:</b>
<pre><code>    curl -d ‘’
“http://&lt;roku-ip-address&gt;:8060/launch/&lt;channel_id&gt;?contentID=&lt;contentID&gt;&amp;mediaType=series”
</code></pre>
<b>Note:</b> When deep linking to a channel, you must test to see if the channel is installed or not, otherwise the command will not launch.

<b>Check and prompt install if channel is not on the Roku Device:</b>
<pre><code>    curl -d ‘’
“http://&lt;roku-ip-address&gt;:8060/install/&lt;channel_id&gt;?contentID=&lt;contentID&gt;&amp;mediaType=series”
</code></pre>
<b>Related Resources:</b>
<ul>
    <li>RAF Framework: <a href="https://blog.roku.com/developer/2016/02/10/roku-ad-framework/">blog.roku.com/developer/2016/02/10/roku-ad-framework/</a></li>
</ul>
<ul>
    <li>Billing Services: <a href="https://blog.roku.com/developer/2016/04/07/roku-billing-services/">blog.roku.com/developer/2016/04/07/roku-billing-services/</a></li>
</ul>
<ul>
    <li>External Control Protocol: <a href="https://sdkdocs.roku.com/display/sdkdoc/External+Control+Guide#ExternalControlGuide-ImplementingDeepLinkinginaChannel">sdkdocs.roku.com/display/sdkdoc/External+Control+Guide#ExternalControlGuide-ImplementingDeepLinkinginaChannel</a></li>
</ul>
<ul>
    <li>How search works: <a href="https://sdkdocs.roku.com/display/sdkdoc/Roku+Search">sdkdocs.roku.com/display/sdkdoc/Roku+Search</a></li>
</ul>
&nbsp;

&nbsp;