# Installation of Raspberry Pi 4 - 64 bit - Server

We want a 64 bit OS to obtain speed from the RPI 4 hardware.\
We also want a desktop/GUI version, to utilize GUI if necessary (yes, it will carry additional load/storage).\
We do not want WIFI enabled as we will utilize fixed cabling.

1. Download the right image from [Raspberry downloads](https://downloads.raspberrypi.org/raspios_arm64)
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
6. Enter SD Card into RPI 4.
7. Boot the device on the network, wait 10 minutes (how long time is really needed?).
8. From the router, set fixed IP on the server.
   - Possibly a new reboot is required.
9. Login through SSH with Putty and user 'pi', and the password set above.
   - Update config with: `sudo raspi-config`
     - Set the following config:
       - `Localisation Options` -> `Locale` to 'en_GB.UTG-8 UTF 8' (if not already set).
       - `Advanced Options` -> `Boot Order` to 'USB Boot' (Boot from USB if available, otherwise boot from SD Card).
     - Save and leave program without reboot.
   - Run `sudo raspi-config`
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
12. Install xrdp to easily get remote desktop with:
    ```shell
    sudo apt-get install xrdp
    ```
