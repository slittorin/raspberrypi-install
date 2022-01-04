# Installation of Raspberry Pi 4 - 64 bit.

We want a 64 bit OS to obtain speed from the RPI 4 hardware.
We do not want WIFI enabled at first.

1. Download the right image from [Raspberry downloads](https://downloads.raspberrypi.org/raspios_arm64)
2. Format SD Card. Can be done with [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/)
3. Download and run [Raspberry PI Imager](https://www.raspberrypi.com/software/)
4. Choose the downloaded image and the SD-Card.
5. Open advanced options with CTRL + SHIFT + X:
   - Enable `Set hostname` and set name of the server.
   - Enable `Enabled SSH` and set a password for user 'pi'.
   - Set `Locale settings` and time zone to 'Europe/Stockholm'.
   - Leave `Keyboard layout` as 'us'.
   - Enabled `Skip first run wizard`.
   - Disable `Enable telemetry`.
6. xxx


sudo raspi-config
