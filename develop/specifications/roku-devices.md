## Overview
Roku provides the leading Operating System for TV. We design the firmware and cloud services to run optimally across a wide range of Televisions. When developing on Roku OS, it's important for your channels to perform across our wide range of products.

- - - -

### Roku's wide range of devices
The Roku OS runs across a spectrum of hardware. The main form factors are:

* **Roku Players:** The original form factor for Roku devices, these are connected devices that stream video also known as Over-the-top transmission (OTT)
* **Roku Streaming Sticks:** A subset of players, these are smaller HDMI devices that directlt plug into TVs
* **Roku Powered:** Devices licensed to Pay-TV operators. Typically are variants or exact versions of our Roku Players.
* **Roku TVs:** Licensed Roku OS to an array of Television manufacturers using our hardware reference designs

 

### Development Tip: Create your device testing bank
Developers building channels need to be test across multiple devices prior to submitting for publication in the Roku Channel Store. 

We strongly suggest you have a few devices that represent the different "families" of devices - which we refer to as Code names. For example, **Giga** is the family of Roku LT, Roku 2 HD, etc that have a similar processor, RAM, and tech specifications.
![Roku devices](https://roku-developer-home-ghost-staging.s3.amazonaws.com/2016/Jul/cm9rdV9kZXZpY2VzLTE0NjkxMjk4NTMzMzA=.png)
_Caption: The following visual shows a sample of the various Roku devices out in the market._

### Device chart
The following table lists our devices over time - including Roku players, streaming sticks, and TVs. Our Marketing names for hardware are re-used over time (Roku 1, 2, 3 etc) so you will want to ensure you understand which device you have. 

**Note:** All the 'Supported' devices indicate that Roku OS 7 or above runs and will be tested in channel certification.

<table>
<thead><tr><th>Roku Device Type</th><th>Model #</th><th>Marketing Name</th><th>Code Name</th><th>Status</th><th>&nbsp;</th><th>&nbsp;</th><th>&nbsp;</th></tr></thead><tbody>
 <tr><td>Roku Player</td><td>N1000</td><td>Roku HD</td><td>Griffin</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>N1050</td><td>Roku SD</td><td>Redwood</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>N1101</td><td>Roku HD</td><td>Redwood</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>N1100</td><td>Roku HD-XR</td><td>Redwood</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2000C</td><td>Roku HD</td><td>Pico</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2050X</td><td>Roku XD</td><td>Pico</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2100X</td><td>Roku XD|S</td><td>Pico</td><td>Legacy</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2400X/EU</td><td>Roku LT</td><td>Giga</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>3000X</td><td>Roku 2 HD</td><td>Giga</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>3050X</td><td>Roku 2 XD</td><td>Giga</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>3100X/EU</td><td>Roku 2 XS</td><td>Giga</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2450X</td><td>Roku LT</td><td>Paolo</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2500X</td><td>Roku HD</td><td>Paolo</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2700X/EU</td><td>Roku LT</td><td>Tyler</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2710X/EU</td><td>Roku 1</td><td>Tyler</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>2720X/EU</td><td>Roku 2</td><td>Tyler</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>4200X/EU</td><td>Roku 3</td><td>Austin</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>4210X</td><td>Roku 2 (US)</td><td>Mustang</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>4230X</td><td>Roku 3 (US)</td><td>Mustang</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku Player</td><td>4400X</td><td>Roku 4</td><td>Dallas</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Streaming Stick</td><td>3400X</td><td>Roku Streaming Stick</td><td>Jackson</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Streaming Stick</td><td>3500X/EU</td><td>Roku Streaming Stick</td><td>Sugarland</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Streaming Stick</td><td>3600X</td><td>Roku Streaming Stick</td><td>Briscoe</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku TV</td><td>5XXXX</td><td>Roku TV</td><td>Liberty</td><td>Supported</td><td>&nbsp;</td><td>&nbsp;</td><td>&nbsp;</td></tr>
 <tr><td>Roku TV</td><td>6XXXX</td><td>Roku 4</td><td>Fort Worth</td><td>Supported</td></tbody></table>