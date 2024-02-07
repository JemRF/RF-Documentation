---
title: RF Devices, Getting Started
keywords: getting starter, basics, basic, what, begin, beginner
last_updated: Feb 7, 2024
tags:sidebar: mydoc_sidebar
permalink: getting_started.html
folder: mydoc
---

## 1. Choose a topology

In the introduction we explored the various network topologies. The easiest starting point is the star topology with one or more sensors and one gateway.

## 2. Choose a gateway

There are few options to consider, starting with your choice of micro-controller. Our gateway will work with any micro-controller that has a serial port, so the options are available are many. However we tend to focus on the popular ones:

* [Raspberry Pi](iot_gatewy.html)
* Arduino
* ESP8266, ESP32

### Raspberry Pi

This is a very popular choice, therefore we developed a daughter board that connects to the Raspberry Pi GPIO header. See [IoT Gateway for Raspberry Pi](iot_gateway.html) for more details. A Raspberry Pi is based on a Linux operating system so there is a learning curve required to be able to set up and install the Raspberry Pi, but there is a massive amount of on-line information on Raspberry Pi which makes this a very popular choice. If you have no programming experience then Raspberry Pi is a popular choice because there is plenty on-line material available to get it set up and you can follow our tutorials for PrivateEyePi, Blynk Home Assistant, and others, to connect the IoT Gateway to a cloud service. If you prefer to keep your data local then Raspberry Pi is also a good choice because is is capable of running databases and web servers. Home Assistant is a good option for a local Raspberry Pi based home automation system.

### Arduino

An Arduino typically does not have a network connection, unless you have added on a WIFI or Ethernet module. Therefore the Arduino is more commonly used with a Flex Radio Module as a sensor node.

### ESP8266 / ESP32

These chips manufactured by Espressif can be easily programmed using the Arduino development environment (plus other options) and have built-in WIFI which makes them extremely popular for IoT devices. Couple the ESP8266/ESP32 with a Flex Radio Module and you have a great option for a Gateway. The advantage that these chips have over the Raspberry Pi is they are more single-purpose and don't come with all the overhead of managing a Linux operating system (even though Linux is VERY stable). You can treat the ESP8266/ESP32 as an appliance. The down side of this option is it is purely a Gateway to a cloud service and is not typically used to store data or act as a web server. However for more advanced users you can configure the ESP8266/ESP32 as a web-server and also store a limited amount of data in the local flash or SPIFFS storage or external SD card.

## 3. Choose a sensor

See the products section for a list of all the sensors available. The sensors come pre-configured with default settings and a random device-id. If the device-id is the same as one of your existing sensors then you will need to change the device-id to a unique number otherwise you will receive sensor data against the same ID. When you purchase sensors from us you have the option of leaving a comment where you can ask us to avoid certain device-id's you already have. Once you power up the sensor it will automatically start transmitting data to the gateway. Depending on the sensor there may be specific set-up steps you need to take. Refer the product documentation of the specific sensor for more details.

### Sensor Types

We have three main types of sensors:

1. A range of battery powered RF devices with built-in sensors that are "plug-in-and-play" like temperature, humidity and pressure. These sensors come in 1 1/4" x 1/2" and 1 3/4" x 3/4" form factor case sizes.
2. A range of battery powered RF devices with external sensors that need a moderate amount of building (basic soldering). All parts are included. These sensors come in 1 1/4" x 1/2" and 1 3/4" x 3/4" form factor case sizes.
3. A RF development module called the Flex Radio Module. This is a multi-purpose radio that can be use as a IoT gateway or as a sensor node. It requires configuration and your own development and integration to a micro-controller or external sensors. The Flex Radio Module can plug into a breadboard and is best suited for bread board prototyping and development.

Refer the products section of the documentation for more details on all of the above sensor types.


### 4. Choose a battery

There are lots of CR2032 lithium “coin" battery manufacturers, so a common question is which is better?  Choosing one to use can be important depending on usage. We tested the current CR2032 batteries sold on Amazon to see if one was better than another. While the results are statically subject to a small sampling error, the analysis implies that there is a base consistency between them.  Meaning, regardless of price, they all should last well over a year or more.  We did fine a few that were 25% to 40% better.  Our analysis and testing results is at [CR2032 Battery Testing](cr2032_battery_testing.html).
