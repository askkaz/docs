<h2>Overview</h2>

Publishing on the Roku Channel Store requires several core items — such as source code, images, and fonts — to be “packaged.” This enables developers to securely publish channels while keeping all intellectual property safely encrypted. The process of “packaging a channel” uses cryptographic hardware built into Roku devices and creates an encrypted package that can be easily and securely distributed on Roku devices.

<b>Requirements to follow along:</b>
    
* [A Roku device](http://www.roku.com/products/compare)
* [A Roku developer account](http://developer.roku.com/enrollment/standard)
* [BrightScript plugin for Eclipse](https://developer.staging.roku.com/home/docs?cs=c-developer-tools&ps=eclipse-plugin)
* [Reviewed Getting Started](https://developer.staging.roku.com/home/docs?cs=c-getting-started&ps=gs-index)

<b>Sections:</b>

* Packaging with Eclipse
* Packaging using the Package Utilities
* Rekeying
* Channel Screenshots

<h2>1: Packaging with Eclipse</h2>

Packaging can be done in Eclipse using the [Roku BrightScript Plugin](https://developer.staging.roku.com/home/docs?cs=c-developer-tools&ps=eclipse-plugin). 

In an existing BrightScript project, select <b>File &gt; Export &gt; BrightScript Deployment</b>.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image04.png" rel="attachment wp-att-1155"><img class="alignnone wp-image-1155 size-full" src="https://blog.roku.com/developer/files/2016/05/image04.png" alt="image04" width="525" height="550" /></a></p>

In the following dialog, check <b>Install on Roku Box</b> and <b>Create Package (.pkg) file</b>. 

If the genkey utility has not been run previously, click on <b>New Keys</b> to generate a signing key.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image01.png" rel="attachment wp-att-1156"><img class="alignnone wp-image-1156 size-full" src="https://blog.roku.com/developer/files/2016/05/image01.png" alt="image01" width="840" height="859" /></a></p>

Select <b>Finish</b> and the package will be available in the <b>out</b> folder of the current BrightScript project in the Eclipse workspace.

<h2>2: Packaging using the Package Utilities</h2>

<h3>A. Install (or “sideload”) channel on a Roku device</h3>

In addition to the Eclipse plugin, developers can use the package utilities located within the Development Application Installer. Note that before a channel can be packaged, it must first be sideloaded onto a Roku device. Refer to our [Hello World Guide](https://developer.staging.roku.com/home/docs?cs=c-getting-started&ps=hello-world) on how to sideload channels.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/Screen-Shot-2016-05-24-at-4.38.35-PM.png" rel="attachment wp-att-1157"><img class="alignnone wp-image-1193 size-full" src="https://blog.roku.com/developer/files/2016/05/Screen-Shot-2016-05-24-at-4.38.35-PM.png" alt="" width="622" height="281" /></a></p>

<h3>B. Open a telnet session</h3>

Once you have the channel side-loaded onto a Roku device, you’ll need to generate a key to sign your package. Windows developers can use a telnet client such as [PuTTY](http://www.putty.org/), while OSX/Linux developers can use the built-in client through terminal.

<b>Windows</b>: In PuTTY, enter the <b>IP address</b> of your Roku player, <b>8080</b> for the port, and <b>Telnet</b> as the connection type.

<a href="https://blog.roku.com/developer/files/2016/05/image08.png" rel="attachment wp-att-1158"><img class="aligncenter wp-image-1158 size-full" src="https://blog.roku.com/developer/files/2016/05/image08.png" alt="image08" width="466" height="448" /></a>

<b>OSX/Linux</b>: Open terminal and type: telnet &lt;Roku-IP-address&gt; 8080

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image12.png" rel="attachment wp-att-1159"><img class="alignnone wp-image-1159 size-full" src="https://blog.roku.com/developer/files/2016/05/image12.png" alt="image12" width="567" height="200" /></a></p>

<h3>C. Run the genkey utility to create a signing key</h3>

Type <b>genkey</b> into the command prompt/terminal and wait for the process to complete. If the prompt says “Command not recognized,” type it again.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image00.png" rel="attachment wp-att-1160"><img class="alignnone wp-image-1160 size-full" src="https://blog.roku.com/developer/files/2016/05/image00.png" alt="image00" width="675" height="424" /></a></p>

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image03.png" rel="attachment wp-att-1161"><img class="alignnone wp-image-1161 size-full" src="https://blog.roku.com/developer/files/2016/05/image03.png" alt="image03" width="568" height="250" /></a></p>

Upon completion, a key has been successfully generated to sign packages. Make note of the developer ID and password as it’ll be required in the next step (and anytime code is updated and needs to be repackaged).

<i>Note: It is a good practice to generate a new signing key for each channel created unless you explicitly want to share registry information between channels.</i>

<h3>D. Packaging the side-loaded channel</h3>

Return to the Developer Application Installer. There should now be a <b>Packager </b> option available. If this option is not available, go through the previous step and run genkey again.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image09.png" rel="attachment wp-att-1162"><img class="alignnone wp-image-1162 size-large" src="https://blog.roku.com/developer/files/2016/05/image09-1024x546.png" alt="image09" width="1024" height="546" /></a></p>

Click on <b>Packager</b> to bring up the Application Packager page. The Dev ID should match the same developer ID that was generated with genkey.

Enter an App Name and Version and enter the password created from the genkey utility.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image07.png" rel="attachment wp-att-1163"><img class="alignnone wp-image-1163 size-large" src="https://blog.roku.com/developer/files/2016/05/image07-1024x486.png" alt="image07" width="1024" height="486" /></a></p>

Click on <b>Package</b> and a few short moments later the signed package can be downloaded using the .pkg link.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image05.png" rel="attachment wp-att-1164"><img class="alignnone wp-image-1164 size-large" src="https://blog.roku.com/developer/files/2016/05/image05-1024x622.png" alt="image05" width="1024" height="622" /></a></p>

<h2>3. Rekeying</h2>

When developing multiple applications, it’s good practice to sign each package with a different key. This ensures registry entries are not shared between channels. To sign different packages on the same device, it will have to be rekeyed.

On the Development Application Installer, select <b>Utilities</b>.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image02.png" rel="attachment wp-att-1165"><img class="alignnone wp-image-1165 size-large" src="https://blog.roku.com/developer/files/2016/05/image02-1024x512.png" alt="image02" width="1024" height="512" /></a></p>

Click on <b>Upload</b> and select the signed package you'd like to use to rekey the player. Enter the <b>password</b> from genkey that matches the key and select <b>Rekey</b>.

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image10.png" rel="attachment wp-att-1166"><img class="alignnone wp-image-1166 size-large" src="https://blog.roku.com/developer/files/2016/05/image10-1024x530.png" alt="image10" width="1024" height="530" /></a></p>

A success dialog will be displayed when the process is complete.

<h2>4. Channel screenshots</h2>

Channel screenshots can also be taken using the Package Utilities tool located in the top nav bar. Select <b>Utilities</b> and click the <b>Screenshot</b> button.</span>

<i>Note: Screenshots will only work for sideloaded channels and static content (i.e. screenshots of video will not work). FHD (1920x1080) screenshots also require a 4K capable Roku set to 1080p or 4K UHD display type.</i>

<p style="text-align: center"><a href="https://blog.roku.com/developer/files/2016/05/image02-1.png" rel="attachment wp-att-1167"><img class="alignnone wp-image-1167 size-large" src="https://blog.roku.com/developer/files/2016/05/image02-1-1024x512.png" alt="image02" width="1024" height="512" /></a></p>