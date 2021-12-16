---
title: Instructions for Programming the Wireless RF Devices
keywords: construction, under construction
last_updated: Dec 15, 2021
tags:
summary: "This page is under construction - stay tuned for updates"
sidebar: mydoc_sidebar
permalink: programming_rf_devices.html
folder: mydoc
---

To update an RF device (sensor, IOT Gateway or Flex IO) requires connecting the device as to a computer as shown in [Hardware & Firmware](hardware_and_firmware.html).
Once complete you will need a ccti-programmer applicaition.<br />
Download [ccti-prog zip](../apps/ccti-prog.zip) for the Windows app ccti-prog.exe.

If you want to use a Raspberry Pi the source for the ccti-prog is included in the zip file with a Makefile.

To compile your own, copy the source to your RPi, then
```
make
gcc -o ccti-prog -Wall ccti-prog.c hex.c
```
Make sure an RF Gateway is attached to the Pi and nothing is using the serial port (e.g. rfsensor.py).

The last step is to get lastest firmware for the RF sensors which is [rf_rev7-4.hex](../apps/rf_rev7-4.hex)

Then Run the utility:

PC version
```
c:\ccti-prog\ccti-prog.exe -d /comX -f rf_rev7-4.hex
```
pi@raspberrypi:~/pep/cctl-prog $ sudo ./cctl-prog  -d /dev/serial0 -f rf_rev7-4.hex
```
Waiting 10s for bootloader, reset board now<br />
...Bootloader detected<br />
Erasing page 1<br />
Erasing, programming and verifying page 2<br />
Erasing, programming and verifying page 3<br />
Erasing, programming and verifying page 4<br />
Erasing, programming and verifying page 5<br />
Erasing, programming and verifying page 6<br />
Erasing, programming and verifying page 7<br />
Erasing, programming and verifying page 8<br />
Erasing, programming and verifying page 9<br />
Erasing, programming and verifying page 10<br />
Erasing, programming and verifying page 11<br />
Erasing, programming and verifying page 12<br />
Erasing, programming and verifying page 13<br />
Erasing, programming and verifying page 14<br />
Erasing, programming and verifying page 15<br />
Erasing, programming and verifying page 16<br />
Erasing, programming and verifying page 17<br />
Erasing, programming and verifying page 18<br />
Erasing, programming and verifying page 19<br />
Erasing, programming and verifying page 20<br />
Erasing, programming and verifying page 21<br />
Erasing, programming and verifying page 22<br />
Erasing, programming and verifying page 23<br />
Erasing page 24<br />
Erasing page 25<br />
Erasing page 26<br />
Erasing page 27<br />
Erasing page 28<br />
Erasing page 29<br />
Erasing page 30<br />
Erasing page 31<br />
Programming complete

The chip now has a new production version installed. Verify it worked by checking the version (rf_config.py 01 VERSION).

Example:

```
python rf_config.py 01 VERSION
SENT     : 03VERSION
RECEIVED : 03VER7.x---
```
You will need to change the device id to another id, care must be taken because the default device ID for the IOT Raspberry Pi is 01.
The example below changes the Device ID from 01 to 05:
```
python rf_config.py 01 CHDEVID05
SENT     : 01CHDEVID05
RECEIVED : 01CHDEVID05
```
{% include note.html content="The default firmware for the IOT gateway is Version 2.0, bacause as it can not be a sensor. The newer firmware could impact its performance." %}



