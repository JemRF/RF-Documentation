---
title: WiFi Green House Pro
keywords: communication, communications, greenhouse, homeassistant, home assistant  green house, basic, radio, spec, wifi, sensor
last_updated: Aug 8, 2026
tags:
sidebar: wifi_sidebar
permalink: wifi32s-greenhouse.html
folder: wifidoc
---
## Introduction
The WiFi Green House Pro with internal Temperature and Humidity Sensor, three external moisture sensors and two external temperature sensors.


## Quick Start
Follow the WiFi Green House Pro series devices for connection to the local WiFi.

## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any Wi-Fi device (e.g., PC, phone, tablet).
- Uses your local 2.4 GHz WiFi to access the Internet
- Cyclic temperature transmission mode with configurable send interval
- MQTT Setup page for connection to the MQTT Broker to relay motion, temperature and humidity readings.
- The WiFi Sensor supports 3 MQTT formats; more details are available in [WiFi Pro Devices MQTT Settings](https://documents.jemrf.com/wifi32s-mqtt.html). The MQTT connection can be upgraded from a standard non-secure to a secure, trusted connection.
- MQTT Home Assistant Auto-Discovery supported.
-

## MQTT Details
The MQTT Configuration page is used to set the connection to the MQTT broker, the port and if a secure connection is requested. The default topic starts with the Gateway ID show at the top right.
There is options to change that topic and change the Gateway ID.
For MQTT Auto Discovery there is the option to post CheckIn messages.
There are three data formats the Gateway sends MQTT Messages.
1. Using the JemRF data format using the device ID and value
2. Using a JSON message format using the device ID , value and message type [Temperature, Humidity, State,...]
3. Home Assistant MQTT Auto Discovery which updates the Home Assistant topics with sensor descriptions and post data using the JemRF format.

## Switch Wiring

## Required, but not included:

USB-C cable and USB power supply.
We have USB-C cables at our store, (JemRF Store)[https://www.jemrf.com].

## Tech Specs:

* Dimensions 74mm x 55mm x 28mm
* Powered either by a USB-C cable 5VDC.