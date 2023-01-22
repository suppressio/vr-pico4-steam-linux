# Pico 4, stream VR software on Linux
#### _Guide to use Pico 4 headset on Linux, streaming vr software and games_
This guide was created to help me to remember all the steps to configure the software elements needed to use the Pico 4 headset with Linux.

The following are the software requirements and steps needed to install and configure the entire environment.
Further details on these topics, if needed, will be covered in the appropriate wiki pages.

## Software requirements
##### To install on your PC (Linux):
- [Steam](https://store.steampowered.com/about/download): is needed due to SteamVR;
- [SteamVR](https://www.steamvr.com/en/): will be used as the main VR environment, enabling the launch and management of VR applications and games on your PC. It is required for the ALVR server;
- [ALVR Server](https://github.com/alvr-org/ALVR) is open source software, which is required for the ALXR client. At the time of writing, version [18.2.3](https://github.com/alvr-org/ALVR/releases/tag/v18.2.3) is required. Other versions are not compatible with the latest ALXR client app;
- [AudioRelay Server](https://audiorelay.net/downloads) is required for audio streaming on the device. This is because ALVR version 18.2.3 does not support audio streaming on Linux. Hopefully, in the next version of ALXL/ALVR it will no longer be necessary;
##### To install on your Pico 4:
- [ALXR Client](https://github.com/korejan/ALVR/wiki/ALXR-Client) is an open source application, the ALVR software client. You must use the ALXR client (and not the ALVR client) because Pico 4 "has" OpenXR runtimes.
- [AudioRelay Client app](https://audiorelay.net/downloads) is the client that connects to the AudioReleay server.

## Steps
##### On your pc:
- [ ] Install Steam: ...;
- [ ] Install SteamVR: ...;
- [ ] Install ALVR Server: ...;
- [ ] Configure ALVR Server: ...;
- [ ] Install AudioRelay Server: ...;
##### On your Pico4:
- [ ] Install ALXR app: ...;
- [ ] Install AudioRelay Client: ...;

## Addendum, optional features
- Streaming over USB: ...;
- Remote control your pc with SteamLink: ...;
- Startup script: ...;
