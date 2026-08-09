---
title: JemRF WiFi Sensor Pro with Contact
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Nov 20, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-switch.html
folder: wifidoc
---
## Introduction
The WiFi Sensor Pro support a digital interface that can be used for an external contact closure using a JST 2.54 2-pin connector.

This configuration guide explains how to use the digital interface to sense the opening and closing
 like a door/window magnetic switch.\
The sensor configuration page will show a Contact row with value of 0 or 1. When the contacts are closed it is a 0 (zero) and when they are not connected it report a 1 value.
Monitoring.JemRF.com can represent the state as 1/0, open/losed or with an open or closed door graphic or open or closed window icon.

The options include options for multiple sensors including up to 4 external temperature sensors at lengths from 1 m to 5 meters, all at the same time.  The Sensor also supports remote pressure sensors from 10 to 500 psi. Has an interface for a remote digital flow sensor.

The JemrRF WiFi Sensor Pro can support multiple sensor types concurrently, reducing the cost of various sensors in a single location.

## Quick Start
When ordered with option for external contact switch, the sensor will include a 2 pin JST 2.54 connection and 6 inch connection cable, optional magnetic switch can be ordered.\
The Sensor Configuration screen will display an additional sensor called Contact Sensor and will show a value of 0 or 1. When the contact circuit is connected (Closed) the value is 0. When the circuit is Open the value is 1.

{% include image.html file="jemrf32scontact.jpg" alt="WiFi Sensor Contact Reading"%}

## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any Wi-Fi device (e.g., PC, phone, tablet).
- Uses your local 2.4 GHz WiFi to access the Internet
- MQTT Setup page for connection to the MQTT Broker to relay temperature and humidity readings.
- The WiFi Sensor supports 2 MQTT formats; more details are available in WiFi Gateway MQTT Explained. The MQTT connection can be upgraded from a standard non-secure to a secure, trusted connection.
- Access Control Option to provide Authorization to save Changes and read hidden settings.
- JST PH2.0 plug option for external 5 volt DC external power, or to provide power to external devices.
- JST PH2.54 2-pin Door Sensor.

## Switch Wiring

## Tech Specs:

* Dimensions 74mm x 55mm x 28mm
* Powered either by a USB-C cable 5VDC.