---
title: The JemRF WIFI Sensor Pro Version Introduction
keywords: getting started introduction
last_updated: Dec  12, 2025
tags:
summary: "The Internet Of Things (IoT) is where everyday things (cars, homes, household appliances, plants) are being connected to the Internet where we can monitor and alert in ways not possible before. This document describes our WiFi Sensor and its place in the IoT Universe."
sidebar: wifi_sidebar
permalink: wifi32s-sensor.html
folder: wifidocs
---

## S32 WiFI Sensor

![WiFi Sensor Case](images/wifisensorcase.jpg "WiFi Case")

The JemRF WiFi Sensor Pro is based on the ESP32 processor, which makes it more than just upgraded Version; it is the start of our next-generation of sensors. The WiFi Sensor Pro expands the versatile device features of the older device with a larger collection of sensor options, ready to go with simple plug-and-play, for quickly and inexpensively updating the cloud. \
It comes in different configurations,
1. Temperature and Humidity Sensor with options,
2. Pressure Sensor with options,
3. Temperature sensor with options,
4. Contact Sensor with options.

The options for each include up to 4 external temperature sensors at lengths from 1 m to 5 meters, all at the same time.  The Sensor also supports remote pressure sensors from 10 to 500 psi. Has an interface for a remote digital flow sensor or door sensor.

The JemrRF WiFi Sensor Pro can support multiple sensor types concurrently, reducing the cost of various sensors in a single location.

It connects to your WiFI access point so you can send temperature readings to monitor.jemrf.com, or another monitoring application. Additionally, MQTT support is available for forwarding readings to an MQTT broker. It is fully assembled and requires no soldering. Connect it to power, and it will advertise itself as a wireless access point. Configure it through a web browser using its easy-to-use config application. Once configured, it will connect to your WiFI network, which will give it access to the internet and the JemRF Monitoring server, your own server, or run on a local network with custom software.\
The WiFi Sensor Pro intelligence monitors network connectivity, retrieves time from Internet Servers, and disables the onboard AP after 10 minutes of connection to the local WiFi to secure open access. If not connected to the Internet, the start time is set to October 1, 2025.\
The sensor provides options to customize for your business and to authenticate changes.


## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any Wi-Fi device (e.g., PC, phone, tablet).
- Uses your local 2.4 GHz WiFi to access the Internet
- Cyclic temperature transmission mode with configurable send interval
- Supports both Celsius and Fahrenheit temperature readings
- DS18B20 temperature sensors (Onboard or Extended) are used to measure temperatures from -55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C
- Note: The operating temperature for the WiFi Temperature sensor is -30F to +125.6F, -34C to 52C
- Supports HTU21D Temperature (-40℃ – 105℃) and Humidity - Sensor, future BME280 Temperature,Humidity and Pressure
- Although the sensor is highly accurate (±0.5°C accuracy), you can calibrate the temperature reading using a configuration in the WiFI sensor app
- The device supports dual Wi-Fi mode, allowing it to act as both a Wi-Fi access point and a Wi-Fi client at the same time. A WiFI access point advertises itself through an SSID and can be connected to via any device or computer that has WiFI.
- MQTT Setup page for connection to the MQTT Broker to relay temperature and humidity readings.
- The WiFi Sensor supports 3 MQTT formats; more details are available in (WiFi Pro Devices MQTT Settings)[https://documents.jemrf.com/wifi32s-mqtt.html]. The MQTT connection can be upgraded from a standard non-secure to a secure, trusted connection.
- MQTT Home Assistant Auto-Discovery supported.
- Access Control Option to provide Authorization to save Changes and read hidden settings.
- JST PH2.0 plug option for external 5 volt DC external power, or to provide power to external devices.
- JST PH2.54 3-pin plug for external Pressure Sensor
- JST PH2.54 2-pin Door Sensor, or 3-pin Flow meter.


## Required, but not included:

USB-C cable and USB power supply.
We have USB-C cables at our store, (JemRF Store)[https://www.jemrf.com].

## Installation and Projects

* [Getting Started installation guide](/wifi32s-setup.html)
* [Onboard Sensor Configuration Guide](/wifi32s-config.html)
* [Remote Control Switch Configuration Guide](/wifi32s-remote-relay-switch.html)
* [Door/Window Switch](/wifi32s-switch.html)
* [Pressure Sensor Option](/wifi32s-pressure.html)
* [Offline interfacing with the sensor](/wifi32s-offline.html)
* [Upgrade WiFI Firmware Guide](/wifi32s-update.html)
* [Flow Meter Option Guide](/wifi32s-flowmeter.html)
* [MQTT Settings](/wifi32s-mqtt.html)
* [White Label Options](/wifi32s-whitelabel.html)

## Tech Specs:

* Dimensions 74mm x 55mm x 28mm
* Powered either by a USB-C cable 5VDC.
* Temperature range: -55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C

