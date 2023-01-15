---
title: Using Orange Pi with JemRF Applications
keywords: Orange Pi, software, IOT Gateway
last_updated: Jan 14, 2023
tags:
summary: "This page provides review of the Orange Pi hardware versions with JemRF IOT Gateway."
sidebar: mydoc_sidebar
permalink: ornagepi.html
folder: mydoc
---
Using an Orange Pi Zero 2 with JemRF products

With the current high cost and lack of availability of Raspberry Pi 3, 4 and Zero I wonder if the Orange Pi would work with the JemRF IOT Gateway.
I went to OrangPI.org to look at the different Orange Pi models. The first thing that happened was that I failed to find the website.  This is because they do not support a secure (https) connection, so I changed it to:
 [http://orangepi.org](http://orangepi.org/) and the website came up.

I found a really good selection of small RPi like boards with lots of features, most had more memory and a faster processor than the normal Raspberry Pi.  While I believe when they first started they tried to make the GPIO bus be compatible with the Raspberry Pi but most of the models today are not. I found the GPIO connector had a very different pin out from the RPi Standard. Some of these changes were because most of the Orange PI models have additional options like additional serial ports.

Reviewing all the different products the first thing I found was the power and ground pins to be consistent with the Raspberry Pi ,but most of the discrete GPIO pins are different  and only 26 pins.

Reviewing the online specification for systems that would support the IOT Gateway hardware my review was:


- Orange Pi 5 - Yes,
- Orange Pi 3 LTS - No
- Orange Pi 4 LTS - No
- Orange Pi R1 Plus LTS - No, no GPIO connector
- Orange Pi One - Yes
- Orange Pi Zero v1.2 - Yes
- Orange Pi Zero 2 v1.5 - Yes

Two things I need to note:

1. The Yes does not mean the same as RPi, just the critical hardware pins for the IOT Gateway match. When plugged into Orange Pi's GPIO interface, the IOT Gateway would extend to the outside of the processor and not over the top of the processor like the standard Raspberry Pi.
2. The serial pins may match from a hardware view, but from a software view not quite. Because the Orange Pi products have more serial interfaces than a Pi, the serial ports numbers are different. More on that later.

For my testing the Orange Pi Zero 2 looked good, because it had the features I wanted with enough memory, a fast processor, a good price and after watching YouTube videos it also boots to Desktop just like the Pi, the Orange Pi Zero requires console connection to get it started..
Details on the Orange Pi Zero 2 are at:
 [http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-Zero-2.html](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-Zero-2.html).

 I ordered it from Amazon and when it arrived, I downloaded the Orange PI OS release for the Orange PI OS for the Pi 2 Zero, which is a derivative of Debian, Bullseye. You Install the OS on an SD card just like a Pi and it is up and running with an Orange Pi Desktop. I found the Orange Pi OS to perform as well, or better than my Raspberry Pi 3B.The Orange OS is stripped of extra features included with Rasputon, but it was responsive with all the setup features to add more software..

It comes with an Orange PI Configuration application similar to the Raspberry Pi.  Depending on need, most of the Orange Pi Systems come with five serial ports.  Serial port 5, or ttyS5 replaces the Pi Serial0 or ttyAMA0.

To run the JemRF Applications, the process is mostly the same as configuring a new RPi.

1. sudo apt update
2. sudo apt upgrade -y
3. sudo Install pip
4. sudo pip install pyserial, numby, gpio (Note: pyserial is the python3 replacement for python-serial)
5. Edit the /boot/orangepiEnv.txt file and add the following:
  1. verlays=uart5
6. sudo reboot

The OrangePi is now ready to install the Projects applications

First do get the software, for my project I just wanted to test the IOT Gateway.

To do that I did the following:

1. mkdir pep
2. wget -N [www.privateeyepi.com/downloads/python3/install.sh](http://www.privateeyepi.com/downloads/python3/install.sh)
3. sh install.sh
4. mkdir rf\_tools
5. cd rf\_tools
6. sudo git clone https://github.com/JemRF/rf\_tools.git

By default only Python 3 is installed and works using python3. If you want to enter python and not python3, run this command:

- sudo ln -s /usr/bin/python3 /usr/bin/python

Almost there, to run the JemRF/PrivateEyePi application on the Orange Pi will only requires 2 changes to the applications:

1. Edit **rlib.py** and change:
  1. **/dev/serial0** to **/dev/ttyS5**
2. Edit **alarmfunctionsr.py** and change:
  1. import RPi.GPIO as GPIO

To

import gpio as GPIO

Now serial\_mon.py and rf\_config.py should work. I tested the serial RF monitor:

1. cd
2. cd pep
3. python3 rf\_tools/serial\_mon.py
