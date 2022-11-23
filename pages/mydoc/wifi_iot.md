---
title: The Internet Of Things (IOT)
keywords: getting started introduction
last_updated: Mar 27, 2022
tags:
summary: "The Internet Of Things (IOT) is phenomenon sweeping the world at this moment where everyday things (cars, homes, household appliances, plants) are being connected to the IOT where we can monitor, control and alert in ways not possible before."
sidebar: mydoc_sidebar
permalink: wifi_iot.html
folder: mydoc
---

## Internet Of Things (IOT) WIFI Sensor
This versatile device allows you to connect sensors quickly and inexpensively to the internet. It comes with software that enables you to sense temperature and humidity as well as control relay so you can switch things on/off at the touch of a button from your device or computer.

It connects to your WIFI access point so you can  send temperature readings to PrivateEyePi, or another monitoring application. It is fully assembled and requires no soldering. Connect it to power and it will advertise itself as a wireless access point. Configure it through a web browser using its easy to use config application. Once configured it will connect to your WIFI network which will give it access to the internet and the PrivateEyePi server.

## Features:

- Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any WIFI device (e.g. PC, phone tablet…)
- Cyclic temperature transmission mode with configurable send interval
- Supports both Celsius or Fahrenheit temperature readings
- Control up to 8 relays
- Sleep mode allows it to be run from battery power
- Configurable temperature delta threshold allows the device to monitor the temperature and only transmit when the current reading exceeds the previous reading by a configurable amount. This feature is very useful for saving battery power
- Built in error log allows you to review and resolve issues. The error log is stored in the device’s memory and can be viewed through the sensor web app
- Fully programmable using the Arduino or LUA development environments
- DS18B20 temperature sensor is used to detect the temperature Measures temperatures from -55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C
- Although the sensor is highly accurate (±0.5°C accuracy) you can calibrate the temperature reading using a configuration in the WIFI sensor app
- The device supports dual WIFI mode allowing it to be WIFI access point and a WIFI client at the same time. A WIFI access point advertises itself through an SSID and can be connected to via any device or computer that has WIFI.
- Control up to 8 relay switches either from the device's dashboard, vial URL or via PrivateEyePi rules

## Required, but not included:

Mini USB cable and power supply (older cell phones used mini USB, so you may already have one in the bottom of a drawer). -5V to 7V power supply. Any USB power supply will work.
Battery pack (optional)

## Installation:

Getting Started installation guide
Temperature and Humidity Configuration Guide
Remote Control Switch Configuration Guide
Door/Window Switch
Advanced setup options described here
This guide shows you how to interface to the sensor
Upgrade WIFI Firmware Guide

## Tech Specs:

Demensions 74mm x 55mm x 28mm
Powered either by USB Mini cable (4.5V DC to 7V DC input) or battery connection (2.5V to 3.5V) via the 2 pin battery connection plug
-55°C to +125°C. Fahrenheit equivalent is -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C
Can be programmed using Arduino or LUA development environments
Upgraded using a 3.3V FTDI cable (recomended while the product is in BETA)
8 GPIO ports avalaiable through the 16 pin header
Supports SPI serial interface
## Board Layout:

Click on image for bigger picture