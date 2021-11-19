---
title: WiFi RF Wireless Sensor Relay
keywords: communication, communications, basics, basic, radio, spec, specification, protocol
last_updated: Nov 18, 2021
tags:
summary: "This Draft Document describes the basics of WiFi RF Wireless Sensor Relay,or WiFi RF Relay"
sidebar: mydoc_sidebar
permalink: wifirfrelay.html
folder: mydoc
---

The WiFi-RF Gateway provides an alternative to using a Raspberry PI or Arduino computer to receive data from the Wireless RF Sensors, do the Celsius to Fahrenheit  conversion if wanted then send the readings to the PrivateEyePi server.

The WiFi-RF Gateway follows the same process as our WiFi IoT Sensors to connect to the local WiFi and then establishes a connection to the PEP server. Differences between the Raspberry Pi or Arduino functions, is the WiFi-RF Gateway is an Wireless RF receiver only, it can be used to not issue commands to the Wireless RF Sensor.

The WiFi-RF Gateway comes in the same physical case as the WiFi IoT Sensor.
It will track messages for up to 64 Sensors, provide a list of the sensors it is forwarding, the last message forwarded and keep count how many messages it has forwarded from each Sensor.

## Setup Details
The configuration page for the WiFi-RF Relay is very similar to the WiFi IoT Sensor. The added features include the option to send secure (https) or not and if Celsius to Farenheit conversion is wanted.

{% include image.html file="SetupScreen.jpg" alt="WiFi RF Relay Setup Page"%}

## Sensors List
The Sensor List page shows the sensors the relay has forwarded messages to the PEP server. The last message from each sensor received by the gateway with how many messages have been forwarded with a total for that sensor and a grand total of messages forwarded.

{% include image.html file="ActiveDevices.jpg" alt="WiFi RF Relay Sensor List"%}


