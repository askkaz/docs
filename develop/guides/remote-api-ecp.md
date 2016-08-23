# Roku Remote API - External Control Protocol

### Overview

Whether you want to launch your channel content from Roku Ssearch or fancy controlling your Roku device remotely, you will need to learn how to use External Control Protocol (ECP). ECP enables a Roku device to be controlled over a local area network by providing a number of external control services. The Roku devices offering these external control services are discoverable using SSDP (Simple Service Discovery Protocol). ECP is a simple RESTful API that can be accessed by programs in virtually acny programming environment. The easiest way to test ECP is to use the cURL command to send POST/GET requests to your network connected Roku device.

**Sections:**
* [What developers can do with the External Control Protocol](#what-developers-can-do-with-the-external-control-protocol)
  * Examples of successful ECP applications
  * ECP Service commands with corresponding examples
* Implementing deep-linking for your Roku Channel
* How to test deep-linking
* ECP Security Implications
* The DIAL (Discovery and Launch) protocol, an alternative protocol with similar features to ECP

### Useful Reference/Related Links
* [Packaging with Eclipse](#packaging-with-eclipse)
[**Roku Search**](https://sdkdocs.roku.com/display/sdkdoc/Roku+Search)
[**Channel Launch Parameters**](https://blog.roku.com/developer/2011/10/06/using-launch-parameters/)
[**Channel Certification Checklist (Note: Deep Linking is on this list)**](https://sdkdocs.roku.com/download/attachments/3737121/Roku-Channel-Certification-Checklist_v2.0.xlsx?version=8&modificationDate=1467219288542&api=v2)
[**Channel Samples**](https://sdkdocs.roku.com/display/sdkdoc/The+Roku+Channel+Developer+Program)

## What developers can do with the External Control Protocol

ECP allows you to implement your out-of-the-box ideas with by giving you the ability to access Roku devices from any network connected device. Here are several of the most common use cases for ECP. These examples should serve as inspiration for what you might want to use ECP for in your channel.

### Use Case: Remote Control
There have been many creative and successful applications using ECP by third-party developers; one great example is the Rokie iPhone/iPod remote app which turns your iPhone/iPod into a Roku remote control replacement:

![Mr Robot](/images/RokieApp.png)

#### Remote Control Examples
The SDK also includes a couple of Java applications that use ECP to turn your Android device into a remote control. Also included is the Rokie app download page if you want to take a look.
[**Rokie iPhone/iPod remote app**](https://itunes.apple.com/us/app/rokie-remote-for-roku-touchpad/id1016562846?mt=8)
[**Sample Android remote control**](http://sourceforge.net/projects/rokusdkexamples/files/ecp_client.zip/download)

### Use Case: Roku Search

Many channels submit XML feeds of their content to Roku for Roku Search. The XML feeds act as an index to the channel’s content, allowing you to deep link from the Roku search page to your channel content or to perform channel actions (such as installing your channel if your channel contains the content the user is searching for) from the Roku home screen. More information on how Roku Ssearch works and example deep linking feeds can be found in the [**Roku Search documentation**](https://sdkdocs.roku.com/display/sdkdoc/Roku+Search).

ECP forms the basis for these features. When done correctly, deep linking from the Roku home screen to specific content on your channel will pass a BrightScript Associative Array containing the information necessary for your channel to perform the correct action. If the content the user searches for is on your channel but your channel isn’t installed, it’ll install your channel. If implemented properly, your channel will then open up the page/content related to the search content. Below is an example of Roku search working for a user searching for “Mr. Robot” and opening/installing the Google Play channel. The process is explained more thoroughly in the deep linking section (3).

![Mr Robot](/images/MrRobotGiphy.gif)

### Use Case: Promotion and Banner Ads

One notable use of ECP is for promotion and banner ads, as seen on the Roku homescreen:
http://gph.is/29Tm9Mu

![Starz](/images/Starz.gif)

For more details, please contact advertising@roku.com.

### Use Case: Games and Motion Control
Games that utilize motion control such as Angry Birds are implemented using ECP.
Note that the Angry Birds Space channel home screen uses Roku’s enhanced remote accelerator and sensor input to navigate the menu, essentially transforming the Roku remote into a Wii controller:

![AngryBirds1](/images/AngryBirdsDemo.gif)

Gameplay also utilizes the Roku remote for a unique motion-based UX rather than the conventional button press experience that remote control users are used to.

![AngryBirds2](/images/AngryBirds2.gif)

## External Control Service Commands

The external control services provided by ECP are included in a simple RESTful API accessed using HTTP on port 8060. Useful implementations might involve a web or mobile app that interacts with the Roku device as a remote control or for remote testing purposes. Once you have the Roku device IP address, you can issue the following external control service commands to the Roku device:

| Command | Description | Example |
| ------- | ----------- | ------- |
| keypress/key | Equivalent to pressing down and releasing the remote control key identified after the slash. You can also use this command, and the keydown and keyup commands, to send keyboard alphanumeric characters when a keyboard screen is active, as described in Keypress Key Values. This command is sent using an HTTP POST with no body. | curl -d '' http://ROKU_IP_HERE:8060/keypress/home
| keydown/key    | Equivalent to pressing the remote control key identified after the slash. This command is sent using an HTTP POST with no body. | curl -d '' http://ROKU_IP_HERE:8060/keydown/left
| keyup/key | Equivalent to releasing the remote control key identified after the slash. This command is sent using an HTTP POST with no body. | curl -d '' http://ROKU_IP_HERE:8060/keyup/left
| install/appID | Exits the current channel, and launches the Channel Store details screen of the channel identified by appID. You can follow the appID with a question mark and a list of launch parameters to be sent to the application as an associative array, and passed to the RunUserInterface() or Main() entry point. If launch parameters are given, the channel is launched immediately after the user installs the channel, and deep-links to content provided in the launch parameters. This command is sent using an HTTP POST with no body. Launches the details screen for the HBO GO channel on the given Roku device: | curl -d '' 'http://ROKU_IP_HERE:8060/install/8378?contentid=MV005011860000&MediaType=movie'|
| launch/appID | Launches the channel identified by appID. You can follow the appID with a question mark and a list of URL parameters to be sent to the application as an associative array, and passed to the RunUserInterface() or Main() entry point. This command is sent using an HTTP POST with no body. The launch command should not be used to implement deep-linking to an uninstalled channel, because it will fail to launch uninstalled channels. Use the install command instead for uninstalled channels. |curl -d '' 'http://ROKU_IP_HERE:8060/launch/dev?streamformat=mp4&url=http%3A%2F%2Fvideo.ted.com%2Ftalks%2Fpodcast%2FVilayanurRamachandran_2007_480.mp4' |
| query/device-info | Retrieves device information similar to that returned by roDeviceInfo. This command is accessed using an HTTP GET. | Request ```curl 'http://ROKU_IP_HERE:8060/query/device-info'```  |
| query/active-app | Returns a child element named 'app' that identifies the active application, in the same format as 'query/apps'. If no application is active, such as when the user is in the homescreen, the element only contains "Roku". If a screensaver is active, a second element will be included containing "screensaver". If the screensaver is an application-provided or plug-in screensaver, the same information is provided as 'query/apps'. If the screensaver is active, but is not running (such as due to system limitations), the screensaver element contains "black". This command is accessed using an HTTP GET. The query/active-app command if the user is in the homescreen. | $ curl http://ROKU_IP_HERE:8060/query/active-app <active-app> <app>Roku</app> </active-app> The query/active-app command if the user is in the homescreen but the default screensaver is active. $ curl http://ROKU_IP_HERE:8060/query/active-app <active-app> <app>Roku</app> <screensaver id="55545" type="ssvr" version="2.0.1">Default screensaver</screensaver> </active-app> The query/active-app command if the user is in the Netflix app. $ curl http://ROKU_IP_HERE:8060/query/active-app <active-app><app id="12" type="appl"version="4.1.218">Netflix</app></active-app> The query/active-app command if the user is in the Roku Media Player with an active screensaver. $ curl http://ROKU_IP_HERE:8060/query/active-app <active-app> <app id="2213" type="appl" version="4.1.1507">Roku Media Player</app><screensaver id="5533" type="ssvr" version="1.1.1">Roku Digital Clock</screensaver> </active-app> |
| query/apps | Returns a map of all the channels installed on the Roku device paired with their application ID. This command is accessed using an HTTP GET. | curl http://192.168.1.134:8060/query/apps |
| query/icon/appID | Returns an icon corresponding to the application identified by appID. The binary data with an identifying MIME-type header is returned. This command is accessed using an HTTP GET.
| Example: GET /query/icon/12 curl 'http://ROKU_IP_HERE:8060/query/icon/12' Output: img.png |
| input | Sends custom events to the current application. It takes a user defined list of name-value pairs sent as query string URI parameters. The external control server places these name-value pairs into an associative array, and passes them directly through to the currently executing channel script using a Message Port attached to a created roInput object. Input Command Conventions includes detailed recommendations on how to pass your data. Messages of type roInputEvent have a GetInfo() method that will obtain the associative array. The arguments must be URL-encoded. This command is sent using an HTTP POST with no body. | POST /input?acceleration.x=0.0&acceleration.y=0.0&acceleration.z=9.8 curl -d '' 'http://ROKU_IP_HERE:8060/input?acceleration.x=0.0&acceleration.y=0.0&acceleration.z=9.8' $ curl -d '' 'http://ROKU_IP_HERE:8060/input?touch.0.x=200.0&touch.0.y=135.0&touch.0.op=down'|

**Note:** All URLs must be properly URL encoded for the command to succeed.
Implementing ECP for Channel Developers
All things related to ECP for channels are passed in as parameters to the initial function of a channel and stored in an Associative Array called args. An example of a typical implementation is shown below:

<pre><code>
sub Main(args as Dynamic)
    if (args <> invalid)
        contentID = args.contentID
        'Call the service provider API to look up the content details,
        'or pull the right data from the feed, etc. for this contentID
        '...
    end if
end sub
</code></pre>

The standard for deep linking parameters enforced by Roku to support home screen banner ads or universal search include:
Parameter
Description
Possible Values
contentID
Partner defined unique identifier for a specific piece of content
contentID=12345, and so forth
mediaType
Parameter to give context to the type of contentID passed.



Response:
```
<device-info>
<udn>015e5108-9000-1046-8035-b0a737964dfb</udn>
<serial-number>1GU48T017973</serial-number>
<device-id>1GU48T017973</device-id>
<vendor-name>Roku</vendor-name>
<model-number>4200X</model-number>
<model-name>Roku 3</model-name>
<wifi-mac>b0:a7:37:96:4d:fb</wifi-mac>
<ethernet-mac>b0:a7:37:96:4d:fa</ethernet-mac>
<network-type>ethernet</network-type>
<user-device-name/>
<software-version>7.00</software-version>
<software-build>09021</software-build>
<secure-device>true</secure-device>
<language>en</language>
<country>US</country>
<locale>en_US</locale>
<time-zone>US/Pacific</time-zone>
<time-zone-offset>-480</time-zone-offset>
<power-mode>PowerOn</power-mode>
<developer-enabled>true</developer-enabled>
<keyed-developer-id>70f6ed9c90cf60718a26f3a7c3e5af1c3ec29558</keyed-developer-id>
<search-enabled>true</search-enabled>
<voice-search-enabled>true</voice-search-enabled>
<notifications-enabled>true</notifications-enabled>  <notifications-first-use>false</notifications-first-use>
<headphones-connected>false</headphones-connected>
</device-info>
```



"series", "episode", "movie", "shortform", and "live"
There is also "track" and "playlist" for music but Roku does not intend on supporting those in the OS but you could use them from an Ad.
When implementing deep-linking, you should first test if the channel is installed because the launch command does not work with uninstalled channels. The following pseudo-code shows how this can be done:
<pre><code>
if IsChannelIstalled(channelID) then  ECP_Command(“launch/channelID?contentID=deep_link_param&mediaType=deep_link_content_type_param)
else
ECP_Command(“install/channelID?contentID=deep_link_param&mediaType=deep_link_content_type_param)
end if
</code></pre>
Developers can test deep linking by invoking the appropriate ECP command from the command line. For example, the install command below launches the side loaded channel on the Roku device on IP address 192.168.1.114 and passes the content ID 13234.
<pre><code>
curl -d '' 'http://192.168.1.114:8060/launch/dev?contentID=13234&MediaType=series'
</code></pre>
This example shows using the install command for uninstalled channels:
<pre><code>
curl -d '' 'http://192.168.1.114:8060/install/8378?contentid=MV005011860000&MediaType=movie'
</code></pre>
Keypress Key Values
When the current screen on the Roku box includes an on-screen keyboard, any keyboard character can be sent via the keyup, keydown, and keypress commands. The key parameter can either be a key name, such as the name of a button on a remote control, or a printable character value specified with the prefix "Lit_".
Printable ASCII character code values can be transmitted "as-is" with the "Lit_" prefix. For example, you can send a 'r' with "Lit_r". In addition, any UTF-8 encoded character can be sent by URL-encoding it. For example, the euro symbol can be sent with "Lit_%E2%82%AC".
There are even some keys you can send that are not available on any physical remote. Enter is for completing keyboard entry fields, such as search fields (it is not the same as Select). Search is useful for short-cutting directly to search screens.
The following key names are recognized by ECP:
Home
Left
InstantReplay
Rew
Right
Info
Fwd
Down
Backspace
Play
Up
Search
Select
Back
Enter
Roku TVs also support:
VolumeDown
VolumeMute
VolumeUp

Security Implications
Note that with the launch command, anyone could write a program that could pass arbitrary parameters to your BrightScript channel. It is important that you validate any parameters that are passed to your program, and check what they may do to your program flow. The launch command can be very powerful to provide all kinds of interaction between network devices and your program. We envision catalogs browsed on the Internet that could instantly be watched in your channel on the Roku. The door is open to many creative uses.
But if you prefer to shut this door on your channel, you can choose to not process any passed parameters. This will mean external control programs could launch your channel, but they could not change the program flow within your channel.

DIAL Protocol
The Roku platform supports the DIAL (Discovery and Launch) protocol. DIAL is a simple network protocol for discovering first screen devices and applications from a second screen (such as a mobile iOS or Android application,) and for launching first screen applications on the first screen device from the second screen app. In the context of the Roku platform, the first screen device is the Roku itself. A first screen application is a DIAL-aware channel installed on the Roku device. Complete details of the DIAL specification can be found here: http://www.dial-multiscreen.org/dial-protocol-specification.
Many current Roku developers are familiar with the Roku external control protocol (ECP) which includes functionality similar to DIAL. An experienced Roku developer may thus fairly ask the question "why do I need DIAL?" One reason is that you may already have a DIAL based second screen implementation for use with other platforms. DIAL support on the Roku platform means that you don’t need to add a second protocol to your current application for discovery and launch.
The Roku DIAL SDK contains detailed documentation of Roku DIAL support, as well as BrightScript, Android, and iOS sample applications.  In DIAL parlance, the BrightScript sample is the first screen application, and the Android and iOS apps are the second screen applications.  These sample applications should help you get started with your own Roku DIAL support.
