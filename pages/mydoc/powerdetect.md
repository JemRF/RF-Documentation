---
title: Wireless Power Detect Sensor
keywords: wireless power detector AC sensor
last_updated: Dec 2, 2024
tags:
summary: "This page explains the JemRF Wireless Power Detect Sensor"
sidebar: mydoc_sidebar
permalink: wireless_power_sensor.html
folder: mydoc
---

{% include image.html file="IMG_4954.jpg" alt="Wireless Power Detector Sensor"%}


## Product Description
The Wireless Power Detector Sensor monitors AC power 100 to 240 VAC for power loss. In less than 2 seconds of power lost, it sends state change to the monitoring server via the local Gateway.  This product assumes that the local Gateway, WiFI access point and the Internet Router are all on backup power (UPS).
The sensor has internal storage power to last for just over 2 minutes after power loss. After the initial message of power loss, With the normal update time of minute, at the next one minute interval it will report a status it will send the initial message power is off, and again a minute later that power is still off. When power is restored it will power up and report power has been restored.

## Installation
Installation is easy, just plug it into the power circuit you want to monitor.

{% include image.html file="IMG_4955.jpg" alt="Wireless Power Detect Sensor"%}

## Testing
The sensor Id is at the bottom of the label. Using the JemRF python application rf_serial.py or the sensor list on a WiFi Gateway, you will see the sensor appear in the list.

## Product Specifications
* [Device specifications](rf_device_specs.html)

### Electrical
* Standard US AC outlet for 120 VAC.
* 2 pin AC US prongs

### Functional
* Standard JemRF wireless sensors, refer [RF Communications section](rf_basics.html) for all the details
* Power status is provided with On and Off State messages when the device to come out of sleep mode, transmit a reading and then go back to sleep

### Messaging details
* BUTTONON- (sent when power is Lost)
* BUTTONOFF (sent when power is Restored)
* STATEON- (the switch state is sent every INYVL minutes indicating power is Off)
* STATEOFF (the switch state is sent every INTVL minutes indicating power is On)


### Physical
* 3 inch x 2 inch x 2 inch

## Default configuration
* Type 1 ([Type](types.html) 1 sensor)
* NOMSG1 (Sends 1 switch readings every time the switch state changes)
* INTVL001 (Sends the switch state every minute)
* SLEEP (puts the device into [sleep mode](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details
