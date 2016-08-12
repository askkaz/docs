
# Audio/Video Encoding Overview
_supported audio and video formats on Roku devices_

### Overview
It is important to understand the available encoding methods and supported formats when streaming content on Roku devices. The following information will give you a good basis and help you choose the best options for distributing content based on quality and availability.

Roku **officially** supports the following media formats:

* Video file types: `MP4`, `MOV`, `M4V`, `MKV`, `WebM`
* Video codecs: `H.264/AVC`, `HEVC/H.265`, `VP9`
* Audio file types: `AAC`, `MP3`, `WMA`, `WAV (PCM)`, `AIFF`, `FLAC`, `ALAC`, `AC3`, `EAC3`
* Streaming protocols: `HLS`, `Smooth`, `DASH`

These have been tested and/or are currently in-use. Other formats or encodings may be supported, but should be evaluated on a case by case basis.

**Sections:**

* [Streaming Protocols](#streaming-protocols)
* [Live Streaming / Live Video](#live-streaming--live-video)
* [Supported Video Formats](#supported-video-formats)
 * [Device Specific Features](#device-specific-features)
* [Supported Audio Formats](#supported-audio-formats)
* [Best Practices](#best-practices)
 * [4K UHD Video Streaming Recommendations](#4k-uhd-video-streaming-recommendations)

---

## Streaming Protocols
Because network speeds can vary over time, a crucial aspect when providing the best experience to your viewers is providing multiple video streams of varying quality. Roku devices can then automatically select the best streaming quality based on the viewer's network connection.

Roku supports the following widely-used standard formats for adaptive bit rate switching:

* HLS (HTTP Live Streaming)
* Smooth Streaming
* DASH (Dynamic Adaptive Streaming over HTTP)

## Live Streaming / Live Video
Roku supports live video streaming in the following formats:

* HLS
* Smooth Streaming

## Supported Video Formats
Roku devices support the following file types:

* MP4
* MOV
* M4V
* MKV
* WebM<sup>1</sup>

Videos can be encoded using `H.264`, `HEVC (H.265)`, or `VP9` codecs.

|                          | H.264   | HEVC (H.265)<sup>1</sup> | VP9<sup>1</sup> |
| ------------------------ | ------- | ------------------------ | --------------- |
| Aspect Ratio<sup>2</sup> | Various | Various                  | Various
| Dimension | Various up to 1920x1080 | Various up to 3840x2160 | Various up to 3840x2160
| Video File Format | `.mp4`, `.mov`, `.m4v`, `.mkv` | `.mp4`, `.mov`, `.m4v`, `.mkv` | `.webm`, `.mkv`
| Streaming Format | HLS: `.m3u8`, `.ts` <br> Smooth: `.ismc` <br> DASH: `.dash` | HLS: `.m3u8`, `.ts` <br> Smooth: `.ismc` <br> DASH: `.dash` | DASH: `.dash`
| Input Frame Rate <sup>3</sup> | 24p, 30p, 60p | 24p, 30p, 60p | 24p, 30p
| Color Space | YUV | YUV and YUV 10-bit | YUV
| Profile | Main/High | Main 10 | Profile 0
| Level/Complexity | 4.0 | 5.1 | 5
| Video Mode | Constrained VBR | Constrained VBR | Constrained VBR
| Average Streaming Video Bit rate | Up to 10Mbps | Up to 40Mbps | Up to 40Mbps
| Average USB Video Bit rate | 384Kbps – 10Mbps | Up to 40Mbps | Up to 40Mbps
| Peak Video Bit rate | 1.5x average | 1.5x average | 1.5x average
| Key Frame Interval <sup>4</sup> | < 10s | < 10s | < 10s
| DRM | PlayReady for Smooth/DASH <br><br> Streaming AES-128 bit encryption for HLS | PlayReady for Smooth/DASH <br><br> Streaming AES-128 bit encryption for HLS | PlayReady for DASH <br><br> Widevine Level 1

### Device Specific Features

|         | Roku 4K capable devices | All other Roku devices |
| ------- | :---------------------: | :--------------------: |
| TEE<sup>5</sup> | Yes | No
| HDCP | 2.2 | 1.4

> <sup>1</sup> Only supported on **Roku 4K capable** devices.

> <sup>2</sup> The dimensions vary on a title-by-title basis depending on the source material and the target aspect ratio for the encoding (such as 4:3 or 16:9).  Content should always be encoded at full width, and the height is adjusted. For example, a 1.66 aspect ratio source is encoded as a 720x432 video and displayed as letterboxed for a 4:3 display.

> <sup>3</sup> The frame rate used for encoding depends on the source material. Film content is generally 23.976 FPS, while video content is generally at 29.97.

> <sup>4</sup> All segments should start with an IDR frame and align across all bit rate variants. The recommended segment size is < 10 seconds for VOD and < 5 seconds for live content, and the segment size should be constant.

> <sup>5</sup> Trusted Execution Environment

## Supported Audio Formats

Roku devices support the following audio file types:

* AAC: HE-AACv2, AAC-LC (CBR)
* MP3
* WMA, WAV (PCM)
* AIFF
* FLAC
* ALAC
* Passthrough: Dolby Digital (AC3), Dolby Digital Plus (EAC3), DTS

|                    | AAC<sup>1</sup> | AC3/EAC3<sup>2</sup> | DTS |
| ------------------ | --------------- | -------------------- | --- |
| Decode/Passthrough | Decode | Passthrough | Passthrough
| Sampling Rate      | 44.1 Khz, 48 Khz | As supported by sink device | As supported by sink device
| Sample Size        | 16-bit | As supported by sink device | As supported by sink device
| Bit rate           | 32-256 Kbps | As supported by sink device | As supported by sink device
| Number of Channels | 2.0 | As supported by sink device | As supported by sink device

> <sup>1</sup> Multichannel AAC is not supported on all Roku models. Roku TV’s and Roku 4 set-top-boxes support multichannel decode to PCM stereo.

> <sup>2</sup> Roku TVs can decode AC3 and EAC3 to PCM stereo.

## Best Practices

For typical streaming video applications, we recommend a range of about 800Kbps to about 4.0Mbps. For USB playback, we recommend that you stay under 8.0 Mbps. This provides a good balance between quality and support for a wide number of users. In some cases, lower and higher bit rates have been used, but this frequently results in a bad quality, or limits the numbers of users that can view those encodings.

Lowest and Highest bit rates:

* Roku recommends encoding a low bit rate stream around 800Kbps.
* Roku recommends the user have at least a 1.5Mbps connection.
* Some customers will have low bit rate connections around 1Mbps or experience intermittent network load that causes drops below Roku recommended network speeds.

### 4K UHD Video Streaming Recommendations

The following are recommendations for streaming 2160p video content (available on Roku 4 and Roku 4K TV devices).

**Supported Profiles:**
* ISO Base Media File Format and VOD only.

**Signaling:**
* `DASH` is the preferred adaptive streaming format with `HEVC` as the preferred video codec.
* The recommended bit rates are 8, 10, 15, and 20Mbps.
* All recommended bit rates should be in the same `DASH` stream.
* Supported audio formats include `AAC`, `AC3`, and `EAC3`.
* AAC 2-channel stereo should be provided as an alternate audio track to surround sound.

**Segment Size and Alignment:**
* All encoded segments must start with an IDR frame.
* The recommended adaptive streaming segment sizes are 2.5, 3.3, or 5 seconds.
* The segment sizes should be constant and the same for all bit rates for the best adaptive switching and trick play (with 10 second BIF files).

**Encryption:**
* Only PlayReady encryption is supported.
