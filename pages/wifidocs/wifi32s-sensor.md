---
title: The JemRF ESP32 WIFI Sensor Version 2 Introduction
keywords: getting started introduction
last_updated: Sept 20, 2025
tags:
summary: "The Internet Of Things (IoT) is where everyday things (cars, homes, household appliances, plants) are being connected to the Internet where we can monitor, control and alert in ways not possible before. This document describes our WiFi Sensor and its place in the IoT Universe."
sidebar: wifi_sidebar
permalink: wifi32s-sensor.html
folder: wifidocs
---

## WiFI Sensor Version 2 is called the JemRF ESP32 WiFi Sensor

![WiFi Sensor Case](images/wifisensorcase.jpg "WiFi Case") 

The JemRF ESP32 WiFi Sensor is a more that next Version 2 is expands the versatile device features of the older devicw with a larger collection of sensor options ready to go in simple plug and go for quickly and inexpensively Updates to the cloud. It comes with software for onboard temperature and humidity as well simple onboard temperature or connect to temperature probles from 1 to 5 meters all at the same time. There are onboard switches to control external relays so you can switch things on/off at the touch of a button from your device or computer.
The Sensor also supports remote pressure sensors from 10 to 500 psi. Has interface for remote digital flow sensor or door sensor.

The JemrRF ESP32 WiFi Sensor can support many of the different sensor types concurrently reducing cost for mutiple sensors in one location.

It connects to your WiFI access point so you can  send temperature readings to [monitor.jemrf.com](https://monitor.jemrf.com), or another monitoring application. As well as MQTT Support for forward readings to an MQTT broker. It is fully assembled and requires no soldering. Connect it to power and it will advertise itself as a wireless access point. Configure it through a web browser using its easy to use config application. Once configured it will connect to your WiFI network which will give it access to the internet and the JemRF Monitoring server, your own server or run on local network with custom software.

## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any WiFI device (e.g. PC, phone tablet…)
- Uses your local 2.4G WiFi to access the Internet
- Cyclic temperature transmission mode with configurable send interval
- Supports both Celsius or Fahrenheit temperature readings
- DS18B20 temperature sensors (Onboard or Extended) are used to measure temperatures from -55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C
* * Note: The operating temperature for the WiFi Temperature sensor is -30F to +125.6F, -34C to 52C
- Supports HTU21D Temperature and Humidity Sensor, future BME280 Temperature,Humidity and Pressure
- Although the sensor is highly accurate (±0.5°C accuracy) you can calibrate the temperature reading using a configuration in the WiFI sensor app
- The device supports dual WiFi mode allowing it to be WiFI access point and a WiFI client at the same time. A WiFI access point advertises itself through an SSID and can be connected to via any device or computer that has WiFI.
- MQTT Setup page for connection to MQTT Broker to relay temperature and humidity readings. The WiFi Sensor support 2 MQTT Format, more detail at [WiFi Gateway MQTT Explained](https://documents.jemrf.com/gatewaymqtt.html). The MQTT connection can be from the standard nonsecure to a secure trusted connection.

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
* Powered either by USB-C cable 5 VDC.
* Temperature range: -55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C

