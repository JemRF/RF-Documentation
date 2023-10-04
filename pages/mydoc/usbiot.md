---
title: Using the USB JemRF IOT Gateway
keywords: USB IOT Gateway, software, IOT Gateway
last_updated: July 9, 2023
tags:
summary: "This page provides review of the USB versions with JemRF IOT Gateway."
sidebar: mydoc_sidebar
permalink: usbiot.html
folder: mydoc
---

# Introduction of USB IOT Gateway

With the JemRF USB IOT Gateway you can run your data collection on a Windows Laptop or Linux computer.
The USB IOT Gateway can run the same Python 3 code on windows that run on the Raspberry Pi and the Orange Pi.<br>
The only adjustments are selecting the serial port from Linux /dev/serialx format to Windows Comx format.

The default address for the USB IOT Gateway is 02, so it can run along side the
RPI or Orange PI gateway which is at the default address of 01.

# Using a Pi computer
Running the JemRF Applications is the same as configuring a new Raspberry or Orange Pi.  Those instructions are at:
https://documents.jemrf.com/iot_gateway.html for the Raspberry PI
https://documents.jemrf.com/orangepi.html for the Orange PI

# Using a Windows 10/11 computer
You will need Python 3 installed. Use Windows Store to install the latest Python 3.
After Python 3 is installed, to load the modules needed for JemRF software:

Open Terminal windows and at the command prompt
1. pip3  install pyserial numpy
2. winget install --id Git.Git -e --source winget

After completing these steps, the PC will be ready to install the JemRF Projects applications.

To install the JemRF Applications:

1. mkdir \pep
2. cd \pep
3. wget -O install.sh [www.privateeyepi.com/downloads/python3/install.sh](https://www.privateeyepi.com/downloads/python3/install.sh)
4. Expand-Archive  pep_python3.zip  .
7. git clone https://github.com/JemRF/rf_tools.git

With Python 3 installed to start Python you can use python3 or just enter python.

Almost there, to run the JemRF/PrivateEyePi application on the PC will only require two changes to the applications:

1. Edit **rlib.py** and change:
2. **/dev/serial0** to **comx**   (Where comx is the USB Com port on your system.)
3. Edit **alarmfunctionsr.py**
 change:
  - "Import RPi.GPIO as GPIO"  to  "import gpio as GPIO"

Now serial\_mon.py and rf\_config.py should work. I tested the serial RF monitor:

1. cd
2. cd pep
3. python3 rf\_tools/serial\_mon.py