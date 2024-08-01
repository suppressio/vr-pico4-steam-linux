# Pico 4, stream VR software on Linux
#### _Guide to use Pico 4 headset on Linux, streaming VR software and games_
***Note:*** _This guide specifically covers using the ALVR software with the Pico 4 headset to stream SteamVR content from a Debian-based Linux system._

_All the installation procedures described are a balanced compromise between "manual" and guided processes. This is one of the methods to configure and use the software._

Below are the software requirements and steps needed to install and configure the entire environment.

## Software requirements
#### To install on your PC (Linux):
- [Steam](https://store.steampowered.com/about/download): Required for SteamVR;
- [SteamVR](https://www.steamvr.com/en/): Free software available on the Steam platform. It serves as the main VR environment on the PC, enabling the launch and management of VR applications and games. It's necessary for the ALVR server;
- [ALVR Streamer](https://github.com/alvr-org/ALVR): Open-source software that streams VR games from your PC. ALVR Streamer is the server part of this software. At the time of writing, the latest release is [20.9.1](https://github.com/alvr-org/ALVR/releases/tag/v20.9.1);
  
#### To install on your Pico 4:
- [ALVR Client](https://github.com/alvr-org/ALVR) The client counterpart of the ALVR software, available as an ".apk" file;


## Installation Steps
#### From your pc:
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

##### Configure ALVR Streamer (Server): 
- [ ] First run:
- On the first run, a wizard window will guide you through some system checks and choices. Click "Next" until the end. 
In my case, I received an "Unsupported OS" message at one step of the wizard (I ignored it).

![ALVR Wizard Welcome](/resources/images/ALVR-wizard-welcome.png)
![ALVR Wizard Unsupported OS](/resources/images/ALVR-wizard-unsupportedOS.png)

- [ ] Installation tab:
- Click "Register ALVR Driver".

![ALVR Wizard To Register Driver](/resources/images/ALVR-toRegister-driver.png)
![ALVR Wizard Registered Driver](/resources/images/ALVR-registered-driver.png)

- [ ] Settings tab, you can set:
Video:
- Preferred framerate: 90Hz;
- Resolution: I selected "Ultra";

![ALVR Video Settings](/resources/images/ALVR-video-settings.png)

- [ ] Connection tab:
- Stream protocol: TCP (I got frequent disconnections if not set);

![ALVR Connection Settings](/resources/images/ALVR-connection-settings.png)

- [ ] Click "Launch SteamVR"...

##### 💩 happens: re-activate SteamVR addons: 
- [ ] Check for Disabled Add-ons: At this stage, SteamVR might start with the add-ons disabled (including the ALVR add-on). Re-enable the add-ons by pressing "Manage Add-ons", then set "alvr_server" to "On". Press "Restart SteamVR".

![SteamVR Blocked Addons](/resources/images/steamVR-blocked-addons.png)
![SteamVR Unlock Addons](/resources/images/steamVR-unlock-addons.png)

The add-ons are correctly enabled if there are no indications of blocked add-ons on the button.

![SteamVR Enabled Addons](/resources/images/steamVR-correct_addons.png)

ALVR Streamer is now ready and waiting for a client to connect.

##### From your Pico4:
Since the Pico 4 is an Android device, you can install almost any Android app on it. So:
- [ ] Install ALVR client app:

Open the web browser on your Pico, then go to the page `https://github.com/alvr-org/ALVR/releases/tag/v20.9.1`.

- Download `alvr_client_android.apk`;

![PICO4 ALVR apk Download](/resources/images/PICO-apk-download.jpg)

**PLEASE NOTE! Use the same ALVR Client version as the installed ALVR Streamer.**

- Once downloaded, click on Open to install `alvr_client_android.apk`;

![PICO4 ALVR apk Download](/resources/images/PICO-apk-downloaded.jpg)

![PICO4 ALVR apk Install](/resources/images/PICO-apk-install-confirm.jpg)

- [ ] First ALVR Client run:

**PLEASE NOTE! Ensure your Pico 4 is connected to the same Wi-Fi network as your PC (they should be on the same subnet). A good 5GHz Wi-Fi connection is recommended**

- Open the "Library" on your Pico 4, select "Unknown" from the left menu, and run the ALVR Client;

![PICO4 ALVR apk Install](/resources/images/PICO-run-ALVR.jpg)

Once inside, get back to you PC to continue...

![PICO4 ALVR Client Searching for streamer](/resources/images/PICO-ALVRclient-searching.jpg)

##### Back to your PC:

- [ ] Trust a new device:

- On the "Devices" tab of ALVR Streamer, you should now see a new device to be trusted;

![ALVR Streamer To Trust Device](/resources/images/ALVR-toTrust-device.png)

![ALVR Streamer Trusted Device](/resources/images/ALVR-trusted-device.png)

##### Back to your Pico4 again:

If your Pico 4 displays only `The streamer will begin soon    Please wait...` for too long (more than 10/20 seconds), it might be necessary to close the ALVR Client and reopen it if the connection is not established.

![ALVR Streamer Waiting](/resources/images/PICO-ALVRclient-waiting.jpg)

Now... You are finally inside the SteamVR Home Environment! 🎉

![SteamVR Home](/resources/images/SteamVR-finally-inside.jpg)


## Addendum, optional features
- [Streaming over USB](ALVR-USB-Streaming.md);


## Troubleshooting 
- Black Screen: I faced a black screen issue from the ALVR Client running on my Pico for months due to a problem with SteamVR. The solution is to add a parameter to SteamVR "Launch Options":
> Add ~/.local/share/Steam/steamapps/common/SteamVR/bin/vrmonitor.sh %command% to the commandline options of SteamVR (SteamVR -> Manage/Right Click -> Properties -> General -> Launch Options).
> This path might differ based on your Steam installation, in that case SteamVR will not start at all. If this is the case you can figure out the actual path by going to Steam Settings -> Storage. Then pick the storage location with the star emoji (⭐) and take the path directly above the usage statistics. Prepend this path to steamapps/common/SteamVR/bin/vrmonitor.sh. Finally put this entire path into the SteamVR commandline options instead of the other one.
[source](https://github.com/alvr-org/ALVR/wiki/Linux-Troubleshooting#black-screen-even-when-steamvr-shows-movement).

- Other Possible Issues: Refer to the [ALVR Linux Troubleshooting page](https://github.com/alvr-org/ALVR/wiki/Linux-Troubleshooting#black-screen-even-when-steamvr-shows-movement);
