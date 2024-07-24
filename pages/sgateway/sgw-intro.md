---
title: "JemRF Smart Gateway"
keywords: getting started introduction, Wifi Jemrf, Gateway, rf Sensor
last_updated: July 23, 2024
sidebar: wifi_sidebar
permalink: sgw-intro.html
summary: JemRF Smart Gateway.
---

## Introduction to the JemRF Smart Gateway

The JemRF Smart Gateway is designed for increased data security by capturing and storing sensor data. It adds a time stamp and logs all measurements, keeping them until they are successfully reported to the monitoring server.

It can operate without an Internet connection communicating with a private network server. It provides full management and monitoring capabilities to provide full control over its features and present the internal health of both the operating firmware and hardware.

## Features
The Smart Gateway has expanded MQTT support with the addition of the SparkPlug B MQTT message protocol. It can detect and report operational issues to an MQTT Broker and provide an external open/close contact reflecting the gateway's health.

Data logging and storage of samples eliminate data loss if the network connection to the server is lost. When the connection is restored, the data captured while the network or server is down can be backfilled.

The hardware features provide Power over Ethernet or from a USB-C power source.

The unit has three LEDs to indicate the State of the Server, the status of the connection to the Server, and the status of the MQTT Broker.

Additional features include an internal battery clock that allows all the Gateways to know what time it is on power up or if it can not reach a Network time server. There is also an option to enter local time manually.

The Smart Gateway can run standalone without connecting to a remote server or MQTT Broker. At the bottom of the Sensor List is an option to download today's readings or schedule sending end-of-day readings to an SFTP or Windows share.

The Smart Gateway provides an internal local WiFi Hotspot on first use and setting up the Gateway.

Each form guides the user when making changes, by turning yellow the field that has new information as well as the Save button for those changes will turn Yellow. This provides feedback and change is requested but has not been completed.

<img src="images/sgw-frontview.png" width="425"/>

## Controlling the Smart Gateway
The system control and health user interface uses an internal Web server. Once connected to the Gateway, there are four primary detail settings tabs.

The initial tab is [Setup Details](/sgw-setup.html) for basic settings.

The [Network Details](/sgw-network.html)  for network features and services.

The [Sensor List](/sgw-sensorlist.html)  tab shows the last message from each sensor is displayed.

The [MQTT Settings](/sgw-mqtt.html)  tab is for entering the address of the MQTT Broker and needed credentials.

## External Connections
The image below shows the Smart Gateway Interface Panel.
There is the option for USB-C Power and the physical Ethernet Interface.
If purchased the Ethernet interface can provide power when connected to a POE switch.

If purchased there is a the dry contact interface to alert and external facility control systems the Gateway is On, Off or in Failed State.
- The Blue Online is connected to the Common if the Gateway is working correctly.
- The Orange Off/Failure is connected to Common if the Gateway is powered Off or there is an internal Alarm.

<img src="images/sgw-interface.png" width="425"/>


