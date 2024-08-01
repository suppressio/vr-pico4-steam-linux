# Pico 4, stream VR software on Linux
#### _Guide to use Pico 4 headset on Linux, streaming VR software and games_
This guide outlines all the steps to configure the software elements necessary for using the Pico 4 headset with Linux (specifically Debian derivates).

Below are the software requirements and steps needed to install and configure the entire environment.

## Software requirements
##### To install on your PC (Linux):
- [Steam](https://store.steampowered.com/about/download): Required for SteamVR;
- [SteamVR](https://www.steamvr.com/en/): Free software available on the Steam platform. It serves as the main VR environment on the PC, enabling the launch and management of VR applications and games. It's necessary for the ALVR server.;
- [ALVR Streamer](https://github.com/alvr-org/ALVR): Open-source software that streams VR games from your PC. ALVR Streamer is the server part of this software. At the time of writing, the latest release is [20.9.1](https://github.com/alvr-org/ALVR/releases/tag/v20.9.1);

  
##### To install on your Pico 4:
- [ALVR Client](https://github.com/korejan/ALVR/wiki/ALXR-Client) The client counterpart of the ALVR software;

## Installation Steps
##### From your pc:
- [ ] Install Steam: Follow the official Debian Linux page to [install Steam](https://wiki.debian.org/Steam#Installing_Steam);
- [ ] Install SteamVR: Open Steam, search for SteamVR in the store, and install it;
- [ ] Install ALVR Streamer: Download `alvr_streamer_linux.tar.gz`. Extract the archive with the commands:
```console
mkdir ~/alvr_streamer
tar -xvzf alvr_streamer_linux.tar.gz -C ~/alvr_streamer/
```

- [ ] Run ALVR Streamer: In the extracted directory, navigate to the `bin` directory, then run `alvr_dashboard`:
```console
cd ~/alvr_streamer/bin
./alvr_dashboard
```
 
- [ ] Configure ALVR Server: 
On the first run, a wizard window will guide you through some system checks and choices. Click "Next" until the end.
In my case, I received an "Unsupported OS" message at one step of the wizard (I ignored it).

Click on "Installation", then click "Register ALVR Driver".

In Settings, you can set:
Video:
- Preferred framerate: 90Hz;
- Resolution: I selected "Ultra";
Connection:
- Stream protocol: TCP (I got frequent disconnections if not set);


##### From your Pico4:
Since the Pico 4 is an Android device, you can install almost any Android app on it. So:
- [ ] Install ALVR client app: Open the web browser on your Pico, then go to the page `https://github.com/alvr-org/ALVR/releases/tag/v20.9.1`.
Download and install `alvr_client_android.apk`;


## Addendum, optional features
- Streaming over USB: ... [TODO];

## Troubleshooting 
- Black Screen: I faced a black screen issue from the ALVR Client running on my Pico for months due to a problem with SteamVR. The solution is to add a parameter to SteamVR "Launch Options":
> Add ~/.local/share/Steam/steamapps/common/SteamVR/bin/vrmonitor.sh %command% to the commandline options of SteamVR (SteamVR -> Manage/Right Click -> Properties -> General -> Launch Options).
> This path might differ based on your Steam installation, in that case SteamVR will not start at all. If this is the case you can figure out the actual path by going to Steam Settings -> Storage. Then pick the storage location with the star emoji (⭐) and take the path directly above the usage statistics. Prepend this path to steamapps/common/SteamVR/bin/vrmonitor.sh. Finally put this entire path into the SteamVR commandline options instead of the other one.
[source](https://github.com/alvr-org/ALVR/wiki/Linux-Troubleshooting#black-screen-even-when-steamvr-shows-movement).

- Other Possible Issues: Refer to the [ALVR Linux Troubleshooting page](https://github.com/alvr-org/ALVR/wiki/Linux-Troubleshooting#black-screen-even-when-steamvr-shows-movement);
