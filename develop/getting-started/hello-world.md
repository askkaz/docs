# Hello World

_How to load a sample channel application on your Roku device_
![Hello World](https://blog.roku.com/developer/files/2016/02/image05-1.png)

### Overview

In this guide, we will cover the essential steps for testing a ‘Hello World’ sample channel application on your Roku device.

**Steps:**

1. Review the [Developer Setup Guide](https://blog.roku.com/developer/2016/02/04/developer-setup-guide/)
2. Open the Developer Application Installer
3. [Download](https://github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip) and Install the Sample Channel Application
4. Edit the Sample channel Application
5. Re-upload Sample Channel onto a Roku device

<hr />

## Requirements to follow this guide:

* A Roku device: [roku.com/products/compare](https://www.roku.com/products/compare)
* A Roku account: [my.roku.com/signup](https://my.roku.com/signup)
* Download the sample channel app: [hello-world.zip](https://github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip)




## 1\. Review the [Developer Setup Guide](https://blog.roku.com/developer/2016/02/04/developer-setup-guide/)

The Roku Developer Setup guide enables any Roku device to install sample applications such as the basic hello world example in this guide.

**Developer Settings**         |  **Development Application Installer**
:-------------------------:|:-------------------------:
![Developer Settings](https://blog.roku.com/developer/files/2016/02/image00-1024x568.png)  |  ![Development Application Installer](https://blog.roku.com/developer/files/2016/02/image08-1024x489.png)


[Follow the Developer Setup Guide >](https://blog.roku.com/developer/2016/02/04/developer-setup-guide/)

## 2\. Open the Development Application Installer

After completing the steps covered in the [Developer Setup guide](https://blog.roku.com/developer/2016/02/03/developer-setup-guide/), open a web browser and navigate to the Roku device URL _(i.e._ [_http://192.168.x.x_](http://192.168.x.x)_)_ 

**_Note:_** _To connect your Roku device, make sure your computer and Roku are on the same local network._ 

[![Logging into Roku Device](https://blog.roku.com/developer/files/2016/02/image11-e1454565719777.png)](https://blog.roku.com/developer/files/2016/02/image11.png) 

**Roku device credentials** 
When you navigate to your Roku device, it will prompt for a **user name** (typically ‘rokudev’) and password was set during the Device Setup guide. Enter this information to continue. 

**Once the page successfully opens, you have successfully connected to the Roku device.**

The primary screen will show the development application installer: [![Development Application Installer](https://blog.roku.com/developer/files/2016/02/image08.png)](https://blog.roku.com/developer/files/2016/02/image08.png) 

_Depending on the Roku OS version, your installer page may look like this:_ [![Old style for Dev Application Installer](https://blog.roku.com/developer/files/2016/02/image04.png)](https://blog.roku.com/developer/files/2016/02/image04.png) 

**_Related guide:_** 
[_How to update the software on a Roku device_](https://support.roku.com/hc/en-us/articles/208755668-How-can-I-update-the-software-on-my-Roku-player-)

## 3\. Download and Install the Sample Channel Application

Now that you have enabled **Developer Mode** on your Roku device and logged in, we can continue with downloading and opening a Sample Channel Application. 

**Download the sample application located at:** [**github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip** ](https://github.com/rokudev/hello-world/raw/master/dist/apps/hello-world.zip)

Once downloaded, take the .zip application and upload it to your Roku device using the Developer Application Installer: [![Upload zip channel](https://blog.roku.com/developer/files/2016/02/image14.png)](https://blog.roku.com/developer/files/2016/02/image14.png) 

To finish this process, click on the **Install** button located below the upload option. If the sample channel contains no errors and the process runs successfully, the sample channel will launch on the Roku device: 

[![Hello World](https://blog.roku.com/developer/files/2016/02/image05.png)](https://blog.roku.com/developer/files/2016/02/image05.png) 

**Note:** Roku devices in “Developer Mode” will allow one “side-loaded” channel at a time. If you run this process again, the new channel upload will replace the existing channel. 

**Finding your Sample Channel on the Roku Device** The developer channel will be automatically placed in the bottom row of your main channels, also known as “My Channels”.

[![](https://blog.roku.com/developer/files/2016/02/roku-example-developer-app.png)](https://blog.roku.com/developer/files/2016/02/roku-example-developer-app.png)

## 4\. Editing the Sample Application

When you uncompress the .zip directory, you’ll see the following setup: 

[![File view of hello world](https://blog.roku.com/developer/files/2016/02/image07.png)](https://blog.roku.com/developer/files/2016/02/image07.png) 

**Here’s a breakdown of the common items inside the sample application:** [![](https://blog.roku.com/developer/files/2016/02/SceneGraph-Diagrams__12_Columns.png)](https://blog.roku.com/developer/files/2016/02/SceneGraph-Diagrams__12_Columns.png) 
For this example, you will open the [helloworld.xml](https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml) file that is located inside the components directory.

### **helloworld.xml**

[![hello world](https://blog.roku.com/developer/files/2016/02/image13.png)](https://blog.roku.com/developer/files/2016/02/image13.png) 

The example XML file above shows how a simple Label is created and centered on the screen. Specifically on [**Line 5**](https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml#L5), the Label’s value is set with [text="Hello World"](https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml#L5). **_Optional:_ **Review the code for additional attributes that can be set for this sample channel application. Change the value of the text field on line 5 to another phrase: 

[![helloooooo again](https://blog.roku.com/developer/files/2016/02/image15.png)](https://blog.roku.com/developer/files/2016/02/image15.png) 

After saving the edits to [helloworld.xml](https://github.com/rokudev/hello-world/blob/master/source/components/helloworld.xml), select all the items inside the directory and zip compress utility on your computer.

### Compressing the contents of the Hello World directory

**Note:** Remember to compress only the contents of the directory, not the parent folder. **For Example:** [![dont zip this way](https://blog.roku.com/developer/files/2016/02/image12.png)](https://blog.roku.com/developer/files/2016/02/image12.png) 

If you compress (“zip”) the parent folder, the Developer Application Installer will return an error. **The proper ways to compress the required files:** **Mac OS X:** Right click all selected files to compress into a .zip file. 

[![zip this way](https://blog.roku.com/developer/files/2016/02/image06.png)](https://blog.roku.com/developer/files/2016/02/image06.png) 

**Windows:** Simply select all the files and folders and right click to compress into a .zip file. 

[![windows compress zip](https://blog.roku.com/developer/files/2016/02/image02.png)](https://blog.roku.com/developer/files/2016/02/image02.png)

### Re-Upload the Channel Application

Once you have recompressed the Channel application, open a web browser and navigate again to the Roku device URL _(i.e._ _http://192.168.x.x__)_ [![upload zip file](https://blog.roku.com/developer/files/2016/02/image09.png)](https://blog.roku.com/developer/files/2016/02/image09.png) Upload the .zip file and click **Install** You will immediately see the edited phrase in your Sample Channel Application: [![Hellooooo Again!](https://blog.roku.com/developer/files/2016/02/image10.png)](https://blog.roku.com/developer/files/2016/02/image10.png)

## 5\. Explore the Developer docs!

Go to [sdkdocs.roku.com](http://sdkdocs.roku.com/) and explore the methods, parameters, and syntax for building rich and complex channel applications on the Roku platform. For samples regarding our new XML framework, Roku SceneGraph, go to [bit.ly/rokudevxml](http://bit.ly/rokudevxml) to get started!
