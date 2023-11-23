---
title: Wireless Temperature Sensor
keywords: wireless temperature, temperature, sensor, 10k, thermistor
last_updated: Nov 22, 2023
tags:
summary: "This page details the JemRF Wireless Digital Temperature Sensor"
sidebar: mydoc_sidebar
permalink: wireless_temperature_sensor.html
folder: mydoc
---

<img src="images/wireless temperature sensor 1.jpg" width="425"/> <img src="images/wireless temperature sensor digital.jpg" width="425"/>

## Product Description
The Wireless Temperature Sensor is now all digital, replacing the original [Wireless Temperature Sensor](wireless_temperature_sensor_analog.html)

Wireless temperature sensor now uses a Dallas 18B20 1-wire digital sensor with accuracy of ±.5°C accuracy. The sensor still operates at a very low power and can last up to a year on a single CR2032 coin cell battery when configured to send readings every 10 minutes.

## Installation
Install battery and close enclosure as described [here](sensor_installation.html).

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation

## Product Specifications
* ±.5°C accuracy
* DS18B20 1-wire digital sensor
* [Sensor Specification](ds18b20.html)

### Electrical
* 2.2-3.3V
* Powered by CR2032 coin cell battery
* Can be externally powered by soldering to the 3V3 and GND through holes on the PCB

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)
* [Device specifications](rf_device_specs.html)

### Messaging details
* TMPC99.99 (temperature reading format)
* TEMPC (the TEMP command requests the sensor to transmit a temperature reading)

### Physical
* 36mm x 36mm x 15mm case size (1.42" x 1.42" x .59")

## Default configuration
* Type 4 ([Type](types.html) 4 sensor)
* NOMSG1 (Sends 1 temperature reading every cycle)
* INTVL005 (Sends a temperature reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details

{% include note.html content="Did you know this sensor is also a [multi function sensor](multi function sensors.html)?"%}
