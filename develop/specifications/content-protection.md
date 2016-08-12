# Content Protection
_informational reference for the DRM formats and the HDCP versions supported on the Roku Platform_

**Sections:**

* [DRM](#drm)
* [Copy Protection](#copy-protection)

## DRM

Although AES-128 Encryption is also supported for HLS, Roku recommends using Adobe DRM because there is no DRM when using AES-128 Encryption.

|        | PlayReady | Adobe DRM | AES-128 |
| ------ | :-------: | :-------: | :-----: |
| HLS    || :heavy_check_mark: | :heavy_check_mark: |
| Smooth | :heavy_check_mark: |           |         |
| DASH   | :heavy_check_mark: |           |         ||

> :information_source: To use Adobe DRM with HLS streams, a channel must include the `requires_aaxs_drm` entry in the manifest file. See [manifest](/develop/specifications/manifest.md) for details.

## Copy Protection

Roku's OS also supports HDCP for content copy protection between the Roku player's HDMI port and the connected display; however, the version of HDCP depends on the Roku Models in the table below.

|      | Roku 4K capable devices | All other Roku devices |
| ---- | :---------------------: | :--------------------: |
| TEE  | Yes | No
| HDCP | 2.2 | 1.4
