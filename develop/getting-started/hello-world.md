<i>How to load a sample channel application on your Roku device</i>
<h1><a href="https://blog.roku.com/developer/files/2016/02/image05-1.png" rel="attachment wp-att-904"><img class="alignnone size-full wp-image-904" src="https://blog.roku.com/developer/files/2016/02/image05-1.png" alt="Hello World" width="1280" height="720" /></a></h1>
<h3>Overview</h3>
In this guide, we will cover the essential steps for testing a ‘Hello World’ sample channel application on your Roku device.

<!--more-->

<strong>Steps:</strong>
<ol>
    <li>Review the <a href="https://blog.roku.com/developer/2016/02/04/developer-setup-guide/"><b>Developer Setup Guide</b></a></li>
    <li>Open the Developer Application Installer</li>
    <li><a href="https://github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip">Download</a> and Install the Sample Channel Application</li>
    <li>Edit the Sample channel Application</li>
    <li>Re-upload Sample Channel onto a Roku device</li>
</ol>

<hr />

<h2>Requirements to follow this guide:</h2>
<ul>
    <li>A Roku device: <a href="https://www.roku.com/products/compare">roku.com/products/compare</a></li>
    <li>A Roku account: <a href="https://my.roku.com/signup">my.roku.com/signup</a></li>
    <li>Download the sample channel app: <a href="https://github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip">hello-world.zip</a></li>
</ul>
<h2>1. Review the <a href="https://blog.roku.com/developer/2016/02/04/developer-setup-guide/">Developer Setup Guide</a></h2>
The Roku Developer Setup guide enables any Roku device to install sample applications such as the basic hello world example in this guide.
<table>
<tbody>
<tr>
<td><a href="https://blog.roku.com/developer/files/2016/02/image00.png"><img class="alignnone wp-image-871 size-large" src="https://blog.roku.com/developer/files/2016/02/image00-1024x568.png" alt="Developer Settings" width="1024" height="568" /></a></td>
<td><a href="https://blog.roku.com/developer/files/2016/02/image08.png"><img class="alignnone wp-image-879 size-large" src="https://blog.roku.com/developer/files/2016/02/image08-1024x489.png" alt="Development Application Installer" width="1024" height="489" /></a></td>
</tr>
</tbody>
</table>
<a href="https://blog.roku.com/developer/2016/02/04/developer-setup-guide/">Follow the Developer Setup Guide &gt;</a>
<h2>2. Open the Development Application Installer</h2>
After completing the steps covered in the <a href="https://blog.roku.com/developer/2016/02/03/developer-setup-guide/">Developer Setup guide</a>, open a web browser and navigate to the Roku device URL <i>(i.e. </i><a href="http://192.168.x.x"><i>http://192.168.x.x</i></a><i>) </i>

<b><i>Note: </i></b><i>To connect your Roku device, make sure your computer and Roku are on the same local network.</i>

<a href="https://blog.roku.com/developer/files/2016/02/image11.png" rel="attachment wp-att-882"><img class="alignnone wp-image-882 size-full" src="https://blog.roku.com/developer/files/2016/02/image11-e1454565719777.png" alt="Logging into Roku Device" width="757" height="382" /></a>

<b>Roku device credentials
</b>When you navigate to your Roku device, it will prompt for a <b>user name</b> (typically ‘rokudev’) and password was set during the Device Setup guide. Enter this information to continue.

<b>Once the page successfully opens, you have successfully connected to the Roku device.
</b>The primary screen will show the development application installer:

<a href="https://blog.roku.com/developer/files/2016/02/image08.png" rel="attachment wp-att-879"><img class="alignnone size-full wp-image-879" src="https://blog.roku.com/developer/files/2016/02/image08.png" alt="Development Application Installer" width="1099" height="525" /></a>

<i>Depending on the Roku OS version, your installer page may look like this:</i>

<a href="https://blog.roku.com/developer/files/2016/02/image04.png" rel="attachment wp-att-875"><img class="alignnone size-full wp-image-875" src="https://blog.roku.com/developer/files/2016/02/image04.png" alt="Old style for Dev Application Installer" width="1423" height="448" /></a>

<b><i>Related guide:</i></b> <a href="https://support.roku.com/hc/en-us/articles/208755668-How-can-I-update-the-software-on-my-Roku-player-"><i>How to update the software on a Roku device</i></a>
<h2>3. Download and Install the Sample Channel Application</h2>
Now that you have enabled <b>Developer Mode</b> on your Roku device and logged in, we can continue with downloading and opening a Sample Channel Application.

<b>Download the sample application located at : </b><a href="https://github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip"><b>github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip
</b></a>Once downloaded, take the .zip application and upload it to your Roku device using the Developer Application Installer:

<a href="https://blog.roku.com/developer/files/2016/02/image14.png" rel="attachment wp-att-885"><img class="alignnone size-full wp-image-885" src="https://blog.roku.com/developer/files/2016/02/image14.png" alt="Upload zip channel" width="720" height="367" /></a>

To finish this process, click on the <b>Install</b> button located below the upload option.

If the sample channel contains no errors and the process runs successfully, the sample channel will launch on the Roku device:

<a href="https://blog.roku.com/developer/files/2016/02/image05.png" rel="attachment wp-att-876"><img class="alignnone size-full wp-image-876" src="https://blog.roku.com/developer/files/2016/02/image05.png" alt="Hello World" width="1280" height="720" /></a>

<b>Note: </b>Roku devices in “Developer Mode” will allow one “side-loaded” channel at a time. If you run this process again, the new channel upload will replace the existing channel.

<b>Finding your Sample Channel on the Roku Device
</b>The developer channel will be automatically placed in the bottom row of your main channels, also known as “My Channels”.

<a href="https://blog.roku.com/developer/files/2016/02/roku-example-developer-app.png" rel="attachment wp-att-872"><img class="alignnone wp-image-962 size-full" src="https://blog.roku.com/developer/files/2016/02/roku-example-developer-app.png" alt="" width="720" height="405" /></a>
<h2>4. Editing the Sample Application</h2>
When you uncompress the .zip directory, you’ll see the following setup:

<a href="https://blog.roku.com/developer/files/2016/02/image07.png" rel="attachment wp-att-878"><img class="alignnone size-full wp-image-878" src="https://blog.roku.com/developer/files/2016/02/image07.png" alt="File view of hello world" width="974" height="228" /></a>

<b>Here’s a breakdown of the common items inside the sample application:</b>

<a href="https://blog.roku.com/developer/files/2016/02/SceneGraph-Diagrams__12_Columns.png" rel="attachment wp-att-874"><img class="alignnone wp-image-960 size-full" src="https://blog.roku.com/developer/files/2016/02/SceneGraph-Diagrams__12_Columns.png" alt="" width="1852" height="1088" /></a>

For this example, you will open the <a href="https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml">helloworld.xml</a> file that is located inside the components directory.
<h3><strong>helloworld.xml</strong></h3>
<a href="https://blog.roku.com/developer/files/2016/02/image13.png" rel="attachment wp-att-884"><img class="alignnone size-full wp-image-884" src="https://blog.roku.com/developer/files/2016/02/image13.png" alt="hello world" width="995" height="656" /></a>

The example XML file above shows how a simple Label is created and centered on the screen. Specifically on <a href="https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml#L5"><b>Line 5</b></a>, the Label’s value is set with <a href="https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml#L5">text="Hello World"</a>.

<b><i>Optional: </i></b>Review the code for additional attributes that can be set for this sample channel application.

Change the value of the text field on line 5 to another phrase:

<a href="https://blog.roku.com/developer/files/2016/02/image15.png" rel="attachment wp-att-886"><img class="alignnone size-full wp-image-886" src="https://blog.roku.com/developer/files/2016/02/image15.png" alt="helloooooo again" width="544" height="189" /></a>

After saving the edits to <a href="https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml">helloworld.xml</a>, select all the items inside the directory and zip compress utility on your computer.
<h3>Compressing the contents of the Hello World directory</h3>
<b>Note: </b>Remember to compress only the contents of the directory, not the parent folder.

<strong>For Example:</strong>

<a href="https://blog.roku.com/developer/files/2016/02/image12.png" rel="attachment wp-att-883"><img class="alignnone size-full wp-image-883" src="https://blog.roku.com/developer/files/2016/02/image12.png" alt="dont zip this way" width="675" height="207" /></a>

If you compress (“zip”) the parent folder, the Developer Application Installer will return an error.

<b>The proper ways to compress the required files:</b>

<b>Mac OS X:
</b>Right click all selected files to compress into a .zip file.

<a href="https://blog.roku.com/developer/files/2016/02/image06.png" rel="attachment wp-att-877"><img class="alignnone size-full wp-image-877" src="https://blog.roku.com/developer/files/2016/02/image06.png" alt="zip this way" width="695" height="312" /></a>

<b>Windows:
</b>Simply select all the files and folders and right click to compress into a .zip file.

<a href="https://blog.roku.com/developer/files/2016/02/image02.png" rel="attachment wp-att-873"><img class="alignnone size-full wp-image-873" src="https://blog.roku.com/developer/files/2016/02/image02.png" alt="windows compress zip" width="633" height="190" /></a>
<h3>Re-Upload the Channel Application</h3>
Once you have recompressed the Channel application, open a web browser and navigate again to the Roku device URL <i>(i.e. </i><i>http://192.168.x.x</i><i>) </i>

<a href="https://blog.roku.com/developer/files/2016/02/image09.png" rel="attachment wp-att-880"><img class="alignnone size-full wp-image-880" src="https://blog.roku.com/developer/files/2016/02/image09.png" alt="upload zip file" width="1360" height="514" /></a>

Upload the .zip file and click <b>Install</b>

You will immediately see the edited phrase in your Sample Channel Application:

<a href="https://blog.roku.com/developer/files/2016/02/image10.png" rel="attachment wp-att-881"><img class="alignnone size-full wp-image-881" src="https://blog.roku.com/developer/files/2016/02/image10.png" alt="Hellooooo Again!" width="1280" height="720" /></a>
<h2>5. Explore the Developer docs!</h2>
Go to <a href="http://sdkdocs.roku.com/">sdkdocs.roku.com</a> and explore the methods, parameters, and syntax for building rich and complex channel applications on the Roku platform.

For samples regarding our new XML framework, Roku SceneGraph, go to <a href="http://bit.ly/rokudevxml">bit.ly/rokudevxml</a> to get started!

&nbsp;