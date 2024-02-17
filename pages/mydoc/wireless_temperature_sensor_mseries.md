---
title: Wireless Temperature Sensor M-Series
keywords: wireless temperature, temperature, sensor, DS18B20, digital
last_updated: Jan 8, 2022
tags:
summary: "This page explains the JEMRF Wireless M Series Temperature Sensor"
sidebar: mydoc_sidebar
permalink: wireless_temperature_sensor_mseries.html
folder: mydoc
---

<img src="images/mseriesrf60.jpg" width="425"/> <img src="images/mseriesrf61.jpg" width="425"/>

## Product Description
Wireless temperature sensor M Series come use the industry standard digital sensor, the Dallas DS18B20 with accuracy of ~.5°C. Housed in a AA battery case with an On/Off switch the very low power sensor can last up to a year on a set of good AA batteries when configured to send readings every 5 minutes.

## Installation
Install battery by sliding the back off and removing and replacing the AA batteries, recommend alkaline batteries.

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation

## Product Specifications
* ~.5°C accuracy
* Dallas DS18B20 digital temperature sensor

### Electrical
* 2.2-3.3V
* Powered by two AA batteries
* On/Off switch on top to power down the sensor when off line.

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)
* [Device specifications](rf_device_specs.html)

### Messaging details
* TMPC99.99 (temperature reading format)
* TEMPC (the TEMP command requests the sensor to transmit a temperature reading)

### Physical
* 65mm x 70mm x 20mm case size (2.5" x 2.75" x .75")

## Default configuration
* Type 4 ([Type](types.html) 4 sensor)
* NOMSG1 (Sends 1 temperature reading every cycle)
* INTVL005 (Sends a temperature reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details

{% include note.html content="Did you know this sensor is also a [multi function sensor](multi function sensors.html)?"%}
