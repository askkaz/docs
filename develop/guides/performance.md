# SceneGraph Performance Guide

### Overview

As a Roku developer, building a unique and visually appealing channel is likely one the first things on your mind - and rightfully so.
While this is certainly possible (and highly encouraged!) with SceneGraph, it's important to remember that functionality and performance should be priorities when designing a channel. Even if your channel is aesthetic and your content entertaining, users likely won't stick around long enough to watch it if there are delays in input response times, low framerate, or slow content delivery.

Since the release of the Roku 2 platform, Roku's product line has expanded such that there are significant hardware capability differences between [models](/develop/specifications/roku-devices.md). To ensure that your content can reach the entire Roku audience watching on the whole range of devices we offer, you should use this guide to help provide a smooth, lag-free experience for users on even the lowest end devices.

* * *

## Performance Bottlenecks

### Texture Memory

A common offense is simply using too much texture memory. It's important to realize that simply using a larger image does not necessarily ensure a higher quality end result. Rather, using unnecessarily large images will more often than not result in performance issues.
All Roku devices have a dedicated amount of texture memory, which varies largely from device to device. Each _unique_ image you would like to display on your channel will take up a certain amount of the limited texture memory (however, reusing the same image on multiple nodes will not take up more memory).
More specifically, the **size in bytes** of the image file does not matter (so compressing your images is inconsequential), rather, the **pixel dimension** of the image is strictly important. Images are loaded into texture memory in the form of bitmaps, taking up 4 bytes per pixel (RGBA). A quick calculation (width x height x 4B) can help you approximate how much texture memory your images will be taking up.

Here is small list of the amount of texture memory available to your channel to use on various devices:

*   Roku: 20 MB
*   Roku2: 44-45 MB
*   Roku3: 60 MB

If your channel ends up going over any of these limits by trying to display more than what the texture memory can allow for, then your channel will run into unexpected behaviour on those devices. A common symptom is flickering images or slow content loading, as bitmaps will be constantly unloaded and reloaded onto memory in an effort to manage the excess images. Even if your images do not use up all the texture memory on a device, your channel will load slower in general if it contains larger images.

#### How Can I Avoid This?

**Make images smaller.** The simplest solution! If you're planning on displaying an image on a 200x200 Poster node, don't load in and render a 1920x1080 image. It will work, but it'll be a waste of system resources for no real benefit.
A quick calculation puts a 1920x1080 image at using a whopping (1920•1080•4 = **~8.3MB**) of memory, while the appropriately sized 200x200 image will only take up **~0.16MB**.
Using the loadWidth and loadHeight fields of a Poster node would be an equivalent solution to resizing the images themselves.

**Use minimalistic item renderers.** The fewer elements, the better. Use [Rectangle](https://sdkdocs.roku.com/display/sdkdoc/Rectangle) nodes, which do not require a bitmap loaded into memory, over [Poster](https://sdkdocs.roku.com/display/sdkdoc/Poster) nodes whenever possible. Keep in mind that even bitmaps for elements like focus rings and keyboard backgrounds take up texture memory - so take care to not use unnecessarily large images for these.

### System Memory

Specifically, we are talking about DRAM. Roku devices have anywhere from 256 MB on the lowest end devices, to 1.5 GB on the Roku 4 platform. While many applications like image processing or 3D modeling software benefit greatly from a large amount of RAM, this is usually not the case for channels running on Roku OS. For nearly all channels, RAM will not be a bottleneck for performance unless you have a serious memory leak somewhere. A channel is far more likely to hit the texture memory or CPU ceiling than to ever run out of RAM, and your channel is sandboxed such that the Roku device will always allocate and save enough RAM for video buffering. In addition, if your channel uses a large amount of RAM (over ~80MB) it will simply be killed before performance hits are noticeable.

### Processing Power

Another common performance bottleneck. If your channel is experiencing low framerate or laggy transitions, this is probably the culprit.
The difference in CPU between the lowest and highest end Roku device is very large, and will likely only continue to grow as new models are released. As such, it's important to keep in mind that the animation that runs smoothly on a Roku 4 might not look as good, or even work at all, on a Roku 1. You can refer back to the list of [models](https://sdkdocs.roku.com/display/sdkdoc/The+Roku+Channel+Developer+Program#TheRokuChannelDeveloperProgram-RokuModels) to see more exact specifications for each model, but generally it's enough to be conscious of CPU intensive tasks and their impact on older devices.

#### How Can I Avoid This?

**Use Animations _Somewhat_ Sparingly.** [Animations](https://sdkdocs.roku.com/display/sdkdoc/Animation) and their associated interpolators require a non-inconsequential amount of computational power (some quantitative data can be found in the FAQ below). An excess of Animation nodes running simultaneously can cause performance issues, although non-concurrent animations will be no problem.
_However, keep in mind it is generally not an excess of animations that cause performance issues (although it is certainly possible)._ Rather, poor texture management or interference from other threads are usually the root cause of stuttering animations. Having many animations can exacerbate any performance issues a channel is having and make it exceedingly obvious to the user. In that case, it would be best to simply avoid animated transitions for large UI layouts with multiple complex elements.

**Use Less Task Nodes.** Task nodes are an essential tool for a channel looking to make any asynchronous calls separate from the main Brightscript thread and the render thread. At the same time, spawning too many different threads is an easy way to create laggy and unresponsive channels. Not only should you take care to follow all of the guidelines listed in the [Task node class documentation](https://sdkdocs.roku.com/display/sdkdoc/Task), be aware that a common problem is calling too many simultaneous URL requests from multiple Task nodes. Depending on network speed and other factors, this could cause serious performance issues and result in HTTP timeouts which prevent content from reaching your users.

* * *

## Optimization Techniques

### SGNode Initialization

**Offload Initialization.** Keep init() in the main scene and its static children as minimal as possible. Having too much "upfront" initialization will cause the channel to take a long time loading the main scene. Leave as much initialization as possible for the task thread function.

### Data Flow

**Copying Nodes:** When copying nodes, do not simply call:

```
node2.setFields(node1.getFields())
```

Setting nonexistent fields in a node will invoke additional internal verification and warning outputs to the debug console, causing UI lag. Instead, do something like:

```Brightscript
function cloneNode(oldNode as Object) as Object
  newNode = createObject("roSGNode",oldNode.subtype()) // subtyped node should automatically have all the fields of the original node
  newNode.setFields(oldNode.getFields())
  return newNode
end function
```

**ContentNode vs. Associative Arrays?** Use [ContentNode](https://sdkdocs.roku.com/display/sdkdoc/ContentNode) fields to represent complex trees of nested data that are expensive to copy, since they will be passed by reference. Use associative arrays to store small, shallow data structs. Associative arrays will be deep-copied through fields (pass-by-value) and has the advantage of keeping parallelization safer and more efficient.

**Avoid onChange in Task Threads.** If you'd like a Task node to execute a function in response to a field change, use the overloaded version of **[observeField()](https://sdkdocs.roku.com/display/sdkdoc/ifSGNodeField#ifSGNodeField-observeField())** to send an roSGNodeEvent to your message port. Do this instead of setting **onChange** in the field you want to watch. While this is certainly not necessary, it might improve visual performance since onChange is usually executed on the render thread.

* * *

## Debugging Texture Memory Performance

You can check your texture memory usage by telnetting to port 8080 on your Roku device and running the command “r2d2_bitmaps”. This command will output a list of memory addresses representing the assets loaded into texture memory, their width and height, as well as their size in bytes. At the bottom, it also shows the available memory you have on your device left, the amount used, and the amount that the device has in total.

## Frequently Asked (Performance) Questions

**Can I have a background video playing in my channel navigation screen?**
Sure. A common channel design is to have a video playing in the background with a RowList or GridList menu overlayed on top. Check out my example implementation [here](https://github.com/andyyu/roku-channel-samples/tree/master/RowListBGVideoTest) to test the performance implications of such a design. There are delays while the video is loading (it is therefore recommended to use a low-res video for something unimportant like a background video), but once it is loaded, there are no further performance decreases that can be attributed to the inclusion of the video.

**How many animations can I use?**
Testing on a higher end device with a dedicated GPU like a Roku 3 has shown it can handle up to 800 [Animation Nodes](https://sdkdocs.roku.com/display/sdkdoc/Animation), each with its own Interpolator, running at the same time without any performance issues. This is likely far more than a reasonable channel will ever need to use. However, on a Roku 2 XS, the channel showed visible lag at just 50 simultaneous Animation Nodes. Even worse was on a Roku 1, which had trouble with 20 Animation Nodes at the same time.
These tests were run on a channel with no other components, so take the exact numbers with a grain of salt. In a real channel, there will likely be other things (Task threads, loading content, user channel navigation, etc.) that will compete with system resources. Instead, you should take note of the large difference between the performance capabilities of a high end device and a low end device and remember to develop your channel accordingly.
**Another note on animation usage:** There was no noticeable performance difference between animating a full screen, high resolution image and animating a small Rectangle. While there may be other costs involved, like in the load time / render time / texture memory usage of the image, the actual CPU usage of the Animation and Interpolator did not change depending on what kind of content it was applied to.

**How many items can I put in a RowList / MarkupGrid / PosterGrid, etc.?**
In theory, as many as you want. SceneGraph Lists and Grids utilize a content manager that automatically loads and unloads bitmaps from texture memory as items in the list/grid are revealed and hidden. Try out this [test channel](https://github.com/andyyu/roku-channel-samples/tree/master/RowListTest) and notice that once the RowList is loaded, having hundreds of images in each row shows little to no performance difference over having just ten - even on a low end device.
However, keep in mind that the initial loading of all of the content into the list or grid still takes time, so trying to download too many large assets or data at once will result in delays and significant load times.

**Help! My channel is still lagging!**
Go through this check list one more time.

*   Switch all your images with the lowest resolution possible (before a noticeable decrease in visual quality). A 3840x2160 image and a 360x240 image will look exactly the same on a 360x240 Poster.
*   Avoid using or gracefully degrade large scale UI animated transitions for lower end devices. Not that it takes up an especially large amount of resources, but a full screen image fading in and out in the background makes it blatantly obvious when your channel is experiencing even the slightest performance lag.
*   Reduce the amount of content loading you're doing at once. If you have multiple Task nodes running hundreds of urlTransfers at once, there will be lag. Load content dynamically as the user needs it.
*   Change the channel's UI to reduce the number of rendered nodes on the screen. If you want 50 Poster nodes overlayed on a changing background video with an animated HUD, then it's likely time to reconsider the UI and compromise for low-end hardware compatibility.

If there are still issues, reach out through one of our developer help outlets (email, forums) and we'll take a look.
