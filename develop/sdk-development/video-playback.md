# Playing Video in SceneGraph

This guide demonstrates adding video to a SceneGraph project which is a continuation from [Building a UI in SceneGraph](/develop/sdk-development/scenegraph-ui.md). This guide will use the same example project.

The main steps include:

1. [Create a video node](#1-create-a-video-node)
2. [Setup the video content](#2-setup-the-video-content)
3. [Map the back button](#3-map-the-back-button)

> :information_source: The following nodes and methods are used in this guide.
* [Video Node](https://sdkdocs.roku.com/display/sdkdoc/Video)
* [Content Node](https://sdkdocs.roku.com/display/sdkdoc/ContentNode)
* [OnKeyEvent()](https://sdkdocs.roku.com/pages/viewpage.action?pageId=1608547)

---

## 1. Create a video node

Video playback in SceneGraph is done using the [Video Node](https://sdkdocs.roku.com/display/sdkdoc/Video).

In the `components` folder, open the `HomeScene.xml` file and the following code:

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

> :information_source: This is done at the end of the `.xml` file because we want the video to show in front of all our other nodes.

## 2. Setup the video content

We will setup our video content in BrightScript in the `HomeScene.brs` file that we created when designing our UI. In the `HomeScene.brs` file, it’s important to set a pointer upon loading that references our video node that we created.

```brightscript
m.Video = m.top.findNode(“Video”)
m.videoContent = createObject(“roSGNode”, “ContentNode”)
```

After doing this, we also create a Content Node (containing the meta-data for a piece of content) that we can assign to our Video Node later on.

Next, we set an observer function that waits for an item to be selected in our RowList so that it can set the content of our Video Node to the video content that we select from our `RowList`. The following observer calls the function `playVideo()` when an item is selected in our `RowList`.

```brightscript
m.RowList.observerField(“rowItemSelected”, “playVideo”)
```

The function `playVideo()` takes our content node named `m.videoContent` that we created earlier and assigns the video stream (mp4) to the field `videoContent.url`. It’s also important to set the `streamFormat` to one that matches the feed. In our case, we will set `m.videoContent.streamFormat` to `mp4`.

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

Now when an item in the `RowList` is selected, it will show a Video Node and play the content.

## 3. Map the back button

Lastly, to make sure the user is able to navigate back to the UI, we need a function that maps the Back button on the remote to leave the video. To do this, we'll create a function responding to an `onKeyEvent()` back button press. With the function below, the video will stop playing and be hidden when the back button is pressed and return to the UI.

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
