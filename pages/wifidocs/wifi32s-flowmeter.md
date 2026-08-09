---
title: WiFi Sensor Pro Switch
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Dec 10, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-flowmeter.html
folder: wifidoc
---
## Introduction
The WiFi S32 Sensor support a digital interface that can be used for an external flow meter. A 3-pin JST 2.54 connector provides 3.3V, signal and ground.

This configuration guide explains how to use the digital interface to sense to use and measure fluid flow with an external flowmeter. The digital flowmeter counts rotations per minute.\
When enabled, the Sensor Config page will show an additional sensor called "FlowMeter" with a value of counts per minute or gallons per minute. There is a new control field use the calibrate tne counts per minute to gallons per minute. When the contol field is 0 the displayed value is counts per minute.

The options include options for multiple sensors including up to 4 external temperature sensors at lengths from 1 m to 5 meters, all at the same time.  The Sensor an interface for a remote digital flow sensor.

The JemrRF S32 WiFi Sensor can support multiple sensor types concurrently, reducing the cost of various sensors in a single location.

## Quick Start
When purchased the S32 Sensor will have a 3 pin JST 2.54 connector installed and a 6 inch 3 wire with connector to connect to the external flowmeter sensor.

## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any Wi-Fi device (e.g., PC, phone, tablet).
- Uses your local 2.4 GHz WiFi to access the Internet
- Cyclic temperature transmission mode with configurable send interval
- MQTT Setup page for connection to the MQTT Broker to relay temperature and humidity readings.
- The WiFi Sensor supports 2 MQTT formats; more details are available in WiFi Gateway MQTT Explained. The MQTT connection can be upgraded from a standard non-secure to a secure, trusted connection.
- Access Control Option to provide Authorization to save Changes and read hidden settings.
- JST PH2.0 plug option for external 5 volt DC external power, or to provide power to external devices.

