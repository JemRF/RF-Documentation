---
title: Wireless Light Sensor
keywords: wireless light, light, photoresistor, photo resistor, photo-resistor
last_updated: Sep 28, 2020
tags:  
summary: "This page explains the JEMRF Wireless Light Sensor"
sidebar: mydoc_sidebar
permalink: wireless_light_sensor.html
folder: mydoc
---

<img src="images/IMG_6859.jpg" style="width:200px;">

## Product Description

* Battery operated wireless light sensor transmitter.

* Can be used for detecting dusk/dawn or interior light levels. Typically used to trigger an event, like switch a light on/off or opening closing automatic blinds or switching anything on off. 

* The device transmits a value between 0 (dark) and 32,000 (light) and all light levels in between. 

The sensor is pre-configured to transmit a temperature reading every 5 minutes. The device sleeps in between transmission in order to save battery power and is awoken every 5 minutes by an internal timer. This allows the device to be used for around 1 year on a single coin cell battery. The transmission interval can be configured between 1 minute and 999 minutes. If powered externally then the device can operate in a fully awake mode and luminescence readings can be requested from the sensor in a request/reply fashion.

Here is a graph showing a sunrise where the reading has been converted to a value between 0 and 60:

<img src="images/Sunrise_Graph.png"> 

## Installation
Install battery and close enclosure as described [here](sensor_installation.html).

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation 

## Product Specifications
* Photo-resistor type 5516, 100V, 540nM, 5-10K(light), 500k(dark)
* [Device specifications](rf_device_specs.html)

### Electrical
* 2.2-3.3V 
* Powered by CR2032 coin cell battery
* Can be externally powered by soldering to the 3V3 and GND through holes on the PCB

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)

### Messaging details
* ANA99999 (temperature reading format)
* ANAA (the ANAA command requests the sensor to transmit a temperature reading)

### Physical
* 36mm x 36mm x 15mm case size (1.42" x 1.42" x .59")

## Default configuration
* Type 5 ([Type](types.html) 5 sensor)
* NOMSG1 (Sends 1 temperature reading every cycle)
* INTVL005 (Sends a temperature reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details

{% include note.html content="Did you know this sensor is also a [multi function sensor](multi function sensors.html)?"%}
