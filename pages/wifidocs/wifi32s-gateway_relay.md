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

<img src="gateway-pro-relay.jpeg" alt="WiFi Gateway Pro with Relay Case" width="200px">

## Tech Specs
* Dimensions 74mm x 55mm x 28mm
* Powered either by USB-C.
* Upgrades are done over the air using the Update button.
* Relay contacts for low voltage AC or DC connections. Recommend licensed Electrician for any control applications.

## Features
* Easy to configure web interface. No programming or soldering skills required. You do not need the internet to configure the device. Connect to it directly from any WIFI device (e.g. PC, phone tablet…)
* Supports both Celsius or Fahrenheit temperature conversion
* Powered either by USB-C cable or battery connection (5.0 V) via the 2 pin battery connection plug
* The device supports dual WIFI mode allowing it to be WIFI access point and a WIFI client at the same time. A WIFI access point advertises itself through an SSID and can be connected to via any device or computer that has WIFI.
* The Sensor List tab will show sensor that the WiFi Relay and heard and forwarded to the server. See Example below:
{% include image.html file="wifis32gatewaypro_list.jpg" alt="WiFi Gateway Pro List" %}

## Required, but not included:

* USB-C cable and USB power supply, 1 Amp or greater.

## Setup Details
The configuration page for the WiFi Gateway is very similar to the WiFi IoT Sensor.
You can configure the Wireless Gateway using any device that supports WiFi and an internet browser. In this example we will use a desktop computer.
{% include image.html file="wifis32gatewaypro_setup.jpg" alt="WiFi Gateway Pro Setup" %}
Click here for the [Details Setup Guide](wifi-rf-gw-setup.html)

## MQTT Details
The MQTT Configuration page is used to set the connection to the MQTT broker, the port and if a secure connection is requested. The default topic starts with the Gateway ID show at the top right.
There is options to change that topic and change the Gateway ID.
For MQTT Auto Discovery there is the option to post CheckIn messages.
There are three data formats the Gateway sends MQTT Messages.
1. Using the JemRF data format, i.e. the MQTT Key as seen on the Sensor List with value.
2. Using a JSON message format. i.e. the MQTT Key, value and message type [Temperature, Humidity, State,...]
3. Home Assistant MQTT Auto Discovery which updates the Home Assistant topics with sensor descriptions and post data using the JemRF format.

{% include image.html file="wifis32gatewaypro_mqtt.jpg" alt="WiFi Gateway Pro MQTT Setup" %}

[Click here for details on the JemRF MQTT format with examples](gatewaymqtt.html)

## Relay Configuration
The Gateway Pro Plus Relay settings page provides selection of the sensor to monitor, the action if the value is
above or below, or equal a set value followed by what action to take.
Each Relay has two settings to be applied to the sensor being monitored.
The setup process would use one setting to activate the relay and the second to deactivate the relay.

In the following Relay setup screen that Relay 1 is on and the setting are using Sensor ID J023TM, monitoring the reading to see if it exceeds 77. In the example sensor J023TM has a value of 78.01 which is above 77 so the relay
has been turned on. If the reading drop below 76 the relay will be turned off.
Relay 2 is also on, and is monitoring temperature sensor 55TMPC. The last value for 55TMPC was 76.55 which is above 76 and not less that 75 so Relay 2 is on.

{% include image.html file="wifis32gatewaypro_relay.jpg" alt="WiFi Gateway Pro Relay Setup" %}

## Sensor List
The Sensor List is all the RF Sensors the Gateway hears. The display shows the sensor ID the message types which are the MQTT keys, the last value how many times the Gateway has heard messages from each sensor and the timestamp for the last message received.

{% include image.html file="wifis32gatewaypro_list.jpg" alt="WiFi Gateway Pro Relay Sensor List" %}

## Firmware Updates
The current WiFi Gateway Plus Version is displayed at the bottom of each page. The firmware of the RF Transceiver is also show with the channel the Gateway is on. The default channel is zero (0).

The WiFi Gateway Plus is updated from the Internet. When a new update is available a message will appear on the Setup Details Page.

[Click here for Illustrated guide on updating the Gateway](wifi-gw-update.html)

## Switch Wiring
The relays each provide a normally open and normally closed dry contact. Designed for low voltage AC (0-24 vac) or low voltate DC (0-24 vdc). If using for control system contact a Licensed Electrician.

## Mounting Instructions
Mount the Gateway in a vertical position with the USB connector down. There is a mounting hold on the back for this. Do not mount against a metal wall as that can block the WiFi and RF signals.