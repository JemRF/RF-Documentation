---
title: WiFi Sensor as Temperature and Humidity Sensor
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Dec 12, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-temp-hum.html
folder: wifidoc
---
## Introduction
The S32 WiFi Sensor support and internal HTU21D Temperature and Humidity Sensor. The HTU21D provides a Temperature reading from -40℃ – 105℃ and Humidity readings from 0 to 100%. The sensor is highly accurate (±0.5°C accuracy) from -20℃ to 85℃.

The JemRF S32 WiFi Sensor is based on the ESP32 processor, which makes it more than just upgraded Version; it is the start of our next-generation of sensors. The S32 WiFi Sensor expands the versatile device features of the older device with a larger collection of sensor options, ready to go with simple plug-and-play, for quickly and inexpensively updating the cloud.

The options include options for multiple sensors including up to 4 external temperature sensors at lengths from 1 m to 5 meters, all at the same time.  The Sensor also supports remote pressure sensors from 10 to 500 psi. Has an interface for a remote digital flow sensor or door sensor.

The JemrRF S32 WiFi Sensor can support multiple sensor types concurrently, reducing the cost of various sensors in a single location.

## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any Wi-Fi device (e.g., PC, phone, tablet).
- Uses your local 2.4 GHz WiFi to access the Internet
- Cyclic temperature transmission mode with configurable send interval
- Supports both Celsius and Fahrenheit temperature readings
- MQTT Setup page for connection to the MQTT Broker to relay temperature and humidity readings.
- The WiFi Sensor supports 3 MQTT formats; more details are available in (WiFi Pro Devices MQTT Settings)[https://documents.jemrf.com/wifi32s-mqtt.html]. The MQTT connection can be upgraded from a standard non-secure to a secure, trusted connection.
- MQTT Home Assistant Auto-Discovery supported.
- Supports HTU21D Temperature (-40℃ – 105℃) and Humidity - Sensor
- Support White Label Options

## Required, but not included:

USB-C cable and USB power supply.
We have USB-C cables at our store, (JemRF Store)[https://www.jemrf.com].

## Tech Specs:

* Dimensions 74mm x 55mm x 28mm
* Powered either by a USB-C cable 5VDC.
* Temperature range: -55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C
