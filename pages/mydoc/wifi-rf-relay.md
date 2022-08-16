---
title: WiFi Wireless Gateway
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: June 3, 2022
tags:
summary: "This Document describes the basics of WiFi RF Wireless Sensor Relay,or WiFi Wireless Gateway"
sidebar: mydoc_sidebar
permalink: wifirfrelay.html
folder: mydoc
---

The WiFi Wireless Gateway (WiFi Gateway) receives messages from the Wireless sensors and sends them to the PrivateEyePi or Elno server. This eliminates the need for a Raspberry PI computer to just to receive data from the Wireless RF Sensors.  <br />
The Wireless Gateway provides an easy to use tool to get your wireless sensors online free of configuring and programming the computer first or having to send commands to RF Wireless Sensors.<br />

The WiFi Gateway is in the same physical case as the current WiFi IoT Sensors.
 * Follows the same setup process as our WiFi IoT Sensors to connect to the local WiFi.
 * Provides the Celsius to Fahrenheit conversion.
 * Using a mini-USB connector for power.


{% include image.html file="wifi-relay-case.jpg" alt="WiFi RF Relay Case"%}


## Setup Details
The configuration page for the WiFi Gateway is very similar to the WiFi IoT Sensor. An added features include the option to establish a secure/encrypted (https) connection to the server or not.  It also has the option for Celsius to Farenheit conversion.

{% include image.html file="SetupScreen.jpg" alt="WiFi RF Relay Setup Page"%}


***To make setup easy, the WiFi RF Wireless Sensor Relay has its own internal Web Server.***

### Step 1 Connect to WiFi

The first step is to connect your smart device to the WIFI sensor. Power up the WIFI sensor and using your computer (or smart device) look for a WIFI connection that starts with **JRF** followed by some numbers. These numbers are the unique ID of your sensor. Connect to the sensor using the default password:

Password: WiFiRelay

### Step 2 : Configure SSID and Password
Now open up a browser  and navigate to http://192.168.4.1/. Next enter the SSID and Password of your WIFI router and click on save.

Wait a few seconds for the WIFI temperature sensor to connect to the WIFI router. Click on the "Login Details" menu option to refresh the screen. Once connected you will see the **WLAN:** IP address has given to the Wireless Gateway, as shown in the next image. In the example below it shows 192.68.254.69, yours will be different. What's important is your gateway is now connected to the internet.

### Step 3 : Connect to PrivateEyePi
The next step is to connect your sensor to PrivateEyePi so you can monitor the sensor or create alerts. If you have not registered an account with PrivateEyePi, go to http://www.privateeyepi.com and click on "Create User". You can also use https://Elno.io to create and account and token. Both are have free online services.

{% include image.html file="get_token_s.jpg" alt="Get PrivateEyePi Token"%}
Now enter your PrivateEyePi token. You can obtain your token from the User menu on www.privateeyepi.com website.

Copy and paste the token into the token field as shown in the below diagram.
Click "Save" and again wait for a few seconds for the WIFI sensor to connect, clicking on the "Login Details" menu option to refresh the screen. Once connected you will see **"PEP: Connected"** as shown by the red circle in the image above.

Once Connected, the Wireless Gatewy is now forwarding Wireless Sensor data to the PrivateEyePi server.

## Sensors List
The Sensor List page shows the sensors the gateway has forwarded messages to the PEP server. It also shows the last message from each sensor received by the gateway with how many messages have been forwarded for that sensor and a grand total of all the messages forwarded to the server.

It tracks messages for up to 64 Sensors.

{% include image.html file="ActiveDevices.jpg" alt="WiFi RF Relay Sensor List"%}

## MQTT Details
[Details on the JemRF MQTT format with examples](gatewaymqtt.html)

