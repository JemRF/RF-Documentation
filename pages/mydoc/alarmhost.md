---
title: Alarmhost API
keywords: interface, integrate, integration, API, message format
last_updated: Sep 28, 2020
tags:
summary: "This page explains the message format from gateways to server."
sidebar: mydoc_sidebar
permalink: alarmhost.html
folder: mydoc
---

## Interfacing JemRF and PrivateEyePi Servers

This is the message format from a JemRF Gateway, WiFi Sensor or RPI running JemRF software.

The server url can be changed to pointing to any server.
There can be a subfolder provided if needed.
What is fixed is the application you connect to and that is alarmhostr.php.

## The message formats:
The message content is in the http url and configured to support parsing with standard Get function.
### WiFi Wireless Gateway
#### Gateway check-in
alarmhostr.php?token=" + String(pep_token) + "&" + "function=27&opcode0=5" + SensorNumber + "&opcode1=" + myIpString+ "&opcode2=" + Version + "&opcode3=" + RSSIIndex

* Token: The JemRF/PrivateEyePi user Token
* function 27  is the WiFI Device Register/Check-in message
* opcode0 is the Gateway Id
* opcode1 is the IP Address of the device
* opcode2 is the Firmware Version
* opcode3 is the RSSI Signal level of the WiFi SSID

#### Sensor Data Message
alarmhostr.php?token=" + (String)pep_token + "&function=" + String(PEP_Function) + "&opcode0=" + opcode0 + "&opcode1=" + opcode1 + "&opcode2=" + opcode2 + "&opcode3=" + opcode3

* Token: The JemRF/PrivateEyePi user Token
* function is message type:
* 37 reading [temperature, humidity, pressure,...]
* opcode0 is the sensor Id
* opcode1 is the Sensor value
* opcode2 is flag for value: 1 == Temperature, 2 == Humidity, 3 == Pressure
* opcode3 is the IP Address of the Unit

* 38 is for contacts/relays with on/off values
* opcode0 is the sensor Id
* opcode1 is the Sensor value (1 or 0)
* opcode2 is flag == 2 is on/off device
* opcode3 is IP Address of unit

* 22 for battery voltage*
* opcode0 is the sensor Id
* opcode1 is the Sensor voltage value
* opcode2 is flag == 2 is voltage
* opcode3 is IP Address of unit



### WiFi Sensor
#### Sensor check-in
alarmhostr.php?token=" + String(pep_token) + "&" + "function=27&opcode0=" + SensorNumber + "&opcode1=" + myIpString+ "&opcode2=" + Version + "&opcode3=" + RSSIIndex

* Token: The JemRF/PrivateEyePi user Token
* function 27  is the WiFI Device Register/Check-in message
* opcode0 is the Gateway Id
* opcode1 is the IP Address of the device
* opcode2 is the Firmware Version
* opcode3 is the RSSI Signal level of the WiFi SSID

#### Temperature & Humidity
alarmhostr.php?token=" + pep_token + "&" + "function=" + function + "&opcode0=" + opcode0 + "&opcode1=" + opcode1 + "&opcode2=" + opcode2 + "&opcode3=" + opcode3 + "&opcode4=" + opcode4

* Token: The JemRF/PrivateEyePi user Token
* function is message type:
* 30 for Temperature and Humidity
* opcode0 is the Sensor temperature value
* opcode1 is flag 1 no Humidity value, 0 Humidity value included
* opcode2 is the sensor Id
* opcode3 is the Humidity value if option1 == 0
* opcode4 is the IP Address of the Unit

#### Send Email
alarmhostr.php?token=" + pep_token + "&" + "function=34"

* Token: The JemRF/PrivateEyePi user Token
* function is message type:

#### Email Alert
alarmhostr.php?token=" + pep_token + "&" + "function=35&opcode1=" + SensorNo + "&opcode0=" + RuleId

* Token: The JemRF/PrivateEyePi user Token
* function is message type:

#### Acknolage Email Update
alarmhostr.php?token=" + pep_token + "&" + "function=36"

* Token: The JemRF/PrivateEyePi user Token
* function is message type:

#### Sned RelayValues
alarmhostr.php?token=" + pep_token + "&" + "function=32&" + strMessage

* Token: The JemRF/PrivateEyePi user Token
* function is message type:

#### Relay Configuration
alarmhostr.php?token=" + pep_token + "&function=28&opcode0=" + SensorNumber + "&opcode1=" + strRelayList

* Token: The JemRF/PrivateEyePi user Token
* function is message type:


### Raspberry Pi
https://www.privateeyepi.com/alarmhostr.php?token="+globals.token+"&function="+str(function)+ "&opcode0=" + opcode0 + "&opcode1=" + opcode1 + "&opcode2=" + opcode2

* Token: The JemRF/PrivateEyePi user Token
* function is message type:
* 37 reading [temperature, humidity, pressure,...]
* opcode0 is the sensor Id
* opcode1 is the Sensor value
* opcode2 is flag for value: 1 == Temperature, 2 == Humidity, 3 == Pressure

* 38 is for contacts/relays with on/off values
* opcode0 is the sensor Id
* opcode1 is the Sensor value (1 or 0)
* opcode2 is flag == 2 is on/off device


