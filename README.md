# Pico 4, stream VR software on Linux [ WORK IN PROGRESS ]
#### _Guide to use Pico 4 headset on Linux, streaming VR software and games_
I wrote this guide to help me to remember all the steps to configure the software elements needed to use the Pico 4 headset with Linux (I use Debian).

The following are the software requirements and steps needed to install and configure the entire environment.
Further details on these topics, if needed, will be covered in the appropriate wiki pages [TODO].

## Software requirements
##### To install on your PC (Linux):
- [Steam](https://store.steampowered.com/about/download): is needed due to SteamVR;
- [SteamVR](https://www.steamvr.com/en/): is a free software available on the Steam platform. It will be used as the main VR environment on the PC, making it possible to launch and manage VR applications and games. It's required for the ALVR server;
- [ALVR Server](https://github.com/alvr-org/ALVR) is open source software, which is required for the ALXR client. At the time of writing, version [18.2.3](https://github.com/alvr-org/ALVR/releases/tag/v18.2.3) is required. Other versions are not compatible with the latest ALXR client app;
- [AudioRelay Server](https://audiorelay.net/downloads) is required for audio streaming on the device. This is because ALVR version 18.2.3 does not support audio streaming on Linux. Hopefully, in the next version of ALXL/ALVR it will no longer be necessary;
##### To install on your Pico 4:
- [ALXR Client](https://github.com/korejan/ALVR/wiki/ALXR-Client) is an open source application, the ALVR software client. You must use the ALXR client (and not the ALVR client) because Pico 4 "has" OpenXR runtimes.
- [AudioRelay Client app](https://audiorelay.net/downloads) is the client that connects to the AudioReleay server.

## Installation Steps
##### From your pc:
- [ ] Install Steam: here the official Debian Linux page to [install Steam](https://wiki.debian.org/Steam#Installing_Steam);
- [ ] Install SteamVR: simply open Steam, search for SteamVR in the store and install it;
- [ ] Install ALVR Server: download `alvr_server_linux_portable.tar.gz` (You can alternatively choose to install `alvr_server_linux.tar.gz`, but you need to install some additional libraries on your system. I recommend to use the `portable` version at first try, because it's surefire).
Extract the archive with the commands:
 `mkdir ~/alvr-server-portable`
 `tar -xvzf alvr_server_linux_portable.tar.gz -C ~/alvr-server-portable/`
 
- [ ] Configure ALVR Server: to configure ALVR, open your web browser and reach the page `localhost:8082` (this is handy because you can reach this page even from your VR headset, but in this case use the address `{your pc ip address}:8082`);
[TODO]
- [ ] Install AudioRelay Server: download latest release, then execute the commands:
```
sudo apt update
sudo apt upgrade -Y
sudo dpkg --install audiorelay*.deb
```
[TODO install libflac8]
 
- [ ] Configure AudioRelay Server: this software should be ready for use as is. But if needed, here is AudioRelay's official page for [advanced configs](https://docs.audiorelay.net/instructions/linux/stream-audio-from-your-linux-pc-to-your-phone);
##### From your Pico4:
Since the Pico 4 is an Android device, it is possible to install almost any Android app on the Pico 4. So:
- [ ] Install ALXR app: open the web browser on your Pico, then go to the page `https://github.com/korejan/ALXR-nightly/releases`.
Download and install `alxr-client-pico-v4.apk`;
- [ ] Install AudioRelay Client: the easiest way to install the AudioRelay client is to first install "Aurora Store" (alternative to Google Play Store), then search the AudioRelay store and install it through that.
Here a safe link to download Aurora Store from [F-Droid repository](https://f-droid.org/repo/com.aurora.store_41.apk).
Now, from Aurora Store, search for AudioRelay and install it.

## Run steps
To execute the entire environment:
##### On your pc:
- Launch ALVC Server:
```
~/alvr-server-portable/bin/alvr_launcher &
```
- Launch AudioRelay Server:
```
/opt/audiorelay/bin/AudioRelay &
```
##### On your Pico4:
- Open AudioRelay App, connect to your pc ip in the app list;
- Open ALXR client, for a few moments, you will see a "teal" background and two rgb cubes instead of controllers, but soon the SteamVR Home will appear.

## Addendum, optional features
- Streaming over USB: ...;
- Remote control your pc with SteamLink: ...;
- Startup script: ...;

## Troubleshooing [TODO]
