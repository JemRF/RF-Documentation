---
title: WiFi RF Wireless Sensor Relay
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Nov 18, 2021
tags:
summary: "This Document describes the basics of WiFi RF Wireless Sensor Relay,or WiFi-RF Relay"
sidebar: mydoc_sidebar
permalink: wifirfrelay.html
folder: mydoc
---

The WiFi-RF Relay provides an alternative to using a Raspberry PI or Arduino computer to receive data from the Wireless RF Sensors, and do the Celsius to Fahrenheit conversion, before sending the readings to the PrivateEyePi server.

The WiFi-RF Relay follows the same process as our WiFi IoT Sensors to connect to the local WiFi and then establishes a connection to the PEP server. <br />
Unlike using a Raspberry Pi or Arduino provides extra functions, internal sensors, and it can be used to issue commands to the Wireless RF Sensor. <br />
The WiFi-RF Relay is an Wireless RF receiver only,  it can not be used to send commands to RF Sensors.

The WiFi-RF Relay will be in the same physical case as the current WiFi IoT Sensor.  Using a mini-USB connector for power.

{% include image.html file="wifi-relay-case.jpg" alt="WiFi RF Relay Case"%}


## Setup Details
The configuration page for the WiFi-RF Relay is very similar to the WiFi IoT Sensor. An added features include the option to establish a secure/encrypted (https) connection to the server or not.  It also supports the option for Celsius to Farenheit conversion.

{% include image.html file="SetupScreen.jpg" alt="WiFi RF Relay Setup Page"%}


## Sensors List
The Sensor List page shows the sensors the relay has forwarded messages to the PEP server. The last message from each sensor received by the gateway with how many messages have been forwarded with a total for that sensor and a grand total of messages forwarded.

It will track messages for up to 64 Sensors.

{% include image.html file="ActiveDevices.jpg" alt="WiFi RF Relay Sensor List"%}


