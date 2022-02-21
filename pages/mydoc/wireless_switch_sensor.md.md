---
title: Wireless Switch Sensor
keywords: wireless switch, switch, sensor, door, window
last_updated: Feb 20, 2022
tags:
summary: "This page explains the JEMRF Wireless Switch Sensor"
sidebar: mydoc_sidebar
permalink: wireless_switch_sensor.html
folder: mydoc
---

{% include image.html file="big wireless switch.jpg" alt="Wireless Switch Sensor"%}


## Product Description
The Wireless Switch Sensor can sense the opening or closing of a tactile switch. Usually used for door window sensing for alarm system, but is also the foundation for other sensors like water sensor and motion sensor.

## Installation
* Thread the tactile switch wires through the case enclosure opening and solder the two sires to the through holes labeled BTN.

{% include image.html file="IMG_2187.jpg" alt="Wireless Switch Sensor"%}

* Install battery and close enclosure as described [here](sensor_installation.html).

* Thread the antennae through the the case enclosure and push the sensor into place within the enclose

{% include image.html file="IMG_2198.jpg" alt="Wireless Switch Sensor"%}

{% include image.html file="IMG_2208.jpg" alt="Wireless Switch Sensor"%}

* Close the enclosure case using a Phillips screw driver

{% include image.html file="IMG_2177.jpg" alt="Wireless Switch Sensor"%}


## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation

## Product Specifications
* [Device specifications](rf_device_specs.html)

### Electrical
* 2.2-3.3V
* Powered by CR2032 coin cell battery
* Can be externally powered by soldering to the 3V3 and GND through holes on the PCB
* Most energy efficient when the BTN contacts are not connected, therefore use a normally closed switch to monitor a door/window that is normally closed and a normally open switch to monitor a door/window that is normally open
* Tested at 288 (144 door open/door close) messages per day for 1 year on one battery

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)
* Opening or closing the switch will cause the device to come out of sleep mode, transmit a reading and then go back to sleep
* For Flex modules use Pin 6 and Pin 10 to connect to the external switch

### Messaging details
* BUTTONON- (sent when the switch is open)
* BUTTONOFF (sent when the switch is closed)
* STATEON- (the switch state is sent every INYVL minutes if the switch is open)
* STATEOFF (the switch state is sent every INTVL minutes if the switch is closed)
* BUTTON (the BUTTON command requests the the switch state from the sensor)

{% include note.html content="On power up of a wireless switch, do not open/close the switch during the first 5 seconds as this will cause the device to start sending messages and cancel the startup sequence and prevent the device from entering sleep mode."%}
### Physical
* 36mm x 36mm x 15mm case size (1.42" x 1.42" x .59")

## Default configuration
* Type 1 ([Type](types.html) 1 sensor)
* NOMSG3 (Sends 3 switch readings every time the switch state changes)
* INTVL030 (Sends the switch state every 30 minutes)
* SLEEP (puts the device into [sleep mode](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details

{% include note.html content="Did you know this sensor is also a [multi function sensor](multi function sensors.html)?"%}