# Installation of Raspberry Pi 4 - 64 bit.

We want a 64 bit OS to obtain speed from the RPI 4 hardware.
We do not want WIFI enabled at first.

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
7. Boot the device on the network and set fixed IP to the device.
8. Login through SSH (X11?) with Putty and user 'pi', and the password set above, utilize XXX to get remote desktop.
9. XXX
10. XXX


sudo raspi-config
