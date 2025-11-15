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
The WiFI Sensor uses the local 2.4G WiFi to connect to the Internet and the remote Monitoring Services.  It can also be queried locally using the internal Sensor configuration page or the /temp command.

There are several configurations for the WiFi Sensor, plus DIY options.
#### Temperature Sensor
The Sensor comes with different digital temperature sensors for highly accurate and consistent readings using the Dallas DS18B20 sensor.
#### Internal Sensor
This configuration has the DS18B20 inside the case for monitoring temperatures around the unit.
#### External Sensor
This configuration utilizes the DS18B20 at the end of a 1-meter or 5-meter cable, with up to four sensors managed by a single base station.  Note: When using multiple sensors, all sensors must be the same length.
#### Temperature and Humidity Sensor
This configuration uses an Internal DHT22 or an External DHT22 to measure temperature and humidity.
#### DIY Options
For the experimenter, there are 8 GPIO pins that can be used as switch contacts or to control external devices. Examples are on the JemRF Projects site.
##### Remote Control Relay
This kit includes a 5V relay that can be controlled by one of the GPIO pins.

[Details on the WiFI Sensor](wifi_iot.html).

### [WiFi Gateway](wifi-rf-relay.html)
The WiFi Gateway provides a bridge between the private Wireless RF environment and the Internet using the local 2.4G WiFi.
The Gateway will capture the messages from our RF Sensors and send them to the monitoring Server.
In addition to sending the messages to the monitoring server, it can forward messages to an MQTT broker for to allow custom monitoring at multiple locations at the same time.

[Details on the Gateway](wifi-rf-relay.html).

## Introduction to S32 Series WiFi devices

Our S32 products are based on the ESP32 processor. These products can make secure connections and support multiple sensors. Support a wide range of sensors to support automation in a single device.

### [S32 WiFi Sensor](wifis32-sensor.html)
The S32 WiFI Sensor uses the local 2.4 GHz WiFi to connect to the Internet and the remote Monitoring Services.  It can also be queried locally using the internal Sensor configuration page or the /temp command.

There are several configurations for the S32 WiFi Sensor: single sensor and multiple sensors.
#### Temperature Sensor
The Sensor comes with different digital temperature sensors for highly accurate and consistent readings using the Dallas DS18B20 sensor.
#### Internal Sensor
This configuration has the DS18B20 inside the case for monitoring temperatures around the unit.
#### External Sensor
This configuration utilizes the DS18B20 at the end of a 1-meter or 5-meter cable, with up to four sensors managed by a single base station.  Note: When using multiple sensors, all sensors must be the same length.
#### Temperature and Humidity Sensor
This configuration uses an Internal HTU21D to measure temperature and humidity.
#### Support remote Pressure Sensor
The sensor can support 5-volt analog pressure sensors from 50 to 500 PSI.
#### Support for Flow Meter
The sensor supports a digital toggle flow meter with calibration for flow counts, ranging from gallons to liters per minute.
##### Remote Control Relays
The S32 WiFi Sensor can control two remote Relays. 

[Details on the S32 WiFI Sensor](wifis32-sensor.html).
