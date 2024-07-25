---
title: "JemRF Smart Gateway"
keywords: getting started introduction, Smart Gateway Jemrf, Gateway, rf Sensor
last_updated: July 23, 2024
sidebar: wifi_sidebar
permalink: sgw-intro.html
summary: JemRF Smart Gateway.
---

## Introduction to the JemRF Smart Gateway

The JemRF Smart Gateway is designed to enhance data security by capturing and storing sensor data. It adds a timestamp and logs all measurements. It stores the measurements until they have been successfully reported to the monitoring server. It can operate without an internet connection and communicate with a private network server. The Smart Gateway provides total management and monitoring capabilities, offering complete control over its features and displaying the operating firmware's and hardware's internal health.

## Features
The Smart Gateway now supports the SparkPlug B MQTT message protocol, expanding its MQTT capabilities. It can detect and report operational issues to an MQTT Broker and provide an external open/close contact to reflect the Gateway's health.

Internal data logging and storing eliminate potential data loss in case of network connection failure. When the network connection is restored, any data captured while the network was down is backfilled to the cloud service or Server.

The hardware features provide Power over Ethernet (POE) or from a USB-C power source.

The unit has three status LEDs:

- The State of the Server
- The status of the connection to the Server
- The status of the MQTT Broker.

Additional features include an internal battery-powered clock that ensures all the Gateways know the current time upon power up or when they cannot reach a network time server. You also have the option to manually input the local time if necessary.

The Smart Gateway can run standalone without connecting to a remote server or with an MQTT Broker. At the bottom of the Sensor List, there is an option to download today's readings or schedule sending end-of-day readings to an SFTP or Windows share.

The Smart Gateway provides an internal local WiFi Hotspot on first use and setting up the Gateway.

Each form guides the user when making changes, by turning yellow the field that has new information as well as the Save button for those changes will turn Yellow. This provides feedback and change is requested but has not been completed.

<img src="images/sgw-frontview.png" width="425"/>

## Controlling the Smart Gateway
During the initial setup, the Smart Gateway creates a local WiFi hotspot. The system control and health User Interface (UI) form uses an internal Web server, which is accessed using its IP address.

Once connected to the Gateway, there are four primary detail settings tabs.

The [Setup Details](/sgw-setup.html)  tab is for basic settings.
The [Network Details](/sgw-network.html)  tab is for network features and services.
The [Sensor List](/sgw-sensorlist.html) tab displays the most recent message from each sensor.
The [MQTT Settings](/sgw-mqtt.html) tab is for entering the address of the MQTT Broker and necessary credentials.

Each tab guides the user when making modifications. The forms indicate changes by turning the edited field and the Save button yellow, signaling that the changes have not been saved.

## External Connections
The image below shows the Smart Gateway Interface Panel. It offers an option for USB-C Power and an Ethernet Interface, which can provide power when connected to a POE switch.

An optional feature is a dry contact interface to alert external facility control systems when the Gateway is On, Off, or in a Failed State.
- The Blue Online is connected to the Common if the Gateway is working correctly.
- The Orange Off/Failure is connected to Common if the Gateway is powered Off or there is an internal Alarm.

<img src="images/sgw-interface.png" width="425"/>


