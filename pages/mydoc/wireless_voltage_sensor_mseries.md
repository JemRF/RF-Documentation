---
title: Wireless Voltage DC Sensor M-Series
keywords: wireless voltage, voltage, sensor, VDC, digital
last_updated: Jan 15, 2022
tags:
summary: "This page explains the JEMRF Wireless M Series Voltage DC Sensor"
sidebar: mydoc_sidebar
permalink: wireless_voltage_sensor_mseries.html
folder: mydoc
---

<img src="images/mseriesrf60.jpg" width="425"/>

## Product Description
Wireless voltage DC sensor M Series measures DC voltage from 0-30VDC. Two screw terminal connect allows custom wiring options. Housed in a AA battery case with an On/Off switch the very low power sensor can last up to a year on a set of good AA batteries when configured to send readings every 5 minutes.

## Installation
Install battery by sliding the back off and removing and replacing the AA batteries, recommend alkaline batteries.

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation

## Product Specifications
* +- .05 VDC accuracy
* Requires firmware version 7.6

### Electrical
* 2.2-3.3V
* Powered by two AA batteries
* On/Off switch on top to power down the sensor when off line.

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)
* [Device specifications](rf_device_specs.html)

### Messaging details
* VDC99.99 (temperature reading format)
* VDC (the VDC command requests the sensor to transmit a voltage reading)

### Physical
* 65mm x 70mm x 20mm case size (2.5" x 2.75" x .75")

## Default configuration
* Type 12 ([Type](types.html) 12 sensor)
* NOMSG1 (Sends 1 voltage reading every cycle)
* INTVL005 (Sends a voltage reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details


