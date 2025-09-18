---
title: JemRF ESP32 WiFi Sensor with Remote Relay
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Sept 20, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-remote-relay-switch.html
folder: wifidoc
---
## Introduction
Configuration guide for JemRF device: - [WIFI Remote Control Switch](https://www.jemrf.com/collections/wifi-enabled-devices/products/wifi-controlled-relay-switch-internet-of-things-iot)

Connecting a relay switch to the WIFI controller.

{% include image.html file="wifi-remote-relay.jpg" alt="WiFi Remote Control Relay Kit"%}

WARNING : Mains electricity can kill if you are careless or lacking in knowledge of how to connect high voltage.

The WIFI Relay is capable of switching up to 8 relays. Each relay is connected to the WIFI controller via three wires as shown in figure 1.

{% include image.html file="WIFI Relay Wiring Diagram.png" alt="WiFi Relay Diagram"%}
Figure 1 - Wiring diagram to connect a relay switch to the WIFI controller


## Configuring the WIFI controller.

Before you start this configuration ensure you have already followed the getting started guide that shows you how to connect your device to your WIFI router and to the PrivateEyePi server (optional).

Open up the WIFI configuration screen by browsing to your WIFI devices IP address in a browser and then click on the Sensor Config menu. If you want to be able to control the device using your PrivateEyePi dashboard then click on the "Allow external control" check box as shown below.

{% include image.html file="allow external control.png" alt="WiFi allow external control"%}

All the other settings in the above image may vary to yours depending on the type of sensor you have and what settings you configured earlier in the Getting Started Guide.

Security Note:
The "Allow external control" option will allow you to switch things on/off from the WWW outside your home network. Communications to the outside world are encrypted, but it is important to keep your Token (from the Login Details Screen) secret. Anyone with your token will be able to control the GPIO ports of your WIFI controller. If you suspect your token has been compromised then you can deny access to the device by de-selecting the "Allow external control". 

You can switch the relay using the following URL to your device:

This will switch Relay 1 off:
http://192.168.2.99/relayoff?relay=1

This will switch Relay 2 on:
http://192.168.2.99/relayon?relay=2

However this will only work if you are on your local home network. You will not be able to do this from the WWW.

Troubleshooting tips

What do I do if the control dashboard says "Connecting"?
This is usually caused by an incorrect PrivateEyePi token configured on the WIFI controller. Copy and paste the token from the www.privateeyepi.com User Menu to the Login Details menu on the WIFI controller. Your configuration screen must say "PEP: Connected" at the top.
