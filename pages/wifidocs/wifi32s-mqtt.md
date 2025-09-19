---
title: JemRF ESP32 WiFi Devices MQTT Settings
keywords: Gateway, mqtt
last_updated: Sept 20, 2025
tags:
summary: "This page is to show how to setup MQTT on the WiFi Gateway and Node-RED"
sidebar: wifi_sidebar
permalink: wifi32s-mqtt.html
folder: wifidocs
---

# JemRF WiFi Wireless Gateway and WiFi Sensor MQTT Options

The JemRF ESP32 WiFi Sensor have a built-in MQTT Client. It supports the same MQTT features as the Smart Gateway and WiFi Gateway. They all can send to the Monitoring Server for it to store and display readings on the use Dashboard. They can also  connect to a MQTT Broker and publish the sensor readings.  It can do both at the same time, or just send to the Server or the Broker. You can now use tools like Node-Red to build your own monitoring displays

The settings to publish the sensor readings to an MQTT broker are done on the MQTT Detail Tab as seen in Figure 1.


<img src="images/jemrf32smqttbase.jpg" width="425"/>
**Figure 1  MQTT Details Setup.**

## Getting Started
Click the MQTT tab and enter the MQTT Broker, in my case my local server, the MQTT Port, for me is the standard MQTT Port. Next is the optional Username and Password.

Like the JemRF Gateways, the ESP32 WiFi Sensor come preset to Port 1883 and is configured to use  the JemRF Broker. The default username is jemrf and mqtt4jemrf as the default password.  If you want an private account contact sales @ jemrf.com.
The JemRF WiFi Sensor can also make Secure Connection. It the port numbers are 8000 or higher, the Sensor will attempt to make a Secure and Trusted Connection. If the Secure and Trusted fails it will try a Secure and UnTrusted, UnTrusted is caused went the site Cerificate is not current or can not be validated. A common Example is using a self-signed certificate. A Secure encrypted connection is made but because the certificate can not be validated it is flagged as UnTrusted. As show in Figure 2.

<img src="images/jemrf32smqttsecnt.jpg" width="425"/>
**Figure 2, MQTT Connected encryupted but server not Trusted**


## Publishing Format
Using the MQTT standard protocol the Gateway will publish data to the broker using the subscription that is the combination of the Gateway Name and the sensor message.
-Subscription
Using the Gateway shown Figure 1, that Gateway name is JRF03516124.
Using the sensor show in Figure 2


## MQTT Formats
### JemRF
This is our original format designed to support the RF sensors with the WiFi Wireless Gateway.  It is now used by the WiFi Sensor as well.

The Gateway or the WiFi Sensor default topic is: [JEM {Gateway Id}] or [PEP {PEP Id}]/

#### MQTT Payloads
[JemRF ID]
- If Temperature Sensor Only

- - [Sensor Id]
- - - TMPA = 56.07

- If Temperature & Humidity Sensor
- - [Sensor Id]  (Note for the dual sensor, the Sensor Id is the PEP Id)
- - - TMPA =66.23
- - - HUMD = 54.2

### MQTT JSON
This format is a generic format and compatible with Home Assistant servers.

The default topic is: [Sensor Id]/

With Payload for temperature Only (Gateway or Sensor) with readings set to Fahrenheit.

[probe id] = [{"temperature":"78.4"},{"unit_of_measurement":"F"}]

.. For WiFi Sensors with multiple probes, the above format is repeated for each probe.


#### Sensor With Payload for Temperature & Humidity sensor:

[probe id] = [[{"temperature":"80.42","unit_of_measurement":"F"}],[{"humidity":"53.10","unit_of_measurement":"%"}]]

{% include note.html content="For the WiFi unit with the Temperate and Humidity Sensor, the Probe Id is the Device Id."%}