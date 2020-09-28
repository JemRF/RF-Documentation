---
title: Modes of Operation
keywords: mode, modes, base station, sensor node, type, type 2, IoT Gateway, Gateway, sensor
last_updated: Sep 28, 2020
tags:  
summary: "This page explains modes of operation and how the personality of a RF device can be altered by changing the mode"
sidebar: mydoc_sidebar
permalink: rf_modes.html
folder: mydoc
---

All of the RF modules can be configured to operate in different modes that determine the how the device will operate.

There are three modes of operation:
1. **Gateway Mode.** In Gateway Mode the device acts as Serial to Radio / Radio to Serial converter. Messages sent to the serial port are transmitted through the radio. Incoming messages from the Radio are sent through the Serial port. One of the main characteristics of Gateway Mode is the serial port. The RF Module must be connected to the serial port of the micro-controller (e.g. Raspberry Pi, Arduino, ESP8266/ESP32...). A Gateway is always awake ,cannot be put into a low lower sleep and is usually powered by a dedicated power supply.

2. **Sensor Mode.** When the RF Module is configured in Sensor Mode then it's main job is to read an external sensor (e.g. temperature sensor, door switch sensor etc..) and transmit the sensor reading to the Gateway. The device can sleep which allows it to operate for long periods of time consuming very little power (0.5 µA). The device is awoken either by an external event (e.g. door switch) or an internal timer that causes the device to wake up, send some data, and then go back to sleep. A device in sensor mode can also be attached to an external power supply and be always awake. When the device is awake it can receive and process radio messages. In this way a request/reply messaging model is created where a Gateway requests data from the sensor nodes.

3. **Actuator Mode** When in Actuator Mode the RF MOdule receives a command from another radio device (e.g. a sensor node or a gateway) and executes a physical action, like turning on a light bulb or switching and external circuit. The sensor is always awake in Actuator Mode because it needs to have the radio on at all time listening for in-coming commands. Therefore an external power supply is required for actuators, not batteries. 
 
{% include note.html content="See the [TYPE](types.html) command that is used to configure the mode of operation."%}
