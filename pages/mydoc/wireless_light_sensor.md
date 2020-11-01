---
title: Wireless Light Sensor
keywords: wireless light, light, sensor, photoresistor, photo-resistor, luminescence
last_updated: Sep 28, 2020
tags:  
summary: "This page explains the JEMRF Wireless Light Sensor"
sidebar: mydoc_sidebar
permalink: wireless_light_sensor.html
folder: mydoc
---

<img src="images/wireless light sensor.jpg" width="425"/> 

## Product Description
The device transmits a value between 0 (dark) and 32,000 (light) and all light levels in between. Very low power and can last up to a year on a single CR2032 coin cell battery when configured to send readings every 10 minutes. 

## Installation
Install battery and close enclosure as described [here](sensor_installation.html).

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation 

## Product Specifications
* Photo-resistor 5516 100V 540mm Light 5-10k Dark 500k
* [Device specifications](rf_device_specs.html)

### Electrical
* 2.2-3.3V 
* Powered by CR2032 coin cell battery
* Can be externally powered by soldering to the 3V3 and GND through holes on the PCB

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)

### Messaging details
* ANAA99.99 (analog reading format)
* ANAA (the ANAA command requests the sensor to transmit an analog reading)

### Physical
* 36mm x 36mm x 15mm case size (1.42" x 1.42" x .59")

## Default configuration
* Type 5 ([Type](types.html) 5 sensor)
* NOMSG1 (Sends 1 luminescence reading every cycle)
* INTVL005 (Sends a reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details

{% include note.html content="Did you know this sensor is also a [multi function sensor](multi function sensors.html)?"%}
