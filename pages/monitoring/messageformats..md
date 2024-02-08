---
title: JemRF Monitoring Message Formats
keywords: communication& communications& relay& basic& radio& spec& wifi& sensor
last_updated: Feb 5, 2024
tags:
summary: "This Document describes the different message formats between the different gateways and Monitoring"
sidebar: mydoc_sidebar
permalink: messageformats.html
folder: monitoring
---

## Gateway Message Protocol Overview
The JemRF Gateway message protocol used to send messages from the Raspberry Pi Server software, or the WiFi based WiFi Sensor and WiFi Gateway to the monitoring server is a simple client to server message format using HTTP GET.
The host sending messages to the monitoring server is referred to as a Gateway.

The message protocol format is:
* http(s)://[**server**]/**alarmhostr.php**?token=[**user token**]&function=[Function Number]&opcode0=[**value0**]&opcode1=[**value1**]&opcode3=[**value1**]&opcode4=[**value1**]

Depending on the function and the number of opcode parameters will change.

- The server is your **server** hostname or IP Address.
- The **token** is used to associate the data with a Monitoring Account.
- The receiving application is fixed to "alarmhostr.php".

## Functions
The Function Number is used to identify the message types
There are functions used to identify what type data is being sent, such as sensor value for temperature, Humidity or sensor State for a door opening or closing. There are also functions that provide diagnostic information about the remote devices.

### Function 27
When a new data sender (aka Gateway) starts up it authenticates to the monitoring server.
That authentication message is done with Function 27.
- The sending server or Gateway is identified in opcode0.
- The sending server's local IP is in opcode1
- Opcodes 2 and 3 are optional and used by the WiFi devices to send the firmware version and the WiFI signal strength value (RSSI) to the server for diagnostic monitoring.
If the authentication process is successful the WiFi devices will show a Connected State on the local device setup screen.

Examples:
1. token=62af64008be7e830503ce894bf787d39&function=27&opcode0=502636544&opcode1=192.168.254.61&opcode2=2.3.9a&opcode3=-54

In this example the sending device Id is "502636544", its firmware is Version 2.3.9a, and its WiFi signal strength is -54db.

2. token=62af64008be7e830503ce894bf787d39&function=27&opcode0=01590588&opcode1=192.168.254.65&opcode2=3.4&opcode3=-66

In this example the sending device Id is "01590588", its firmware is Version 3.4, and its WiFi signal strength is -66 db.

The WiFi devices will send a Function 27 message every 5 minutes as a check-in to validate the connection and update the server that the device is still online and working.

### Data Functions
The common data monitoring functions are:
#### Function 30
This is the normal data measurement message from WiFi Sensors.
* token=62af64008be7e830503ce894bf787d39&function=30&opcode0=82.18&opcode1=1&opcode2=5421211168&opcode3=0&opcode4=192.168.254.32

In the above example the temperature reading for device "5421211168" is 82.18, opcode1 = 1 means the reading is in Fahrenheit. For readings in Celsius, opcode1 would be 0.

* token=ec1e01e6d2f5586bc582e9e9c97751d6&function=30&opcode0=76.82&opcode1=1&opcode2=01451557&opcode3=34.30&opcode4=192.168.254.76

The second example shows both temperature and humidity, opcode3 is the humidity reading of 34.30%. In this example a value of 0 is no humidity reading.

#### Function 37
These messages are discrete readings for temperature and humidity readings from device 50.
* token=62af64008be7e830503ce894bf787d39&function=37&opcode0=50&opcode1=67.532&opcode2=1&opcode3=192.168.254.61

To identify a humidity reading from device 50 the Id is changed to 350. Now the receiving monitoring system knows it is a humidity reading.

* token=62af64008be7e830503ce894bf787d39&function=37&opcode0=350&opcode1=25.40&opcode2=2&opcode3=192.168.254.61

#### Function 38
Function 38 is for on/off devices or device States.
In this example, device 52 is on on/off device and opcode = 1 is its current reading.
* token=62af64008be7e830503ce894bf787d39&function=38&opcode0=52&opcode1=1&opcode2=2&opcode3=192.168.1.194


### Information Functions
To support diagnostic monitoring of the remote devices and gateway there are some informational messages.
#### Function 22
To monitor the wireless RF sensors, there is Function 22.
Function 22 is used to report the RF Sensor battery levels to the monitoring server for diagnostic monitoring.
The RF Sensor will send a battery reading on every tenth transmission.

Example of Function 22:
* token=62af64008be7e830503ce894bf787d39&function=22&opcode0=44&opcode1=2.79&opcode2=2&opcode3=192.168.254.61

Where opcode 1 is the battery reading of 2.79 volts.

#### Function 39
Function 39 is a special function in the WiFi devices, that is used to send the receive signal strength of the remote RF Sensor to the monitoring server.
The RF receiver will send a signal strength message (RSSI) after the first new message is received by the RF IoT Gateway.

Example of Function 39:
* token=62af64008be7e830503ce894bf787d39&function=39&opcode0=44&opcode1=-86.0&opcode2=2&opcode3=192.168.254.61

This shows the receive signal strength from device 44 is -86db.

#### Function 70
Function 70 is a special diagnostic function for the WiFi Gateway. It reports the version of the RF Receiver and if the RF Receiver was reset.

Example of Function 70:
* token=62af64008be7e830503ce894bf787d39&function=70&opcode0=1&opcode1=7.61&opcode2=0&opcode3=192.168.254.61

In this example the RF Receiver was reset once on startup and the RF Receiver Firmware version is 7.61.




