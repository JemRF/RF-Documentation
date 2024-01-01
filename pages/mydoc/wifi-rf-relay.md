---
title: WiFi Wireless Gateway
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Jan 1, 2024
tags:
summary: "This Document describes the basics of the WiFi Wireless Gateway"
sidebar: mydoc_sidebar
permalink: wifirfrelay.html
folder: mydoc
---
## Introduction
The WiFi Wireless Gateway (WiFi Gateway) receives messages from the Wireless sensors and sends them to the PrivateEyePi or JemRF Monitoring server. This eliminates the need for a Raspberry PI computer and all that extra overhead. The Gateway provides an easy to use tool to get your wireless sensors online free of configuring and programming a computer first.<br />

The WiFi Gateway is in the same physical case as the current WiFi IoT Sensors.
 * Follows the same setup process as our WiFi IoT Sensors to connect to the local WiFi.
 * It has option to send Celsius to Fahrenheit readings.
 * Using a USB-mini connector for power.
 * It provides a Sensor List overview page to show all the sensors it is tracking and their last value.

{% include image.html file="wirelessgateway.png" alt="WiFi Gateway Case"%}

## Tech Specs
* Dimensions 74mm x 55mm x 28mm
* Powered either by USB Mini cable and USB power supply, or battery connection (2.5V to 3.5V) via the 2 pin battery connection plug
* Upgrades are done over the air using the Update button or can be done manually done using a 3.3V FTDI cable


## Setup Details
The configuration page for the WiFi Gateway is very similar to the WiFi IoT Sensor.
You can configure the Wireless Gateway using any device that supports WiFi and an internet browser. In this example we will use a desktop computer.

{% include image.html file="Slide1da59.jpg" alt="WiFi GW Start"%}


***To make setup easy, the WiFi Gateway has its own Access Point.***

### Step 1 Connect to WiFi

The first step is to connect your smart device to the WiFi Gateway. Power up the WiFi Gateway and using your computer (or smart device) look for a WiFi connection that starts with **JRF** followed by some numbers. These numbers are the unique ID of your device. Connect to the device using the default password:
{% include image.html file="gwsetup-ssid.jpg" alt="WiFi GW Connect"%}


Password: WiFirelay

### Step 2 : Configure SSID and Password
Now open up a browser  and navigate to http://192.168.4.1/.
{% include image.html file="wifigwsetup.jpg" alt="WiFi GW Setup Page"%}
From here you configure your WiFi Settings.

{% include image.html file="wifigwsetup-ssid.jpg" alt="WiFi GW SSID Select Page"%}
Next enter the SSID and Password of your WiFi router and click on save.

Wait a few moments for the WiFi Gateway to connect to the WiFi router. Click on the "Setup Details" menu option to refresh the screen. Once connected you will see the **WLAN:** IP address has given to the Wireless Gateway, as shown in the next image. In the example below it shows 192.168., yours will be different. What's important is your gateway is now connected to the Internet.
{% include image.html file="wifigwsetuponline.jpg" alt="WiFi Gateway Online"%}

### Step 3 : Connect to Monitoring Server
The next step is to connect your gateway to one of our services so you can monitor the devices and create alerts.  Both of our online services have a free tier.
**"www.PrivateEyePi.com"** is our original service and it provides custom event triggering and well as basic monitoring.
**"monitor.jemrf.com"** is our newer service, focused on monitoring with custom tolerance settings to trigger notifications to help alert when there is a problem.  You are welcome to visit each to see which meets your needs and can sign up for both (only one will work at a time). Both use a token to link your device to your account. You can use the PEP Token on the Monitor service if you want to switch between the two.

#### <span style="color:blue">www.PrivateEyePi.com</span>

If you have not registered an account with PrivateEyePi, go to https://www.privateeyepi.com and click on "Create User".

{% include image.html file="get_token_s.jpg" alt="Get PrivateEyePi Token"%}
Now enter your PrivateEyePi token. You can obtain your token from the User menu on www.privateeyepi.com website.
.

 The Gateway Server setting is: **"www.PrivateEyePi.com"**
 Copy and paste the token into the token field as shown in the below diagram
{% include image.html file="wifigwsetup-pep.jpg" alt="WiFi GW to PEP Server"%}


#### <span style="color:blue">Monitor.JemRF.com</span>
 You can also use https://monitor.jemrf.com to create and account and token.
 To create an account you select the Register option on top right. Once registered you will receive a validation email with link. Click on the link and your account will be activated and ready for you to login.
 When you login under your name will be a drop down, select Account and then click on the Edit Token button. If you have a PrivateEyePi token already you can paste it in the token field and click the Accept Token to validate it is unique and Save. Now the same token works for both servers.
 If you do not have a PrivateEyePi Token, click Generate Gateway Id and it will create a token for you. Click the Accept Token to validate it is unique and Save.
{% include image.html file="JemRf-account-token.jpg" alt="WiFi GW Get token"%}

 The Gateway Server setting is: **"pep.jemrf.com"**
 Copy and paste the token into the token field as shown in the below diagram

{% include image.html file="wifigw_pep.jemrf.png" alt="WiFi GW JemRF Server"%}
Click "Save" and after a few seconds for the WiFi Gateway to connect, clicking on the "Login Details" menu option to refresh the screen. Once connected you will see **"PEP: Connected"** as shown by the red circle in the image above. Once Connected, the Wireless Gateway is now forwarding Wireless Sensor data to the selected server.

## Sensors List
The Sensor List page shows the sensors the gateway has forwarded messages to the PEP server. It also shows the last message from each sensor received by the gateway with how many messages have been forwarded for that sensor and a grand total of all the messages forwarded to the server.

It tracks messages for up to 64 Sensors.

{% include image.html file="ActiveDevices.jpg" alt="WiFi GW Sensor List"%}

## MQTT Details
#### MQTT Features:
Easy to configure web interface.<br />
Connects to MQTT Broker with or without a username or password.<br />
Tested with Mosquito Docker brokers and Emqx public broker.<br />
JemRF provides an MQTT Broker for customers.

[Details on the JemRF MQTT format with examples](gatewaymqtt.html)

## Firmware Updates
The Gateway is normally updated over the Internet.
[Click Illustrated instructions](wifi-gw-update.html)

## Mounting Instructions
{% include note.html content="Mount the Gateway in a vertical position with the USB connector down. There is a mounting hold on the back for this. Do not mount against a metal wall as that will block the WiFi and RF signals."%}

