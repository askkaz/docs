This tutorial will show you how to add video to your SceneGraph project. If you haven’t already taken a look, see our previous guide on Building a SceneGraph UI here[link-to-building-SG-UI]! This tutorial will be using the same example project from the previous guide.

<i>Note: The following nodes and methods will be used in this guide.</i>

* [Video](link-to-video-docs)
* [Content Node](link-to-content-node-docs)
* [OnKeyEvent()](link-to-onkeyevent-docs)

<h2>Creating Your Video Node</h2>

To make Video in SceneGraph we will add our video node inside our HomeScene.xml file in your components folder.

<pre><code>&lt;children&gt;        
    &lt;Video
	    id = “Video”
	    height = “1080”
	    width = “1920”
	    enableUI = “false”
	    loop = “true”
	    visible = “false”/&gt;
&lt;/children&gt;
</code></pre>

Note that this is done at the bottom of our .xml file because we want the video to show in front of all our other nodes. A reference to the fields set into the video node can be found here [link-to-video-node-docs].

<h2>Setting Your Video Content</h2>

We will setup our video content in BrightScript in the HomeScene.brs file that we created when designing our UI. In the HomeScene.brs file, it’s important to set a pointer upon loading that references our video node that we created. 

<pre><code>m.Video = m.top.findNode(“Video”)
m.videoContent = createObject(“roSGNode”, “ContentNode”)
</code></pre>

After doing this, we also create a Content Node that we can assign to our video player later on.

Next, we set an observer function that waits for an item to be selected in our RowList so that it can set the content of our Video node to the video content that we select from our RowList. The following observer calls the function playVideo() when an item is selected in our RowList.

<pre><code>m.RowList.observerField(“rowItemSelected”, “playVideo”)</code></pre>

The function playVideo() takes our content node named m.videoContent that we created earlier and assigns our video stream (mp4) to the field videoContent.url. It’s also important to set the streamFormat to one that matches the feed. In our case, we will set the m.videoContent.streamFormat to “mp4”

<pre><code>Sub playVideo()
    m.videoContent.url = RowList.content.getChild(m.RowList.rowItemFocused[0]).getChild(m.RowList.rowItemFocused[1].URL
    ‘rowItemFocused[0] is the row and 
    'rowItemFocused[1] is the item index in the row
	
    m.videoContent.streamFormat = “mp4”
    m.Video.content = m.videoContent
    m.Video.visible = “true”
    m.Video.control = “play”
End Sub
</code></pre>

After, all that’s left is to play the video and make it visible. 

<h2>Mapping Your “Back” Button</h2>

To make sure that the user is able to navigate back to the RowList, we have to set a function that maps our “Back” button to leave the video. To do this we will use the onKeyEvent() function provided here in the SDK. In this function, we hide the video and stop it from playing when the back button on the controller is pressed so that we can go back to the RowList.

<pre><code>Function onKeyEvent(key as String, press as Boolean) as Boolean ‘Maps back button to leave video
	if press
		if key = “back” If the back button is pressed
			m.Video.visible = “false” ‘Hide video
			m.Video.control = “stop” ‘Stop video from playing
			return true
		end if
	end if
end Function
</code></pre>
