---
title: JemRF WiFi Pro Devices MQTT Settings
keywords: Gateway, mqtt
last_updated: May 18, 2026
tags:
summary: "This page is to show how to setup MQTT on the WiFi Gateway and Node-RED"
sidebar: wifi_sidebar
permalink: wifi32s-mqtt.html
folder: wifidocs
---

# JemRF WiFi Wireless Gateway Pro and WiFi Sensor Pro MQTT Options

The JemRF WiFi Pro have all the same features of our previous WiFi devices including the built-in MQTT Client. It supports the same MQTT features as the Smart Gateway, WiFi Gateway, and the older WiFi Sensors.  They can all send data to the Monitoring Server, which will store and display the readings on the user's Dashboard. They can also connect to a MQTT Broker and publish the sensor readings.  They send to both at the same time, or just send to the Server or the Broker. You can now use tools like Node-Red to build your own monitoring displays.\
The Pro series also has an option that supports your Home Assistant Server using Home Assistant MQTT Auto Discovery.\
The Pro series also does a CheckIn on MQTT start with optional checkin setting. The Checkin includes the WLAN IP and MAC address to support troubleshooting areas where more than one sensor might be installed.

The settings for publishing sensor readings to an MQTT broker are configured on the MQTT Detail Tab, as shown in Figure 1.


<img src="images/jemrf32smqttbase.jpg" width="425"/>
**Figure 1  MQTT Details Setup.**

## Getting Started
Click the MQTT tab and enter the MQTT Broker, in my case, my local server, and the MQTT port. For me, the standard MQTT port is used. Next is the optional Username and Password.

Like the JemRF Pro series come preset to Port 1883 and is configured to use the JemRF Broker. But also supports secure connections on the standard port 8883 or other user defined ports. The secure connection will show Not Secure, Secure but not Trusted (if the digital certificates are self signed) and Secure Trusted if the certificates are valid. \
The default username is jemrf, and the default password is mqtt4jemrf.  If you want a private account, contact sales @ jemrf.com.
The JemRF WiFi Sensor can also make a Secure Connection. If the port numbers are 4000 or higher, the Sensor will attempt to make a Secure and Trusted Connection. If the Secure and Trusted fails, it will try a Secure and UnTrusted. Untrusted is caused when the site Certificate is not current or cannot be validated. A typical Example is using a self-signed certificate. A Secure, encrypted connection is made, but because the certificate cannot be validated, it is flagged as Untrusted. As shown in Figure 2.

<img src="images/jemrf32smqttsecnt.jpg" width="425"/>
**Figure 2, MQTT Connected, encrypted, but the server is not Trusted**


## Publishing Format
Using the MQTT standard protocol, the Gateway will publish data to the broker using the subscription that is the combination of the Gateway Name and the sensor message.
-Subscription
Using the Gateway shown in Figure 1, the Gateway name is JRF03516124.
Using the sensor shown in Figure 2


## MQTT Formats
### JemRF
This is our original format designed to support the RF sensors with the WiFi Wireless Gateway.  It is now also used by the WiFi Sensor./
All messages are limited to each sensor resulting in a discrete MQTT message for each sensor. The Temperature and Humidity sensor is a single sensor so messages include both temperature and humidity in one message. All other sensors are discrete readings.

The Gateway or the WiFi Sensor default topic is: [JEM {Gateway Id}] or [PEP {PEP Id}]/

### MQTT Payloads
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

With Payload for temperature only (Gateway or Sensor) with readings set to Fahrenheit.

[probe id] = [{"temperature":"78.4"},{"unit_of_measurement":"F"}]

.. For WiFi Sensors with multiple probes, the above format is repeated for each probe.


#### Sensor With JSON Payload for Temperature & Humidity sensor:

[probe id] = [[{"temperature":"80.42","unit_of_measurement":"F"}],[{"humidity":"53.10","unit_of_measurement":"%"}]]

{% include note.html content="For the WiFi unit with the Temperature and Humidity Sensor, the Probe Id is the Device Id."%}

#### Contact Payload 
The contact state is 0 for Off and 1 for On.\
Example Relay message

[{"contact":"0","unit_of_measurement":"State"}]

### MQTT Home Assistant Auto Discovery
This option formats the messages for Home Assistant. To assist auto discovery to work, the data payloads are JemRF type messages. Using the example of JemRF device JEMCC7DC0A28DCC with a temperature and humidity sensor, plus a flow meter sensor on the host board with a device ID CC7DC0A28DCC. There are three sub-categories under the device ID, one for Humidity, one for Temperature and one for a Flow meter.\
homeassistant 
homeassistant/sensor
homeassistant/sensor/CC7DC0A28DCC
homeassistant/sensor/CC7DC0A28DCC/humidity
homeassistant/sensor/CC7DC0A28DCC/humidity/config
```json
{"device":{"identifiers":["JEMCC7DC0A28DCC"],"name":"JemRF Sensor JEMCC7DC0A28DCC","model":"WiFi Sensor","mf":"JemRF"},"device_class":"humidity","state_topic":"JEMCC7DC0A28DCC/CC7DC0A28DCC/HUM","name":"Humidity","unique_id":"CC7DC0A28DCCHumidity","state_class":"measurement","unit_of_measurement":"%","availability_topic":"JEMCC7DC0A28DCC/CheckIn","payload_available":"online","payload_not_available":"offline"}
```
homeassistant/sensor/CC7DC0A28DCC/temperature/config
```json
{"device":{"identifiers":["JEMCC7DC0A28DCC"],"name":"JemRF Sensor JEMCC7DC0A28DCC","model":"WiFi Sensor","mf":"JemRF"},"device_class":"temperature","state_topic":"JEMCC7DC0A28DCC/CC7DC0A28DCC/TMPA","name":"Temperature","unique_id":"CC7DC0A28DCCTemperature","state_class":"measurement","unit_of_measurement":"°F","availability_topic":"JEMCC7DC0A28DCC/CheckIn","payload_available":"online","payload_not_available":"offline"}
```
homeassistant/sensor/CC7DC0A28DCC/flow/config
```json
{"device":{"identifiers":["JEMCC7DC0A28DCC"],"name":"JemRF Sensor JEMCC7DC0A28DCC","model":"WiFi Sensor","mf":"JemRF"},"device_class":"volume_flow_rate","state_topic":"JEMCC7DC0A28DCC/CC7DC0A28DCC/FLOW","name":"Flow","unique_id":"CC7DC0A28DCCFlow","state_class":"measurement","unit_of_measurement":"gal/min","value_template":"{{ value | regex_replace('[^0-9.-]', '') }}","suggested_display_precision":2,"availability_topic":"JEMCC7DC0A28DCC/CheckIn","payload_available":"online","payload_not_available":"offline"}
```
with payload data in the form: \
JEMCC7DC0A28DCC/CC7DC0A28DCC
HUM = 62.02
TMPA = 76.15
FLOW = 0.00

This will let MQTT Auto Discover the Sensors and present them as a single device with multiple sensors without any YAML code.

<img src="images/jemrf-mqtt-homeassistant-exp.jpg" width="425"/>
**Figure 2, MQTT Device listing