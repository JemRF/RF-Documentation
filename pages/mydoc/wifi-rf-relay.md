---
title: WiFi RF Wireless Sensor Relay
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: April 26, 2022
tags:
summary: "This Document describes the basics of WiFi RF Wireless Sensor Relay,or WiFi-RF Relay"
sidebar: mydoc_sidebar
permalink: wifirfrelay.html
folder: mydoc
---

The WiFi-RF Relay eliminates the need for a Raspberry PI or Arduino computer to receive data from the Wireless RF Sensors.  It provides and alternate way to do the Celsius to Fahrenheit conversion if wanted, then send the readings to the PrivateEyePi server.

The WiFi-RF Relay follows the same setup process as our WiFi IoT Sensors to connect to the local WiFi and then establishes a connection to the PEP server. <br />
Unlike using a Raspberry Pi or Arduino you do not get the extra functions, internal sensors, or option to issue commands to the Wireless RF Sensor. <br />
The WiFi-RF Relay is an Wireless RF receiver only, it has no internal sensors and it can not be used to send commands to RF Sensors.

The WiFi-RF Relay is in the same physical case as the current WiFi IoT Sensor. Using a mini-USB connector for power.

{% include image.html file="wifi-relay-case.jpg" alt="WiFi RF Relay Case"%}


## Setup Details
The configuration page for the WiFi-RF Relay is very similar to the WiFi IoT Sensor. An added features include the option to establish a secure/encrypted (https) connection to the server or not.  It also has the option for Celsius to Farenheit conversion.

{% include image.html file="SetupScreen.jpg" alt="WiFi RF Relay Setup Page"%}


*To make setup easy, the WiFi RF Wireless Sensor Relay has its own internal Web Server.*

### Step 1 Connect to WiFi

The first step is to connect your smart device to the WIFI sensor. Power up the WIFI sensor and using your computer (or smart device) look for a WIFI connection that starts with **JRF** followed by some numbers. These numbers are the unique ID of your sensor. Connect to the sensor using the default password:

Password: WiFiRelay

### Step 2 : Configure SSID and Password
Now open up a browser  and navigate to http://192.168.4.1/. Next enter the SSID and Password of your WIFI router and click on save.

Wait a few seconds for the WIFI temperature sensor to connect to the WIFI router. Click on the "Login Details" menu option to refresh the screen. Once connected you will see the IP address has given to the WIFI-RF Relay, as shown in the next image. In  the example below it shows 192.68.254.69, but yours will be different. Your WIFI-RF Relay is now connected to the internet.

### Step 3 : Connect to PrivateEyePi
The next step is to connect your sensor to PrivateEyePi so you can monitor the sensor or create alerts. If you have not registered an account with PrivateEyePi, go to http://www.privateeyepi.com and click on "Create User". This is a free online service.

{% include image.html file="get_token_s.jpg" alt="Get PrivateEyePi Token"%}
Now enter your PrivateEyePi token. You can obtain your token from the User menu on www.privateeyepi.com website.

Copy and paste the token into the token field as shown in the below diagram.
Click "Save" and again wait for a few seconds for the WIFI sensor to connect, clicking on the "Login Details" menu option to refresh the screen. Once connected you will see **"PEP: Connected"** as shown by the red circle in the image above.

Once Connected, WiFi-RF Relay is now forwarding Wireless Sensor data to the PrivateEyePi server.

## Sensors List
The Sensor List page shows the sensors the relay has forwarded messages to the PEP server. It also shows the last message from each sensor received by the gateway with how many messages have been forwarded for that sensor and a grand total of all the messages forwarded to the server.

It tracks messages for up to 64 Sensors.

{% include image.html file="ActiveDevices.jpg" alt="WiFi RF Relay Sensor List"%}


