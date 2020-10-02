---
title: Configure Raspberry Pi Serial port
keywords: serial port, serial, gateway, Inappropriate ioctl for device, iotcl, /dev/ttyAMA0, Permission denied
last_updated: Oct 1, 2020
tags:  
summary: "This page explains how to enable the serial port on a Raspberry Pi"
sidebar: mydoc_sidebar
permalink: configure_serial_port.html
folder: mydoc
---

## Overview
The Raspberry Pi (RPI) has the serial port (pins 8-Tx & 10-Rx) configured for a login shell by default, therefore you have to configure it for serial use in order for the Wireless Gateway to communicate with the RPI. 

Open up a terminal window and type:

```
sudo raspi-config
```

Select "Interface options"

<img src="images/Interface_Options_large.png" width="425"/>

Then select "P6 Serial" option.

<img src="images/serial_large.png" width="425"/>

Say "No" to the question "Would you like a login shell to be accessible over serial"?

<img src="images/no_large.png" width="425"/>

The reply "Yes" to the question "Would you like the serial port hardware enabled?"

<img src="images/yes_large.png" width="425"/>

Exit, save and reboot (ctrl-x followed by "y").

## Special instructions for Raspberry Pi 3 & 4 only
You need to disable Bluetooth so that the serial port will work.
Edit config.txt

```
sudo nano /boot/config.txt
```

Page down to the bottom of the file and add the following line:
 
```
dtoverlay=pi3-disable-bt
```

Exit, save and reboot (ctrl-x followed by "y").

