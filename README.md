# Installation of Raspberry Pi 4 - 64 bit - Server

## Prequisities

- We want a 64 bit OS to obtain speed from the RPI 4 hardware.
- We also want a desktop/GUI version, to utilize GUI if necessary (yes, it will carry additional load/storage).
- We do not want WIFI enabled as we will utilize fixed cabling.
- Preferably, use a RPI 4 with 8GB RAM.

## Installation

1. Download the right 64 bit image from [Raspberry downloads](https://downloads.raspberrypi.org/raspios_arm64)
2. Format SD Card. Can be done with [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/)
3. Download and run [Raspberry PI Imager](https://www.raspberrypi.com/software/)
4. Choose the downloaded image and the SD-Card.
5. Open advanced options with CTRL + SHIFT + X:
   - Enable `Set hostname` and set name of the server.
   - Enable `Enable SSH` and set a password for user 'pi'.
   - Set `Locale settings` and time zone to 'Europe/Stockholm'.
   - Leave `Keyboard layout` as 'us'.
   - Enabled `Skip first run wizard`.
   - Disable `Enable telemetry`.
6. Enter SD Card into RPI.
7. Boot the device on the network, wait 10 minutes (how long time is really needed?).
8. From the router, set fixed IP on the server.
   - Possibly a new reboot is required.
9. Login through SSH with Putty and user 'pi', and the password set above.
   - Update config with: `sudo raspi-config`.
     - Set the following config:
       - `System Options` -> `Boot/Auto Login` to 'Desktop'.
       - `Display Options` -> `VNC Resolution` to '1280x720'.
       - `Interface Options` -> `VNC` to Enabled-Yes.
       - `Localisation Options` -> `Locale` to 'en_GB.UTG-8 UTF 8' (if not already set).
       - `Advanced Options` -> `Boot Order` to 'USB Boot' (Boot from USB if available, otherwise boot from SD Card).
         - As we may want to boot from SSD disk later.
     - Save and leave program without reboot.
10. Update RPI and reboot with:
    ```shell
    sudo apt update
    sudo apt full-upgrade
    sudo shutdown -r now
    ```
11. After reboot, login with ssh and verify that bootloader is updated with:
    ```shell
    sudo rpi-eeprom-update
    ```
    If not correct, update with `sudo raspi-config` and `Advanced options` -> `Bootloader version` -> `Latest` -> `Yes`. Reboot thereafter and run `sudo rpi-eeprom-update` again to verify.
12. Login with VNC to continue config:
    - Disable Bluetooth by clicking the bluetooth-symbol at the upper right corner.
13. Fine tune the installation with.
    - To get network tools, install dns-utils with `sudo apt install dnsutils`.
    - To get telnet-client (not the daemon), install with `sudo apt install telnet`.
14. Reboot.

## Install docker

1. Login and run the the following commands:
   - `sudo apt install docker`.
   - `sudo apt install docker-compose`.
   - `sudo usermod -aG docker pi`.
   - `sudo systemctl enable docker` (to ensure that the docker service is enabled to start at boot).
2. Create the directory `/srv` if not already created.
   - Utilize `/srv` as directory to mount volumes in docker.
