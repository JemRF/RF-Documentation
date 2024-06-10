---
title: "JemRF WiFi Devices"
keywords: getting started introduction, Wifi Jemrf, Gateway, wifi Sensor
last_updated: Jan 30, 2024
sidebar: wifi_sidebar
permalink: wifi_intro.html
summary: JemRF WiFi Devices.
---

## Introduction to WiFi Devices

### [WiFi Sensor](wifi_iot.html)
The WiFI Sensor uses the local 2.4G WiFi to connect to the Internet and the remote Monitoring Services.  It an also be queried locally using the internal Sensor configuration page or the /temp command.

There are several configuration for the WiFi Sensor, plus DIY options.
#### Temperature Sensor
The Sensor comes with different digital temperature sensors of highly accurate and consistent readings using the Dallas DS18B20 sensor.
##### Internal Sensor
This configuration has the DS18B20 inside the case for monitoring temperatures around the unit.
##### External Sensor
This configuration uses the DS18B20 at the end of a 1 meter or 2 meter cable with up to 4 sensors managed by one base station.  Note: With multiple sensors, all sensors have to be the same length.
#### Temperature and Humidity Sensor
This configuration uses an Internal DHT22 or External DHT22 to measure temperature and humidity.
#### DIY Options
For the experimenter there are 8 GPIO pins that can be used as switch contacts or to control external devices. Examples are on the JemRF Projects site.
##### Remote Control Relay
This kit provides a 5v relay that can be turned on and off by one of the GPIO pins.

[Details on the WiFI Sensor](wifi_iot.html).

### [WiFi Gateway](wifi-rf-relay.html)
The WiFi Gateway provides a bridge between the private Wireless RF environment and the Internet using the local 2.4G WiFi.
The Gateway will capture the messages from our RF Sensors and send them to the monitoring Server.
In addition to sending the messages to the monitoring server, it can forward messages to an MQTT broker for to allow custom monitoring at multiple locations at the same time.

[Details on the Gateway](wifi-rf-relay.html).

