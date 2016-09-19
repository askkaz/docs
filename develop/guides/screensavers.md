# Screensavers for Roku OS

_Entertain your viewers with custom screensavers_

![Sample Screensaver](../../images/screensaver-preview.png)

### Overview

Screensavers are simply channels designed to be customizable display screens that can be played in the background. Screensavers use the same features as any other channel to design a UI; all they require is a different entry point from the `main()` function. With the release of OS 7.2, screensavers can now be created in SceneGraph for flexible and customizable UIs and animations.

**Sections:**
* [Types of Screensavers](#types-of-screensavers)
* [Screensaver Entry Points](#screensaver-entry-points)
* [Creating a Screensaver](#creating-a-screensaver)

---

## Types of Screensavers

### Stand-alone Screensavers

Stand-alone screensavers are screensavers that only show up in the Screensaver Settings on Roku devices (i.e. they do not appear as a channel on the Roku home screen).

**Requirements for a stand-alone screensaver:**
* manifest uses `screensaver_title` in place of `title`
* manifest does not contain any `mm_icon` references
* only uses a `RunScreenSaver()` entry point

**Sample manifest:**
```brightscript
screensaver_title="Dog Screensaver"
major_version=1
minor_verstion-2
build_version=150
```

### In-channel Screensavers

In-channel screensavers are only displayed within a channel. These are commonly seen in music channels that want to use screensavers to show album cover art for songs playing.

**Requirements for in-channel screensavers:**
* manifest contains `mm_icon_focus_hd` attribute to show up as a channel on the homescreen
* manifest contains `screensaver_private=1` attribute
* channel uses the `RunScreenSaver` or `RunUserInterface` entry point in addition to the `Main()` function of the channel

> :information_source: In-channel screensavers will not appear in the screensavers menu and will override the current screensaver being used when the channel is running.

**Sample manifest:**
```brightscript
title="Dog Channel"
major_version=1
minor_verstion-2
build_version=150

mm_icon_focus_hd=pkg:/images/mm_icon_focus_hd.png

screensaver_private=1
```

### Screensaver Constraints:

1. SceneGraph based screensavers **can** play audio
2. SceneGraph based screensavers **cannot** play video
3. SceneGraph based screensavers **cannot** execute Channel Store APIs

## Screensaver Entry Points

When launching screensavers from Screensaver Settings, the `RunScreenSaver` function will be called and it will run as a stand-alone screensaver. When launching screensavers from the home screen, the `RunUserInterface` or `main()` function will be called and it will behave as a normal channel allowing the use of any BrightScript or SceneGraph components and user input.

Optionally, a `RunScreenSaverSettings` function can be used to implement settings such as changing colors, fonts, etc. The Settings option will be displayed under the Preview option in Screensaver Settings.

![Sample Channel Screenshot](../../images/screensaver-screenshot.png)

## Creating a Screensaver

When creating a screensaver with SceneGraph, we will be using the `roSGScreen` component. This will allow us to draw straight to the scene with nodes that we create in our XML file. We start off by creating these components in the `main.brs` file.

```brightscript
screen = CreateObject(“roSGScreen”)
```

When creating screensavers in the `RunUserInterface` function, a message port can be used to observe events from the SceneGraph XML. This is useful for triggering responses from the screensaver based off events from the SceneGraph XML.

```brightscript
m.port = CreateObject(“roMessagePort”)
screen.setMessagePort(m.port)

glb = screen.getGlobalNode()
glb.AddField(“MyField”, “int”, true)
glb.MyField = 100

Scene = screen.createScene(“screensaver”)
screen.show()
```

Implementing a `while` loop will also help keep track of data from screensavers. It’s also useful for continuously changing fields such as observers that constantly receive events to progress animations, color changes, background switches, etc.

```brightscript
while(true)
    Msg = wait(2000,m.port)
    if (msg <> invalid)
        if msgType = “roSGScreenEvent”
            if msg.isScreenClosed() then
                return
        End if
    else
        glb.MyField - glb.MyField + 10
    End if
End while
```

The `MyField` function can also have an observer from the `init()` function that will be called everytime the field changes:

```brightscript
m.global.observeField(“MyField”, “changeBackGroundImage”)
```

### Initialization

One of the first items to run when a channel is launched is the `init()` function. This function can be used to call other functions, set backgrounds, and establish event listeners in SceneGraph. This BrightScript function can be embedded in SceneGraph using a `<script>` tag to access other fields in SceneGraph.

```brightscript
function init()
    m.animationNode = m.top.findNode(“SceneAnimation”)
    m.top.backgroundURI = “pkg:/images/background.jpg”
    slideRectangle()
end function
```

![Screensaver animations](../../images/screensaver-preview.png)

### Animations

It’s also possible to create animations in screensavers using animation nodes. Simply create the node that you want to animate and then use an animation node to modify its behavior.

```xml
<Rectangle id="Box"
    color="0x0000FFFF"
    width="500"
    height="400"
    translation="[300, 150]" >
    <Label text="Screensaver Example" horizAlign="center" vertAlign="center" width="300" height="200" color="0x200000FF"/>
</Rectangle>

<Animation id="SceneAnimation" repeat="true" duration="10" easeFunction="linear" >
    <Vector2DFieldInterpolator id="AnimInterp"
        key = “[0,1]”
        keyValue = “[[0,0],[500,500]]”
        FieldToInterp = “Box.translation” />
</Animation>
```

## Additional Resources
This is just one example of using SceneGraph to design a layout for screensavers. Follow the links below to find different examples of what can be done with screensavers.

* SDK documentation: https://sdkdocs.roku.com/display/sdkdoc/Screensavers
* Screensaver examples: https://roku.box.com/v/screensaver-examples

> :information_source: Special thanks and credit to Jason Benjamin for the artwork used in these screensaver examples. **Jason** ([@PerfectHue](https://www.instagram.com/perfecthue)) is based in Los Angeles and is focused on crafting motion graphics, Virtual Reality, and interactive design experiences. You can find his body of work at [perfecthue.com](http://www.perfecthue.com).
