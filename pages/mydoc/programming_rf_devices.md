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
Once complete you will need a ccti-programmer applicaition.
Download [ccti-prog zip](../apps/ccti-prog.zip) for the Windows app ccti-prog.exe.

If you want to use a Raspberry Pi the source for the ccti-prog is included with a Makefile.

To compile your own
```
make
gcc -o ccti-prog -Wall ccti-prog.c hex.c
```
Make sure an RF Gateway is attached to the Pi and nothing is using the serial port (e.g. rfsensor.py).

The lastest firmware for the RF sensors is [rf_rev7-4.hex](../apps/rf_rev7-4.hex)
Run the utility:
```
pi@raspberrypi:~/pep/cctl-prog2 $ sudo ./cctl-prog  -d /dev/Serial0 -f iot2.hex
```
Waiting 10s for bootloader, reset board now
...Bootloader detected
Erasing page 1<br />
Erasing, programming and verifying page 2<br />
Erasing, programming and verifying page 3<br />
Erasing, programming and verifying page 4<br />
Erasing, programming and verifying page 5<br />
Erasing, programming and verifying page 6
Erasing, programming and verifying page 7
Erasing, programming and verifying page 8
Erasing, programming and verifying page 9
Erasing, programming and verifying page 10
Erasing, programming and verifying page 11
Erasing, programming and verifying page 12
Erasing, programming and verifying page 13
Erasing, programming and verifying page 14
Erasing, programming and verifying page 15
Erasing, programming and verifying page 16
Erasing, programming and verifying page 17
Erasing, programming and verifying page 18
Erasing, programming and verifying page 19
Erasing, programming and verifying page 20
Erasing, programming and verifying page 21
Erasing, programming and verifying page 22
Erasing, programming and verifying page 23
Erasing page 24
Erasing page 25
Erasing page 26
Erasing page 27
Erasing page 28
Erasing page 29
Erasing page 30
Erasing page 31
Programming complete

The chip now has a new production version installed. Verify it worked by checking the version (rf_config.py 01 VERSION).

Example:

```
python rf_config.py 01 VERSION
SENT     : 03VERSION
RECEIVED : 03VER7.x---
```
You will need to change the device id to another id, care must be taken because the default device ID for the IOT Raspberry Pi is 01.
```
python rf_config.py 01 CHDEVIDxx
SENT     : 01CHDEVIDxx
RECEIVED : 01CHDEVIDxx
```



