_Speed up the development, testing, and publishing for channels_

## Overview
With over 80,000 developers on the platform, we have been working to improve the experience of building channels on the Roku Platform. Today, we’re excited to share an open beta for the revamped Roku plugin for Eclipse!

![Eclipse screenshot](../../images/eclipse_1.png)

<a href="https://eclipse.org/ide/">The Eclipse IDE (Integrated Development Environment)</a> is used by millions of professional engineers around the world for coding and deploying rich applications.
## Why the Roku plugin is great?
Building channel applications requires several items to work together in unison:
<ul>
 	<li>A Roku device</li>
 	<li>The Roku Operating System</li>
 	<li>Your channel application</li>
 	<li>Hosted media content (video, audio, games, etc)</li>
</ul>
To make this happen, developers set up various ways to get rapid coding installed quickly on a device. Thanks to the Roku Plugin for Eclipse, within several minutes you’ll have the power of a fully baked Integrated Development Environment and the customizations needed to develop, test, package, and install channels on Roku devices.

<h3>Key Features</h3>

<h3>Code highlight / Syntax Coloring</h3>
![Code highlighting screenshot](../../images/eclipse_2.png)<br><br>

Quickly find errors in your channel application with our built in color coding for BrightScript and Roku SceneGraph syntax.<br><br>

![Syntax coloring screenshot](../../images/eclipse_3.png)

<h3>Code completion and hints</h3>
The plugin checks the reference guides for BrightScript and Roku SceneGraph, allowing for auto completion and details for parameters, methods, and nodes.<br><br>

![Code hints screenshot](../../images/eclipse_4.png)

<h3>Built in telnet console for BrightScript and SceneGraph</h3>
All the available Roku device telnet ports are built into the plugin, allows for fast feedback on bugs, stack traces, and break points in your channel application.<br><br>

![Telnet debugger screenshot](../../images/eclipse_5.png)

<h2>Create a new BrightScript project</h2>
Quickly have all required assets and files setup through Eclipse. In addition, reference sample channels are provided in a simple drop down for testing. The manifest, components, source, images, locale, and related directories are handled instantly.<br><br>

![New BrightScript Project](../../images/eclipse_6.png)

<h3>Installing and packaging channel application</h3>
Using the standard export option for projects, the Roku plugin for Eclipse enables developers to install their current channel code onto Roku devices within seconds. In addition, developers can package and key their applications for preparing the Channel Store required assets.<br><br>

![Packaging channel](../../images/eclipse_7.png)

<h2>Installation Steps:</h2>
<p><i><b>Note:</b> Make sure any previous versions of the Roku plugin for Eclipse are uninstalled via Eclipse &gt; Help &gt; Installation Details &gt; BrightScript core &gt; Uninstall. In addition the minimum required version of Eclipse is the “Mars” release.</i></p>

<p><i><b>Workspace:</b> We encourage you to start your Roku projects in a fresh workspace. You can copy your projects back in afterwards. Thanks!</i></p>
<ol>
 	<li>Download Java version 8: <a href="http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html">oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html</a></li>
 	<li>Download the latest version of the Eclipse Installer _(currently version “Mars”)_ for Java IDE Developers: <a href="https://eclipse.org/downloads/installer-instructions.php">eclipse.org/downloads/installer-instructions.php</a></li>
 	<li>Add the Roku Plugin package via Eclipse &gt; Help &gt; Install New Software &gt; Add...
<ul>
 	<li>Name: Roku Plugin</li>
 	<li>Location: <a href="https://devtools.web.roku.com/ide/eclipse/plugin">https://devtools.web.roku.com/ide/eclipse/plugin</a></li>
 	<li>Follow the instructions and click Next... then Finish</li>
</ul>
</li>
</ol>
<h2>Note: Updated version available!</h2>
<p>We've released an updated version of the Roku Eclipse plugin following the release of OS 7.2 to patch bugs and regressions. Developers who installed the Eclipse plugin prior to August 1, 2016 should update the plugin by clicking Eclipse &gt; Help &gt; Install New Software &gt; Add...</p>
<ul>
 	<li>Name: Roku Plugin</li>
 	<li>Location: <a href="https://devtools.web.roku.com/ide/eclipse/plugin">https://devtools.web.roku.com/ide/eclipse/plugin</a></li>
 	<li>Follow the instructions and click Next.</li>
 	<li>You'll receive a message saying that "'BrightScript Core'" is already installed, so an update will be performed instead." Click Finish.</li>
 	<li>Restart Eclipse.</li>
</ul>
**Related resources:**
<ul>
 	<li><a href="http://www.eclipse.org/downloads/">http://www.eclipse.org/downloads/</a></li>
 	<li><a href="https://devtools.web.roku.com/ide/eclipse/plugin">https://devtools.web.roku.com/ide/eclipse/plugin</a></li>
 	<li><a href="https://sdkdocs.roku.com/display/sdkdoc/Roku+SDK+Documentation">https://sdkdocs.roku.com/display/sdkdoc/Roku+SDK+Documentation</a></li>
</ul>
