# Trick Play Overview

![BIF Example](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/YmlmX3NjcmVlbnNob3QtMTQ2OTgzMjM1MjIxNw==.jpg)

### Overview

Trick Play is a feature of digital video **activated when a user fast-forwards or rewinds**. The device displays **a small image frame preview** to help the viewer look for the right spot in the content that they want to watch. It is a feature that mimics the visual feedback given during the same operations that were provided by analog systems such as VCRs.

**Roku BIF**

Roku devices implement trick mode by using our BIF (Base Index Frame) file format. A BIF file, much like a ZIP-compressed folder, is used to encapsulate a set of images. It also includes some additional metadata, such as the total number of images, and their timestamp values.

**Sections:**

* [Creating BIF files](#creating-bif-files)
  * [Mac and Linux](#mac-and-linux)
  * [Windows](#windows)
* [Using BIF files](#using-bif-files)

---

## Creating BIF Files
We provide command-line tools for Mac, Windows, and Linux that lets you generate BIF files for your videos.

### Mac and Linux

#### Mac Installation
**Prerequisites:**

- [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)
- [Homebrew](http://brew.sh/)*
- [FFmpeg](https://ffmpeg.org/)

> :information_source: Homebrew is a command-line package manager for Mac OS X. It is **not required** to use Roku's BIF tool, but it can be used to easily install FFmpeg.

After you have Xcode and Homebrew installed, open your terminal application and run: `$ brew install ffmpeg`

Download and unzip: [biftool_mac.zip](https://sdkdocs.roku.com/download/attachments/3737253/biftool_mac.zip?version=1&modificationDate=1461287453365&api=v2)

#### Linux Installation
**Prerequisites:**

- ffmpeg-lib

On RedHat and Fedora Core, you can typically install `ffmpeg-lib` by running this yum command as root: `$ yum install ffmpeg-libs`

Download and unzip: [biftool_linux.zip](https://sdkdocs.roku.com/download/attachments/3737253/biftool_linux.zip?version=1&modificationDate=1461287442035&api=v2)

The executables are compiled for **Linux x86 64-bit machines**. Make sure that the `biftool` and `biftool_processor` executables are in the same directory on the development machine.

### Mac and Linux Usage
The BIF tool will automatically generate three `.bif` files: one for SD, one for HD, and one for FHD.

**Example:**
```
$ path/to/biftool ~/public_html/Movies/HarryPotter/HLS/600000/*.ts
Finding candidate frames in 917 files
Detected stream PTS offset of 10033ms
Captured 2368 candidate frames in 79s
Selected 915 BIFs
Success: ./fileSequence0000-fhd.bif (size=14.096MiB, numImages=915, avgSize=15.767KiB)
Success: ./fileSequence0000-hd.bif (size=8.528MiB, numImages=915, avgSize=9.535KiB)
Success: ./fileSequence0000-sd.bif (size=3.920MiB, numImages=915, avgSize=4.378KiB)
```

---

### Windows

#### Windows Installation
Download and Unzip: [biftool_windows.zip](https://sdkdocs.roku.com/download/attachments/3737253/biftool_windows.zip?version=1&modificationDate=1461287812523&api=v2)

#### Windows Usage
The simplest way to use the command-line tool is to open your favorite terminal application, and drag the biftool executable to its window. After that, just add the path to a video and biftool will generate the BIF files and save them to your current directory.

For example: `$ ./path/to/biftool ./path/to/video-file.mp4`

You can also type `--help` after dragging the biftool executable, and the terminal will display a [help message](#executable-help) containing more details and options about using the tool.

We recommend generating two `.bif` archives for each piece of content, one for SD and one for HD. Roku devices automatically select which version will be used **depending on the user UI**.  That is why it is important to generate HD `.bif` archives even if the content is SD. If there is no HD `.bif` available, the player will fallback to using the SD `.bif`.

**Example:**
```
$ mkdir abc-sd abc-hd
$ ffmpeg -i abc.mp4 -r .1 -s 240x180 abc-sd/08d.jpg
$ ffmpeg -i abc.mp4 -r .1 -s 320x240 abc-hd/08d.jpg
$ path/to/biftool -t 10000 abc-sd
$ path/to/biftool -t 10000 abc-hd
```

This will result in two new files: `abc-sd.bif` and `abc-hd.bif`.

There are two caveats here:

- FFmpeg generates the JPG files starting with index 1. This means that all the timestamps will be off by 10 seconds. To fix this, use the following command (make sure you are in the directory containing the `.bif` files): `$ % j=00000000.jpg; for i in *; do mv ${i} ${j}; j=${i}; done;`

- The SD frames should have a width of 240, and the HD frames should have a width of 320. Their height should be specified to coincide with their aspect ratio. The commands above assume a 4x3 aspect ratio. Unfortunately, FFmpeg doesn't let you specify only a width, keeping the original aspect ratio. If your source file is not 4:3, you should calculate the height used in the commands above using the width and the aspect ratio.

Here's a table of common resolutions:

| Display | Aspect Ratio | Width | Height |
| ------- | ------------ | ----- | ------ |
| SD | 4:3 | 240 | 180
| HD | 4:3 | 320 | 240
| HD | 16:9 | 320 | 180
| HD | 2.35 | 320 | 136

#### Executable Help
```
biftool <options> <target(s)>

Three types of <target(s)> are allowed:

1) A single <target> which is a directory. All files in the directory will be archived into single BIF file with the same name as the directory.

2) A single <target> which is a file with a .bif suffix. Its contents will be extracted into a new directory with the same name as the file. E.g., extracting mymovie-hd.bif will create and populate a directory named mymovie-hd.

3) One or more <targets> which are files that do not have a .bif suffix. These files are assumed to be video files, such as .mkv, .mp4 and .ts files. Frames will be extracted from the first video stream in each file, to create a single .bif file with the same base name as the first video file specified. If more than one video file is specified, they are expected to be segments of the same video and must be specified in playback order, based on the presentation timestamps (PTSes) within the files

Available options:
  --target arg                      The file(s) or directory on which to
                                   operate.
  -t [ --timestamp-multiplier ] arg The absolute presentation timestamp (PTS)
                                    in milliseconds is the filename multiplied
                                    by this value.
  -v [ --verbose ]                  Be verbose about activity.
  -h [ --help ]                     Help message.
```

## Using BIF Files
For instructions on how to use the generated BIF files in your content feed, please refer to the following docs:

**SDK Docs** - [Content Metadata, Playback Configuration Attributes](https://sdkdocs.roku.com/display/sdkdoc/Content+Meta-Data#ContentMeta-Data-PlaybackConfigurationAttributes)

**Streaming Feed Spec** - [Streaming Feed Specification - TrickPlayFile Definition]()
