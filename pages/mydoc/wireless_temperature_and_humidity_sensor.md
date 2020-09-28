---
title: Wireless Temperature and Humidity Sensor
keywords: wireless temperature, temperature, sensor, 10k, thermistor
last_updated: Sep 28, 2020
tags:  
summary: "This page explains the JEMRF Wireless Temperature and Humidity Sensor"
sidebar: mydoc_sidebar
permalink: wireless_temperature_and_humidity_sensor.html
folder: mydoc
---

<img src="temperature and humidity sensor 1 small.JPG" width="425"/> 

<img src="../images/temperature and humidity sensor 2 small.JPG" width="425"/> 

## Product Description
Wireless temperature and humidity sensor with high degree of accuracy (~0.3°C and +-2% Humidity). Very low power and can last 6 months on a single CR2032 coin cell battery when configured to send readings every 10 minutes. 

## Installation
Install battery and close enclosure as described [here](sensor_installation.html).

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation 

## Product Specifications
* ~0.3°C accuracy
* +-2% Humidity
* Sensirion based SHT21 sensor
* [Device specifications](rf_device_specs.html)

<BR>

**Sensor (SHT21) Performance:**
{% include image.html file="temperature_and_humidity_graphs_2_1024x1024.PNG" alt="Wireless Sensor Graphs"%} 

### Electrical
* 2.2-3.3V 
* Powered by CR2032 coin cell battery
* Can be externally powered by soldering to the 3V3 and GND through holes on the PCB

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)
* If the RF module cannot find the BME280 sensor then it will report back (NOSENSOR). Check the wiring and power to the BME280 module.


### Messaging details
* TMPA99.99 (temperature reading format)
* HUM99.99 (temperature reading format)
* HTU21 (the SHT21 command requests the sensor to transmit a temperature and humidity reading)

### Physical
* 51mm x 36mm x 20mm case size (2" x 1.42" x .79") 

## Default configuration
* Type 10 ([Type](types.html) 10 sensor)
* NOMSG2 (Sends 2 temperature & humidity readings every cycle)
* INTVL005 (Sends a temperature reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details


