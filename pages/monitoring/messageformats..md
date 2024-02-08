---
title: JemRF Monitoring Message Formats
keywords: communication& communications& relay& basic& radio& spec& wifi& sensor
last_updated: Feb 5, 2024
tags:
summary: "This Document describes the message protocol between the sending gateways and Monitoring Service"
sidebar: mydoc_sidebar
permalink: messageformats.html
folder: monitoring
---

## Gateway Message Protocol Overview
The JemRF Gateway message protocol used to send messages from the Raspberry Pi Server software, or the WiFi based WiFi Sensor or the WiFi Gateway to the monitoring server is a simple client to server message format using HTTP GET. For JemRF Monitoring, the host that sends messages to the monitoring service is referred to as a Gateway.  Gateways send updates about their operation as well as forward sensor readings.

The message protocol format is:
* http(s)://[**server**]/**alarmhostr.php**?token=[**user token**]&function=[Function Number]&opcode0=[**value0**]&opcode1=[**value1**]&opcode3=[**value1**]&opcode4=[**value1**]

Depending on the function and the number of opcode parameters will change.

- The server is your **server** hostname or IP Address.
- The **token** is used to associate the data with a Monitoring Account.
- The receiving application name is fixed to "**alarmhostr.php**".

## Functions
The Function Number is used to identify the message types
The common functions are used to identify what type data is being sent, such as sensor value for temperature, humidity or sensor State for a door opening or closing. There are also functions that provide diagnostic information about the remote devices.

### Authentication
When a new data sender (aka Gateway) starts up it authenticates to the monitoring server.
Function 27 is used to authenticate the token used is valid and that future data from that sender will be accepted.

That authentication message is done with Function 27.
- The sending device or Gateway is identified in opcode0.
- The sending device's local IP is in opcode1
- Opcodes 2 and 3 are optional and used by the WiFi devices to send the firmware version and the WiFI signal strength value (RSSI) to the server for diagnostic monitoring.
If the authentication process is successful the WiFi devices will show a Connected State on the local device setup screen.

Example:
* token=62af64008be7e830503ce894bf787d39&function=27&opcode0=01590588&opcode1=192.168.254.65&opcode2=3.4&opcode3=-66

- opcode0 is the Gateway Id - "01590588"
- opcode1 is the IP Address of the device - 192.168.254.65
- opcode2 is the Firmware Version - 3.4
- opcode3 is the WiFi Signal level (RSSI) at the Gateway - 66 db

The WiFi devices will send a Function 27 message every 5 minutes as a check-in to validate the connection and update the server that the device is still online and working.

### Data Functions
The common messages are data monitoring messages using these functions:
#### Function 30
This is the normal data measurement message from WiFi Sensors.

* token=ec1e01e6d2f5586bc582e9e9c97751d6&function=30&opcode0=76.82&opcode1=0&opcode2=01451557&opcode3=34.30&opcode4=192.168.254.76

This example shows both temperature and humidity:
- opcode0 is the Sensor temperature value - 76.82
- opcode1 is flag 1 no Humidity value, 0 Humidity value included
- opcode2 is the sensor Id -  01451557
- opcode3 is the Humidity value - 34.30%
- opcode4 is the IP Address of the Unit - 192.168.254.76

* token=62af64008be7e830503ce894bf787d39&function=30&opcode0=82.18&opcode1=1&opcode2=5421211168&opcode3=0&opcode4=192.168.254.32

In the above example the temperature reading for device "5421211168" is 82.18, opcode1 = 1 means the reading is in Fahrenheit. For readings in Celsius, opcode1 would be 0.

#### Function 37
These messages are discrete readings for temperature and humidity readings from device 50.
* token=62af64008be7e830503ce894bf787d39&function=37&opcode0=50&opcode1=67.532&opcode2=1&opcode3=192.168.254.61

To identify a humidity reading from device 50 the Id is changed to 350. Now the receiving monitoring system knows it is a humidity reading.

* token=62af64008be7e830503ce894bf787d39&function=37&opcode0=350&opcode1=25.40&opcode2=2&opcode3=192.168.254.61

- opcode0 is the sensor Id - 50 (When a sensor can send both temperature and humidity the sensor id starts with 300)
- opcode1 is the Sensor value - 25.40
- opcode2 is flag for value: 1 == Temperature, 2 == Humidity, 3 == Pressure   - 2 (humidity)
- opcode3 (optional) is the IP Address of WiFi device - 192.168.1.194

#### Function 38
Function 38 is for on/off devices or device States.
In this example, device 52 is on on/off device and opcode = 1 is its current reading.
* token=62af64008be7e830503ce894bf787d39&function=38&opcode0=52&opcode1=1&opcode2=2&opcode3=192.168.1.194
- opcode0 is the sensor Id - 52
- opcode1 is the Sensor value (1 or 0) - 1
- opcode2 is flag == 2 is on/off device - 2
- opcode3 (optional) is the IP Address of WiFi device - 192.168.1.194

### Information Functions
To support diagnostic monitoring of the remote devices and gateway there are some informational messages.
#### Function 22
To monitor the wireless RF sensors, there is Function 22.
Function 22 is used to report the RF Sensor battery levels to the monitoring server for diagnostic monitoring.
The RF Sensor will send a battery reading on every tenth transmission.

Example of Function 22:
* token=62af64008be7e830503ce894bf787d39&function=22&opcode0=44&opcode1=2.79&opcode2=2&opcode3=192.168.254.61

Where:
- opcode0 is the sensor Id - 44
- opcode 1 is the battery reading of 2.79 volts.
- opcode 2 (optional) is the IP Address of WiFi device - 192.168.1.194

#### Function 39
Function 39 is a special function in the WiFi devices, that is used to send the receive signal strength of the remote RF Sensor to the monitoring server.
The RF receiver will send a signal strength message (RSSI) after the first new message is received by the RF IoT Gateway.

Example of Function 39:
* token=62af64008be7e830503ce894bf787d39&function=39&opcode0=44&opcode1=-86.0&opcode2=2&opcode3=192.168.254.61

This shows the receive signal strength from device 44 (opcode0) is -86db (opcode1).

#### Function 70
Function 70 is a special diagnostic function for the WiFi Gateway. It reports the version of the RF Receiver and if the RF Receiver was reset.

Example of Function 70:
* token=62af64008be7e830503ce894bf787d39&function=70&opcode0=1&opcode1=7.61&opcode2=0&opcode3=192.168.254.61

In this example the RF Receiver was reset once on startup and the RF Receiver Firmware version is 7.61.


### DIY Functions
The PrivateEyePi Monitoring Service has DIY messages option and rules on event changes.

#### Function 34
Function 34 is used to tell monitoring server to send the Email information for the account associated with the token.

* token=”pep_token “&“function=34”

This request gets a response message header /EMAIL
- With details on email

#### Function 35
Function 35 is used to tell the monitoring Service to setup an Email Alert rule
* token=”pep_token “&“function=35&opcode1=”SensorNo“&opcode0=”RuleId"

#### Function 36
Funtion 36 is used to tell the Service to acknowledge the Email Update.

* token=”pep_token“&“function=36”

#### Function 32
Function 32 is used to tell the Service to the status of the Relay Values
* token=”pep_token“&“function=32&”strMessage

#### Function 28
Function 28 is used to send the current Relay Configuration information to the Service.

* token=”pep_token“&function=28&opcode0=”SensorNumber“&opcode1=”strRelayList

