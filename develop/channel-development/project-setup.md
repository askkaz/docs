*Creating the structure for channel applications*

<h2>Project setup</h2>

To start off, create a directory for the application it will contain, such as *VideoExample*. Within this directory, create the following subdirectories and files:

* *source* directory
* *components* directory
* *images* directory
* *manifest*

<h3>Source Directory</h3>

The source directory contains BrightScript code for the main application’s execution thread with the extension *.brs*. Since applications including SceneGraph scenes allow BrightScript code to either be embedded in, or used by, an XML component file in a *&lt;script&gt;* element, for many SceneGraph applications this directory will only contain a *main.brs* file to start the application. The *main.brs* file only need have enough BrightScript code to start the application by creating and displaying the scene specified in the SceneGraph scene.

The following shows a *main.brs* file that starts the application by creating and showing the scene defined in the SceneGraph scene named *VideoExample* (the *VideoExample* scene is defined in an XML component file in the components directory in the next section).

<pre><code>sub Main()
   screen = CreateObject("roSGScreen")
   m.port = CreateObject("roMessagePort")
   screen.setMessagePort(m.port)

   scene = screen.CreateScene("VideoExample")
   screen.show()
   
   # exit the channel if back button is pressed at top-level
   while(true)
       msg = wait(0, m.port)
       msgType = type(msg)
       if msgType = "roSGScreenEvent"
           if msg.isScreenClosed() then return
       end if
   end while
end sub</code></pre>

<h3>Components Directory</h3>

The components directory contains all the XML component and associated BrightScript code files needed for your SceneGraph scene. The XML files must have the extension *.xml*, and BrightScript code files must have the extension *.brs*. 

Each XML component file contains a single *&lt;component&gt;* element that contains a specific SceneGraph node/element tree defining that component. When the channel is launched, all the files with extension *.xml* in the *components* directory are loaded and added to the available types of nodes that can be created.

<h3>Images Directory</h3>

Any graphic image files to be included in the application package are stored in the *images* directory. At a minimum, the *images* directory must contain the *mm_icon_focus* images and splash screen graphic files described in the following section.

<h3>Manifest File</h3>

At the root level there must be a file named *manifest* which contains attributes for the application. The attributes specified in the *manifest* include the name and version number of the application, the application image to be used on the main menu, etc.

* Each attribute is on a separate line, and has the form *name=value*
* Each name=value pair must end with a newline character, or it may not be parsed by the firmware
* The last line must end with a newline character
* Empty lines are ignored
* Lines beginning with a '#' (number sign) are comment lines and are ignored

The following fields are required:

<pre><code>##   Channel Details
title=application_title 
major_version=major_version_number 
minor_version=minor_version_number 
build_version=build_version_number

##   Channel Assets
###  Main Menu Icons / Channel Poster Artwork 
#### Image sizes are FHD: 540x405px | HD: 290x218px | SD: 214x144px
mm_icon_focus_fhd=FHD_focus_graphic_file_URI
mm_icon_focus_hd=HD_focus_graphic_file_URI 
mm_icon_focus_sd=SD_focus_graphic_file_URI 

###  Splash Screen + Loading Screen Artwork 
#### Image sizes are FHD: 1920x1080px | HD: 1280x720px | SD: 720x480px
splash_screen_sd=SD_splash_screen_graphic_file_URI 
splash_screen_hd=HD_splash_screen_graphic_file_URI 
splash_screen_fhd=FHD_splash_screen_graphic_file_URI 
</code></pre>

The various *graphic_file_URI* field values are used to specify a graphic that allows a user to select your application and a "splash" screen that appears as the application is loading.

All graphics files specified in the manifest file should be included in the *images* directory.

The URI to set the path to the files should use the *pkg:* resource prefix, such as *pkg:/images/splash_sd.jpg*.