# Playing Video in SceneGraph

This guide demonstrates adding video to a SceneGraph project which is a continuation from [Building a SceneGraph UI](/develop/channel-development/scenegraph-ui.md). This guide uses the same example project.

The main steps include:

1. [Create a video node](#1-create-a-video-node)
2. [Setup the video content](#2setup-the-video-content)
3. [Map the back button](#3-map-the-back-button)

> :information_source: The following nodes and methods are used in this guide.
* [Video Node](https://sdkdocs.roku.com/display/sdkdoc/Video)
* [Content Node](https://sdkdocs.roku.com/display/sdkdoc/ContentNode)
* [OnKeyEvent()](https://sdkdocs.roku.com/pages/viewpage.action?pageId=1608547)

## 1. Create a video node

To make Video in SceneGraph we will add our video node inside our HomeScene.xml file in your components folder.

```brightscript
<children>
    <Video
        id = “Video”
        height = “1080”
        width = “1920”
        enableUI = “false”
        loop = “true”
        visible = “false”/>
</children>
```

> :information_source: This is done at the bottom of the `.xml` file because we want the video to show in front of all our other nodes. A reference to the fields set into the video node can be found [here](https://sdkdocs.roku.com/display/sdkdoc/Video).

## 2. Setup the video content

We will setup our video content in BrightScript in the `HomeScene.brs` file that we created when designing our UI. In the `HomeScene.brs` file, it’s important to set a pointer upon loading that references our video node that we created.

```brightscript
m.Video = m.top.findNode(“Video”)
m.videoContent = createObject(“roSGNode”, “ContentNode”)
```

After doing this, we also create a Content Node that we can assign to our Video Node later on.

Next, we set an observer function that waits for an item to be selected in our RowList so that it can set the content of our Video Node to the video content that we select from our `RowList`. The following observer calls the function `playVideo()` when an item is selected in our `RowList`.

```brightscript
m.RowList.observerField(“rowItemSelected”, “playVideo”)
```

The function `playVideo()` takes our content node named m.videoContent that we created earlier and assigns our video stream (mp4) to the field `videoContent.url`. It’s also important to set the `streamFormat` to one that matches the feed. In our case, we will set `m.videoContent.streamFormat` to `mp4`

```brightscript
Sub playVideo()
    m.videoContent.url = RowList.content.getChild(m.RowList.rowItemFocused[0]).getChild(m.RowList.rowItemFocused[1].URL
    ‘rowItemFocused[0] is the row and rowItemFocused[1] is the item index in the row

    m.videoContent.streamFormat = “mp4”
    m.Video.content = m.videoContent
    m.Video.visible = “true”
    m.Video.control = “play”
End Sub
```

After, all that’s left is to play the video and make it visible.

## 3. Map the back button

To make sure that the user is able to navigate back to the `RowList`, we have to set a function that maps our Back button to leave the video. To do this we will use the `onKeyEvent()` function. In this function, we hide the video and stop it from playing when the back button on the controller is pressed so that we can go back to the `RowList`.

```brightscript
Function onKeyEvent(key as String, press as Boolean) as Boolean ‘Maps back button to leave video
    if press
    	if key = “back” If the back button is pressed
		m.Video.visible = “false” ‘Hide video
		m.Video.control = “stop” ‘Stop video from playing
		return true
	end if
    end if
end Function
```
