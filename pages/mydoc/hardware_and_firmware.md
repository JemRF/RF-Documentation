---
title: Hardware & Firmware
keywords: hardware, firmware, update, download
last_updated: July 3, 2016
tags:  
summary: "This page explains the JEMRF hardware and firmware"
sidebar: mydoc_sidebar
permalink: hardware_and_firmware.html
folder: mydoc
---

## Connecting an RF device to an MCU

We have a number of different board layouts but each board has a standard edge board connector that can be used to connect a device directly to an MCU (like Raspberry Pi or Arduino). The main reason for doing this is to configure the 16 character password (see [sensor encryption](encryption.html)). See below diagram for connecting a device to an MCU. 

{% include image.html file="MCU to Device Schematic.png" alt="MCU to Device Schematic"%}  

{% include note.html content="
The Flex module has the same edge board connection but also has RX and TX pins (pins 15 & 16 respectively) and Ground on pin 10." %}

## Pinouts

|Flex Pin|Sensor node*|MCU Pin|Raspberry Pi Pin|
|--------|------------|-------|----------------|
| 1 | 3V3 | 3V3 | 1 |
| 10 | GND | GND | 6 |
| 15 | Tx | Rx | 10 |
| 16 | Rx | Tx | 8 |

{% include note.html content="*It is possible to convert a sensor mode into a Gateway, however your will need to solder wires or pins to the board contacts labeled in the above table." %}


## Serial Port Settings

The serial port is configured as follows: <BR><BR>
Baud : 9600 <BR>
Data : 8 <BR>
Parity : None <BR>
Stop : 1 <BR>


## Hardware & Firmware
There is common firmware (software that is loaded onto the chip) across all our RF modules. This means you don't need to load different firmwares when you want to re-configure a RF module to do something else. The RF modules are highly configurable. There are however hardware differences (i.e. physical board differences) between some of the sensors that are described in the product pages of each sensor. The Flex modules provides the greatest flexibility because it has 20 pins that expose all of the functionality available on our sensors. 

### Firmware versions
As we develop more sensors we release new firmware versions for our sensors. You can check the version of a firmware using the VERSION command. The [Message Reference Section](rf_message_reference.html) of this documentation contains details on what functionality is available on each version. 



