# Roku Channel Manifest

### Overview
The root level of all Roku Channels must contain a `manifest` file containing important attributes for the application. These attributes include the name and version number of the application, the channel icon, splash screen image, etc.

**Sections:**
* [Manifest Guidelines](#manifest-guidelines)
* [Required Attributes](#required-attributes)
* [Optional Attributes](#optional-attributes)
  * [Splash Screen Attributes](#splash-screen-attributes)
  * [Graphics Scaling Attributes](#graphics-scaling-attributes)
  * [Launch Requirement Attributes](#launch-requirement-attributes)
  * [DRM Attributes](#drm-attributes)
  * [Special Purpose Attributes](#special-purpose-attributes)
* [Screensaver Attributes](#screensaver-attributes)
  * [Required Screensaver Attributes](#required-screensaver-attributes)
  * [Optional Screensaver Attributes](#optional-screensaver-attributes)
* [Legacy Attributes (Deprecated)](#legacy-attributes-deprecated)

---

## Manifest Guidelines

* Each attribute is on a separate line, and has the form `name=value`
* Each `name=value` pair must end with a newline character, or it may not be parsed by the firmware
* The last line must end with a newline character
* Empty lines are ignored
* Lines beginning with a '#' (number sign) are comment lines and are ignored
* All graphics files specified in the manifest file should be included in the `images` directory.
* The URI to set the path to the files should use the `pkg:` resource prefix, such as `pkg:/images/splash-screen.png`.

## Required Attributes
These are the minimum attributes required for every Roku channel:

| Attribute | Type   | Description | Sample manifest entry | Specification |
| --------- | ------ | ----------- | --------------------- | ------------- |
| `title`   | string | name of the channel | `title="Roku Media Player"` ||
| `major_version` | integer | major portion of channel version | `major_version=1` ||
| `minor_version` | integer | minor portion of channel version | `minor_version=2` ||
| `build_version` | integer | build number | `build_version=150` ||
| `mm_icon_focus_hd` | string | local URI for the channel icon | `mm_icon_focus_hd=pkg:/images/channel-icon.png` | 540x405
| `splash_screen_fhd` | string | local URI for the splash screen displayed when the channel is launched | `splash_screen_fhd=pkg:/images/splash-screen.png` | 1920x1080

## Optional Attributes
The following categories of attributes are optional:

### Splash Screen Attributes
| Attribute | Type   | Description | Sample manifest entry | Specification |
| --------- | ------ | ----------- | --------------------- | ------------- |
| `splash_color` | hex value | background color to use if the splash screen image is not full screen | `splash_color=#121212`
| `splash_min_time`<sup>1</sup> | integer | minimum amount of time (in milliseconds) to display the splash screen | `splash_min_time=1500`
| `splash_screen_hd`<sup>2</sup> | string | local URI for the HD splash screen | `splash_screen_fhd=pkg:/images/splash-screen.png` | 1280x720
| `splash_screen_sd`<sup>2</sup> | string | local URI for the SD splash screen | `splash_screen_fhd=pkg:/images/splash-screen.png` | 720x480

> <sup>1</sup> If no value is specified, then 1600 (1.6 seconds) is used. If 0 is specified, then there is no default time, so the splash screen disappears as soon as the application displays its first screen.   (This may result in the appearance of flashing, if your application shows its first screen quickly).

> <sup>2</sup> The FHD splash screen image is scaled down for HD and SD display modes but this attribute can be used to specify a resolution-specific splash screen image.

### Graphics Scaling Attributes

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `ui_resolutions`<sup>1</sup> | comma separated values | A comma-separated list of up to three strings that identify the UI resolutions the application has been designed to support. | `ui_resolutions=sd,hd,fhd`
| `uri_resolution_autosub`<sup>2</sup> | comma separated values | Provides a flexible way to specify graphical image URIs that are automatically modified to replace a specified string with a string that gets a resolution-specific graphical image. | `uri_resolution_autosub=$$RES$$,SD,720p,1080p`

> <sup>1</sup> The default value is `sd,hd`. <br>`sd`	Applications designed for standard definition 720x480 <br> `hd` Applications designed for high definition 1280x720 <br> `fhd` Applications designed for full high definition 1920x1080

> <sup>2</sup> The attribute value is a comma-separated list of four strings that specify the string to be replaced along with the replacement strings for SD, HD and FHD resolutions. <br><br>For example, suppose the manifest includes this line: uri_resolution_autosub=$$RES$$,SD,720p,1080p And the Roku player supports full high-definition resolution. <br><br>Then if the application specifies a URI of: http://www.roku.com/testChannel/assets/$$RES$$/rokuTV.jpg At runtime that URI will be modified to: http://www.roku.com/testChannel/assets/1080p/rokuTV.jpg and the application will get the full-high definition version of the graphical image in the specified directory.

### Launch Requirement Attributes

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `requires_audiometadata` | integer | The roAudioMetadata component requires the use of a dynamically loaded library that is not part of the initially booted image. Therefore, an entry must be added to the manifest of any applications that use the roAudioMetadata component so that it can be loaded when the channel is launched | `requires_audiometadata=1`
| `requires_gaming_remote` | integer | Specifies that a gaming remote must be linked to the Roku Player to launch the application. If not, a dialog box is presented to the user. |	`requires_gaming_remote=1`
| `requires_mkv` | integer | Playing MKV files requires the use of a dynamically loaded library that is not part of the initially booted image. Therefore, an entry must be added to the manifest of any applications that require MKV support so that support is enabled when the channel is launched. | `requires_mkv=1`
| `network_not_required` | integer	| Set to 1 to specify the application does not require the network (such as the USB Media Player). This lets the user launch an application even if there is no network connection.	| `network_not_required=1`
| `bs_libs_required`	| string | Specifies the BrightScript libraries required for the application. | `bs_libs_required=roku_ads_lib`
| `requires_flite_tts` | integer | Text to speech requires loading of the current flite_tts library (for platforms where the library is not built in). | `requires_flite_tts=1`
| `requires_flite_version`	| value | Version number of the current text to speech flite_tts library (currently 2.0.0).	| `requires_flite_version=2.0.0`

### DRM Attributes

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `requires_aaxs_drm` | integer | Specifies that Adobe DRM is to be used with HLS streams. Use this if your HLS streams are protected with Adobe aaxs DRM. | `requires_aaxs_drm=1`
| `requires_aaxs_version` | value | Specifies the version of aaxs to use. Currently Roku only supports version 1.0 | `requires_aaxs_version=1.0`

### Special Purpose Attributes

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `hidden`    | integer | The hidden property tells the firmware to not display the app on the home screen. Hidden apps can still be launched over the network via the External Control API. | `hidden=1`
| `playonly_aware` | integer | Attribute to specify the application responds to the Play Only remote control button event. If not set, the application will receive the Play event instead when the user selects the button. | `playonly_aware=1`

## Screensaver Attributes

For an overview and guide on screensavers, see [Screensavers on Roku](/develop/guides/screensavers.md).

### Required Screensaver Attributes

For [stand-alone screensavers](/develop/guides/screensavers.md#types-of-screensavers), only the following attributes are required:

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `screensaver_title`   | string | name of the screensaver displayed in Settings | `screensaver_title="Dog Screensaver"`
| `major_version` | integer | major portion of screensaver version | `major_version=1`
| `minor_version` | integer | minor portion of screensaver version | `minor_version=2`
| `build_version` | integer | build number | `build_version=150`

### Optional Screensaver Attributes

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `screensaver_private` | integer | Attribute to specify if the screensaver will only run within a channel. | `screensaver_private=1`

## Legacy Attributes (Deprecated)

The following attributes are no longer required or used by Roku devices:

| Attribute | Type   | Description | Sample manifest entry |
| --------- | ------ | ----------- | --------------------- |
| `subtitle`  | string | Short promotional description of your application for display beneath the title | `subtitle="providing the latest in cool videos"`
| `mm_icon_side_hd` | string | local URI for side unfocused image for HD | `mm_icon_side_hd=pkg:/images/side-hd.png`
| `mm_icon_side_sd` | string | local URI for side unfocused image for SD | `mm_icon_side_sd=pkg:/images/side-sd.png`
| `mm_icon_focus_sd` | string | Local URI for the channel poster image for SD | `mm_icon_focus_sd=pkg:/images/focus-sd.png`
| `requires_bluetooth` | integer | Specifies that a Bluetooth remote must be linked to the box to launch the app. If not, a dialog box is presented to the user. This attribute has been superseded by `requires_gaming_remote`.	 | `requires_bluetooth=1`
