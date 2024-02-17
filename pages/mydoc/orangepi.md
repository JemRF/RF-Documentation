---
title: Using Orange Pi with JemRF Applications
keywords: Orange Pi, software, IOT Gateway
last_updated: Feb 15, 2023
tags:
summary: "This page provides review of the Orange Pi hardware versions with JemRF IOT Gateway."
sidebar: mydoc_sidebar
permalink: orangepi.html
folder: mydoc
---

# Testing an Orange Pi Zero 2 with JemRF products

With the current high cost and lack of availability of Raspberry Pi 3, 4, and Zero, would the Orange Pi work with the JemRF IOT Gateway? So I went to OrangPI.org to look at the different Orange Pi models.

My quest started with the orange Pi website. I found the address at [http://orangepi.org](http://orangepi.org/). Unfortunately, the orangepi.org does not support a secure (https) connection.

I found an excellent selection of small RPi-like boards with lots of features. Most had more memory and a faster processor than the standard Raspberry Pi. Although when they first started, they tried to make the GPIO bus compatible with the Raspberry Pi, most of the models today are different. The GPIO connector had a very different pin-out from the RPi Standard. Some of these changes were because most of the Orange PI models have additional options like additional serial ports.

Reviewing all the different products, I first found the power and ground pins to be consistent with the Raspberry Pi, but most of the discrete GPIO pins are different and only 26 pins.

Reviewing the online specification for systems that would support the IOT Gateway hardware, my review was:

- Orange Pi 5 - Yes,
- Orange Pi 3 LTS - No
- Orange Pi 4 LTS - No
- Orange Pi R1 Plus LTS - No, no GPIO connector
- Orange Pi One - Yes
- Orange Pi Zero v1.2 - Yes
- Orange Pi Zero 2 v1.5 - Yes, tested and verified to work.

Three things I need to note:

1. The Yes does not mean the same as RPi, just the critical hardware pins for the IOT Gateway appear to match.
2. When plugged into Orange Pi's GPIO interface, the IOT Gateway would extend to the outside and not over the top of the processor like the standard Raspberry Pi.
3. The serial pins may match from a hardware view, but from a software view, not quite. Because the Orange Pi products have more serial interfaces than a Pi, the serial port numbers differ. For example, the serial port number for the Orange Pi Zero 2 is /dev/ttyS5.

The Orange Pi Zero 2 looked promising for my testing because it had the features I wanted; enough memory, a fast processor, and a reasonable price. After watching YouTube videos, it boots to a Desktop similar to the Raspberry Pi. The Orange Pi Zero also requires a console connection to get it started. Details on the Orange Pi Zero 2 are at: [http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-Zero-2.html](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-Zero-2.html).

I ordered it from Amazon, and when it arrived, I downloaded the Orange PI OS release for the Orange PI OS for the Pi 2 Zero, which is a derivative of Debian, Bullseye. You Install the OS on an SD card, just like a Pi, and it is up and running with an Orange Pi Desktop. I found the Orange Pi OS to perform better than my Raspberry Pi 3B. The Orange OS has limited features included, but it was responsive with all the setup features to add more software.

It comes with an Orange PI Configuration application similar to the Raspberry Pi. Depending on need, most Orange Pi Systems come with five serial ports. Serial port 5, or ttyS5 replaces the Pi Serial0 or ttyAMA0 and needs to be enabled.

Running the JemRF Applications is the same as configuring a new RPi.

1. sudo apt update
2. sudo apt upgrade -y
3. sudo Install pip
4. sudo pip install pyserial, numby, gpio (Note: pyserial is the python3 replacement for python-serial)
5. Edit the /boot/orangepiEnv.txt file and add the following:
6. verlays=uart5
7. sudo reboot

After completing these steps, the OrangePi will be ready to install the Projects applications.

Before adding the software to my project, I wanted to test the IOT Gateway.

To do that I did the following:

1. mkdir pep
2. wget -N [www.privateeyepi.com/downloads/python3/install.sh](http://www.privateeyepi.com/downloads/python3/install.sh)
3. sh install.sh
4. mkdir rf\_tools
5. cd rf\_tools
6. sudo git clone https://github.com/JemRF/rf\_tools.git

By default, only Python 3 is installed and works using python3. If you want to enter python and not python3, run this command:

- sudo ln -s /usr/bin/python3 /usr/bin/python

Almost there, to run the JemRF/PrivateEyePi application on the Orange Pi will only require two changes to the applications:

1. Edit **rlib.py** and change:
2. **/dev/serial0** to **/dev/ttyS5**
3. Edit **alarmfunctionsr.py** and change:
4. Import RPi.GPIO as GPIO to import gpio as GPIO

Now serial\_mon.py and rf\_config.py should work. I tested the serial RF monitor:

1. cd
2. cd pep
3. python3 rf\_tools/serial\_mon.py