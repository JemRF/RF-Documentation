---
title: Flex Radio Module
keywords: flex, temperature, humidity, pressure, alarm, button, reed, door, window, ds18b20, dht22, sht21, bme280, bmp280
last_updated: Sep 28, 2020
tags:  
summary: "This page explains the JEMRF Flex Radio Module"
sidebar: mydoc_sidebar 
permalink: flex.html
folder: mydoc
---

{% include image.html file="flex rf module tn.PNG" alt="Flex Radio Module"%}

## Product Description
The Flex RF Module is an all purpose module designed for prototyping on breadboards but can also be deployed on a PCB using 2.54mm 10 pin headers. It is commonly used in alarm systems, weather stations, remote control (e.g. lights, garage doors), temperature and humidity monitoring or lightweight wireless communications.

20 pins provides access to all JEMRF functionality (sensors & IoT Gateway) in one module. The radio module comes with support for a multitude of external sensors often used for Internet Of Things (IOT) projects.

## Pinout

{% include image.html file="flex pinout v2.PNG" alt="Flex Radio Pinout"%}

<BR>
**Pin Description**
 
 * Pin 1 - 3V3 Power
 * Pin 2, 19 & 20 - Pins used for the CC1110 interface to the CC Debugger used for loading new firmware at factory
 * Pin 3,4 & 5 - GPIO output pins that can be set high (3V3) or low (0V) using the [GPIO](rf_message_reference.html) command
 * Pin 6 - Used for tactile switches, like reed switches or magnetic alarm switches. A BUTTON radio message is fired when connected and unconnected to GND
 * Pin 7 - DHT22 - Connect the data pin on the DHT22 sensor to this pin using the [TEMPB](rf_message_reference.html) command
 * Pin 8 - DS18B20 - Connect the data pin on the DS18B20 sensor to this pin using the [TEMPA](rf_message_reference.html) command
 * Pin 9 - Spare pin not used yet
 * Pin 10 - Ground
 * Pin 11 - Connect to one of the two 10k thermistor connectors (the other goes to 3V3 or Pin 12). Query the temperature using the [TEMP](rf_message_reference.html) command
 * Pin 12 - Can be used to power external sensors. This pin goes high before reading an external sensor and low after the sensors reading. This is a good option to conserve battery power by not always powering sensors that are not in use. 
 * Pin 13 & 14 - SDL and SCL respectively of the I2C interface used by BME280 and SHT21/HTU21 sensors
 * Pins 15 & 16 - When sensor is Type 2 (IoT Gateway mode)[types.html] then these pins are TX and RX respectively and used for the serial interface to the controller (e.g. Raspberry Pi). When set to Type 7 then these pins can be used to control 2 external relays using the RELAYA or RELAYB commands. 
 * Pins 17 & 18 - Analog input pins that can read any external analog sensor using the [ANAA and ANAB](rf_message_reference.html) commands

## Product Specifications
* Support for growing list of sensors:
  - DS18B20 Temperature Sensor
  - DS18B20 Waterproof Sensor
  - DHT22 Temperature and Humidity Sensor
  - Tactile switch sensor (e.g. reed switch or magnetic switch for alarms)
  - BME280/BMP280 Pressure, Temperature and Humidity Sensor
  - SHT21/HTU21 Humidity and Temperature Sensor
  - MAX7219 digital display control module
  - Motion Sensors
  - Forked Water Sensor
  - 10k Thermistor Temperature Sensor
  - 10k Waterproof Thermistor Temperature Sensor
  - Any analog sensor (e.g. light sensor)
* Single firmware supports all the above sensors. No need to load new firmwares unless you need to upgrade to support new sensors we add. Refer to the [message reference](rf_message_reference.html) for details on which messages are support by which version.
* [Device specifications](rf_device_specs.html)

### Electrical
* 2.2-3.3V 
* Can be powered by CR2032 coin cell battery, or external power supply

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)

### Physical
* 25.40mm x 30.48mm PCB size (1" x 1.2") 
* Pin spacing 2.54mm (0.1")

## Default configuration
* Type 1 ([Type](types.html) 1 sensor)
* Refer [device configuration](configuration_overview.html) for more details


