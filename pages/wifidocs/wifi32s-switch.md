---
title: JemRF ESP32 WiFi Sensor as Switch
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Nov 20, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-switch.html
folder: wifidoc
---
## Introduction
The WiFi S32 Sensor support a digital interface that can be used for an external contact closure using a JST 2.54 2-pin connector.

This configuration guide explains how to use the digital interface to sense the opening and closing 
 like a door/window magnetic switch.\
The sensor configuration page will show a Contact row with value of 0 or 1. When the contacts are closed it is a 0 (zero) and when they are not connected it report a 1 value.
Monitoring.JemRF.com can represent the state as 1/0, open/losed or with an open or closed door graphic or open or closed window icon.

Optional internal and external temperature sensors can be added, as well as an Internal Temperature & Humidity Sensor.

## Quick Start
When ordered with option for external contact switch, the sensor will include a 2 pin JST 2.54 connection and 6 inch connection cable, optional magnetic switch can be ordered.\
The Sensor Configuration screen will display an additional sensor called Contact Sensor and will show a value of 0 or 1. When the contact circuit is connected (Closed) the value is 0. When the circuit is Open the value is 1.

{% include image.html file="jemrf32scontact.jpg" alt="WiFi Sensor Contact Reading"%}

## Switch Wiring

