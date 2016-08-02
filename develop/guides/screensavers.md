<em>Entertain your viewers with custom screensavers</em>

<a href="https://blog.roku.com/developer/files/2016/07/Pasted-image-at-2016_07_08-11_06-AM.png"><img class="alignnone wp-image-1312" src="https://blog.roku.com/developer/files/2016/07/Pasted-image-at-2016_07_08-11_06-AM.png" alt="Sample Screensaver" width="613" height="345" /></a>
<h2><span style="font-weight: 400;">Overview</span></h2>
<span style="font-weight: 400;">Screensavers are simply channels designed to be customizable display screens that can be played in the background. Screensavers use the same features as any other channel to design a UI; all they require is a different entry point from the <code>main()</code>. With the release of OS 7.2, screensavers can now be created in SceneGraph for flexible and customizable UIs and animations.</span>
<h2><span style="font-weight: 400;"><!--more-->Types</span></h2>
<h3><span style="font-weight: 400;">Public Screensavers</span></h3>
<span style="font-weight: 400;">Similarly to traditional BrightScript screensavers, SceneGraph screensavers will also use the <code>RunScreenSaver</code> entry point with the option of including a <code>RunUserInterface </code>or <code>Main()</code> function. Screensavers that implement a <code>RunUserInterface</code> function also have the option to launch from the Home Screen in addition to the screensavers menu.</span>
<h3><span style="font-weight: 400;">Private Screensavers</span></h3>
<span style="font-weight: 400;">Private screensavers are only displayed within a specific channel. These are commonly seen in music channels that want to use screensavers to show album cover art for songs playing. Screensavers can be made private by creating an entry named “screensaver_private” in the manifest file of its current channel.</span>

<b><i>Note: </i></b>P<span style="font-weight: 400;">rivate screensavers will not appear in the screensavers menu and will override the current screensaver being used when the channel is running. </span>

<strong>Constraints:</strong>
<ol>
<li style="font-weight: 400;"><span style="font-weight: 400;">SceneGraph based screensavers </span><b>cannot</b><span style="font-weight: 400;"> play video </span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">SceneGraph based screensavers </span><b>can</b><span style="font-weight: 400;"> play audio</span></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">SceneGraph based screensavers </span><b>cannot</b><span style="font-weight: 400;"> execute Channel Store APIs</span></li>
</ol>
<h2><span style="font-weight: 400;">Screensaver Entry Points</span></h2>
<span style="font-weight: 400;">When launching screensavers from the screensaver menu, the <code>RunScreenSaver </code>function will be called and it will run as a normal screensaver.</span>

<span style="font-weight: 400;">When launching screensavers from the home screen, the <code>RunUserInterface</code> function will be called and it will behave as a normal channel allowing the use of any Brightscript or SceneGraph components and user input.</span>

<span style="font-weight: 400;">Optionally, a <code>RunScreenSaverSettings</code> function can be used to modify settings such as colors, fonts, etc. The settings option will be displayed under the preview option in the screensavers menu.</span>

<a href="https://blog.roku.com/developer/files/2016/07/Pasted-image-at-2016_07_08-11_08-AM.png"><img class="alignnone wp-image-1314" src="https://blog.roku.com/developer/files/2016/07/Pasted-image-at-2016_07_08-11_08-AM.png" alt="Sample Channel SS" width="617" height="347" /></a>
<h2><span style="font-weight: 400;">Creating a Screensaver</span></h2>
<b>BrightScript (Main.brs)</b>

<span style="font-weight: 400;">When creating a screensaver with SceneGraph, we will be using the <code>roSGScreen </code>component. This will allow us to draw straight to the scene with nodes that we create in our XML file. We start off by creating these components in our main BrightScript file.</span>
<pre><code>screen = CreateObject(“roSGScreen”)
</code></pre>
<span style="font-weight: 400;">When creating screensavers in the <code>RunUserInterface </code>function, a message port can be used to observe events from the SceneGraph XML. This is useful for triggering responses from the screensaver based off events from the SceneGraph XML.</span>
<pre><code>m.port = CreateObject(“roMessagePort”)
screen.setMessagePort(m.port)

glb = screen.getGlobalNode()
glb.AddField(“MyField”, “int”, true)
glb.MyField = 100

Scene = screen.createScene(“screensaver”)
screen.show()
</code></pre>
<span style="font-weight: 400;">Implementing a while loop will also help keep track of data from screensavers. It’s also useful for continuously changing fields such as observers that constantly receive events to progress animations, color changes, background switches, etc. </span>
<pre><code>while(true)
Msg = wait(2000,m.port)
If (msg <> invalid)
If msgType = “roSGScreenEvent”
If msg.isScreenClosed() then
Return
End if
else
glb.MyField - glb.MyField + 10
End if
End while
</code></pre>
<span style="font-weight: 400;">The <code>MyField</code> function can also have an observer from the <code>init() </code>function that will be called everytime the field changes:</span>
<pre><code>m.global.observeField(“MyField”, “changeBackGroundImage”)
</code></pre>
<h2><b>Initialization</b></h2>
<span style="font-weight: 400;">One of the first items to run when a channel is launched is the <code>init() </code>function. This function can be used to call other functions, set backgrounds, and establish event listeners in SceneGraph. This BrightScript function can be embedded in SceneGraph using a <code><script></code> tag to access other fields in SceneGraph.</span>
<pre><code>function init()
m.animationNode = m.top.findNode(“SceneAnimation”)
m.top.backgroundURI = “pkg:/images/background.jpg”
slideRectangle()
end function
</code></pre>
<a href="https://blog.roku.com/developer/files/2016/07/image01.jpg"><img class="aligncenter size-large wp-image-1299" src="https://blog.roku.com/developer/files/2016/07/image01-1024x576.jpg" alt="Screensaver animations" width="1024" height="576" /></a>
<h2><span style="font-weight: 400;">Animations</span></h2>
<span style="font-weight: 400;">It’s also possible to create animations in screensavers using animation nodes. Simply create the node that you want to animate and then use an animation node to modify its behavior.</span>
<pre><code><Rectangle id="Box"
color="0x0000FFFF"
width="500"
height="400"
translation="[300, 150]"
>
<Label text="Screensaver Example" horizAlign="center" vertAlign="center" width="300" height="200" color="0x200000FF"/>
</Rectangle>

<Animation id="SceneAnimation" repeat="true" duration="10" easeFunction="linear" >
<Vector2DFieldInterpolator id="AnimInterp"
key = “[0,1]”
keyValue = “[[0,0],[500,500]]”
FieldToInterp = “Box.translation”
/>
</Animation>
</code></pre>
<span style="font-weight: 400;">This is just one example of using SceneGraph to design a layout for screensavers. Follow the link below to find different examples of what can be done with screensavers.</span>

<b>Additional Resources</b>
<ul>
<li style="font-weight: 400;"><span style="font-weight: 400;">Documentation on entry points and private screensavers: </span><a href="https://sdkdocs.roku.com/display/sdkdoc/Screensavers"><span style="font-weight: 400;">sdkdocs.roku.com/display/sdkdoc/Screensavers</span></a></li>
<li style="font-weight: 400;"><span style="font-weight: 400;">Sample code for additional example screensaver apps: <a href="https://roku.app.box.com/s/zrs06qiz4ss4gs2bwt02pbi3cn5us1i4">roku.app.box.com/s/zrs06qiz4ss4gs2bwt02pbi3cn5us1i4</a></span></li>
</ul>
<em><strong>Note:</strong> Special thanks and credit to Jason Benjamin for the artwork used in these screensaver examples. </em>

<em>Jason (<a href="https://www.instagram.com/perfecthue/">@PerfectHue</a>) is based in Los Angeles and is focused on crafting motion graphics, Virtual Reality, and interactive design experiences. You can find his body of work at <a href="http://www.perfecthue.com/">perfecthue.com</a></em>