# Pico 4 SteamVR via Steam Link VR (2026)

**Quick Note (2026 Update)**  
Valve now provides **Steam Link VR** for Pico 4 (and other Pico headsets). This allows you to **stream SteamVR games from your PC directly to your headset over Wi-Fi**, with minimal setup, bypassing manual ALVR installation.

> ⚠️ **Linux Support:** Currently experimental. Some users may encounter driver or stability issues. If you experience problems, refer back to the [original guide](./README.md) for manual streaming setup.

---

## Requirements

- Pico 4 headset with latest firmware;
- Steam installed on your PC with SteamVR;
- **SteamVR opted into the public beta**;
- Pico Store access to download **Steam Link VR** app;
- Stable Wi-Fi connection (preferably 5GHz).

---

## Quick Start

1. **Install Steam Link VR** on your Pico 4:  
   - Open the **Pico Store**;
   - Search for **Steam Link VR** and install it.

2. **Prepare your PC**:
   - Make sure Steam and SteamVR are running;
   - Enable **Remote Play** in Steam settings (`Steam > Settings > Remote Play`).

3. **Enable SteamVR Beta** *(Required)*:
   To ensure compatibility with Steam Link VR, opt into the **SteamVR public beta**:

   1. Open Steam and go to **Library > Tools**  
   2. Find **SteamVR**, right-click and select **Properties**  
   3. Go to the **Betas** tab  
   4. Choose **`public_beta - Public Beta`** from the dropdown  
   5. Close and restart SteamVR  

   ![SteamVR Beta Settings](main/resources/images/STEAMLINK-steamvr-beta-settings.png) 

4. **Connect your headset**:
   - Launch **Steam Link VR** on Pico;
   - Scan for your PC on the same network;
   - Pair and start streaming;

5. **Adjust settings if needed**:
   - Use the VR interface to select graphics/performance options;
   - If you encounter lag or stutter, try 5GHz Wi-Fi or wired connection for PC;

---

## Troubleshooting

- **No PC detected:** Ensure both PC and headset are on the same network, and Steam is running;
- **Performance issues:** Lower VR graphics settings or try a wired connection;
- **Linux specific issues:** Steam Link VR on Linux is still experimental. Some features may not work; consider fallback to manual ALVR setup from the [original guide](./README.md)

---

## References

- [Steam Link VR on Pico Store](https://www.pico-vr.com/us/store)  
- [Original ALVR guide](./README.md)  
- [GamingOnLinux report on Steam Link VR Linux support](https://www.gamingonlinux.com/2025/09/steam-link-vr-now-available-for-pico-and-htc-headsets-plus-valve-confirm-experimental-linux-support)

---

## Final Note

From personal experience using Steam Link VR with Pico 4:

- Occasional and sometimes frequent disconnections can occur;
- Sometimes the headset has difficulty starting the connection or pairing.

On the positive side:

- Visual quality, especially color reproduction, feels better than with manual streaming;
- Responsiveness and latency are generally improved;
- Ease of use is far superior to the ALVR/manual setup.

With some future improvements, this is likely **the best way to use Pico 4 on Linux** for most users.
