---
title: "JemRF WiFi Devices"
keywords: getting started introduction, Wifi Jemrf, Gateway, wifi Sensor
permalink: wifi_intro.html
summary: JemRF WiFi Devices.
---

## Introduction to WiFi Devices

### WiFi Sensor
The WiFI Sensor uses the local WiFi to connect to the Internet and the remote Monitoring Services.  It an also be queried locally using the internal Sensor configuration page or the /temp command.

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

### WiFi Gateway
The WiFi Gateway provides a bridge to capture messages from our RF Sensors and forward them to the monitoring Server.
It forwards messages to the monitoring server and can forward data messages to an MQTT broker for external custom monitoring.

[Details on the Gateway](wifi-rf-relay.html).

