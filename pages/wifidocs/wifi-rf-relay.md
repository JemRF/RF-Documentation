---
title: WiFi Wireless Gateway
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Jan 1, 2024
tags:
summary: "This Document describes the basics of the WiFi Wireless Gateway"
sidebar: wifi_sidebar
permalink: wifirfrelay.html
folder: mydoc
---
## Introduction
The WiFi Wireless Gateway (WiFi Gateway) receives messages from the Wireless sensors and sends them to the PrivateEyePi or JemRF Monitoring service. This eliminates the need for a Raspberry PI computer and all that extra overhead. The Gateway provides an easy to use tool to get your wireless sensors online free of configuring and programming a computer first.<br />

The WiFi Gateway is in the same physical case as the current WiFi IoT Sensors.
 * Follows the same setup process as our WiFi IoT Sensors to connect to the local WiFi.
 * It has option to send Celsius to Fahrenheit readings.
 * Using a USB-mini connector for power.
 * It provides a Sensor List overview page to show all the sensors it is tracking and their last value.

{% include image.html file="wirelessgateway.png" alt="WiFi Gateway Case" width="200px"%}

## Tech Specs
* Dimensions 74mm x 55mm x 28mm
* Powered either by USB Mini cable and USB power supply, or battery connection (2.5V to 3.5V) via the 2 pin battery connection plug
* Upgrades are done over the air using the Update button or can be done manually done using a 3.3V FTDI cable


## Setup Details
The configuration page for the WiFi Gateway is very similar to the WiFi IoT Sensor.
You can configure the Wireless Gateway using any device that supports WiFi and an internet browser. In this example we will use a desktop computer.
Click here for the [Details Setup Guide](wifi-rf-gw-setup.html)

## MQTT Details
* Easy to configure web interface.
* Connects to MQTT Broker with or without a username or password.
* Tested with Mosquito Docker brokers and Emqx public broker.
* JemRF provides an MQTT Broker for customers.

[Click here for details on the JemRF MQTT format with examples](gatewaymqtt.html)

## Firmware Updates
The Gateway is normally updated over the Internet.
[Click here for Illustrated manual updating instructions](wifi-gw-update.html)

## Mounting Instructions
Mount the Gateway in a vertical position with the USB connector down. There is a mounting hold on the back for this. Do not mount against a metal wall as that can block the WiFi and RF signals.

