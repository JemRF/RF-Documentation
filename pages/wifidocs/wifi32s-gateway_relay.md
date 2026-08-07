---
title: WiFi Wireless Gateway Pro Plus Relay
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor, gateway, RF Gateway, WiFi Gateway
last_updated: Aug 7, 2026
tags:
sidebar: wifi_sidebar
permalink: wifi32s-gateway_relay.html
folder: mydoc
---

{% include note.html content="Future Release, currently only available on request" %}

## Introduction
The WiFi Wireless Gateway Pro Plus Relay (WiFi Gateway Plus) receives messages from the Wireless sensors and sends them to the JemRF Monitoring service. This eliminates the need for a Raspberry PI computer and all that extra overhead. The WiFi Gateway Plus provides an easy to use tool to get your wireless sensors online free of configuring and programming a computer first.<br />

The WiFi Gateway Plus is in the same physical case as the current WiFi IoT Sensors.
 * Follows the same setup process as our WiFi IoT Sensors to connect to the local 2.4G WiFi Only.
 * It has option to send Celsius to Fahrenheit readings.
 * Using a USB-C connector for power.
 * It provides a Sensor List overview page to show all the sensors it is tracking and their last value.
 * Supports RF4 Sensors, sensors with 4-character device IDs as well as the 2-character IDs.

{% include image.html file="wirelessgateway.png" alt="WiFi Gateway Case" width="200px"%}

## Tech Specs
* Dimensions 74mm x 55mm x 28mm
* Powered either by USB-C.
* Upgrades are done over the air using the Update button or can be done manually done using a 3.3V FTDI cable

## Features
* Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any WIFI device (e.g. PC, phone tablet…)
* Supports both Celsius or Fahrenheit temperature conversion
* Powered either by USB-C cable or battery connection (5.0 V) via the 2 pin battery connection plug
* The device supports dual WIFI mode allowing it to be WIFI access point and a WIFI client at the same time. A WIFI access point advertises itself through an SSID and can be connected to via any device or computer that has WIFI.
* The Sensor List tab will show sensor that the WiFi Relay and heard and forwarded to the server. See Example below:
{% include image.html file="ActiveDevices.jpg" alt="WiFi Gateway Sensor List" %}

## Required, but not included:

* USB-C cable and USB power supply, 1 Amp or greater.

## Setup Details
The configuration page for the WiFi Gateway is very similar to the WiFi IoT Sensor.
You can configure the Wireless Gateway using any device that supports WiFi and an internet browser. In this example we will use a desktop computer.
Click here for the [Details Setup Guide](wifi-rf-gw-setup.html)

## MQTT Details
* Easy to configure web interface.
* Connects to MQTT Broker with or without a username or password.
* Tested with Mosquito Docker brokers and Emqx public broker.
* JemRF provides an MQTT Broker for customers.
* Home Assistant MQTT Auto Discovery option

[Click here for details on the JemRF MQTT format with examples](gatewaymqtt.html)

## Firmware Updates
The current WiFi Gateway Plus Version is displayed at the bottom of each page. The firmware of the RF Transceiver is also show with the channel the Gateway is on. The default channel is zero (0).

The WiFi Gateway Plus is normally updated over the Internet. When a new update is available a message will appear on the Setup Details Page.

[Click here for Illustrated guide on updating the Gateway](wifi-gw-update.html)

## Mounting Instructions
Mount the Gateway in a vertical position with the USB connector down. There is a mounting hold on the back for this. Do not mount against a metal wall as that can block the WiFi and RF signals.