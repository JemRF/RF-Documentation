---
title: WiFi Gateway MQTT Explained
keywords: Gateway, mqtt
last_updated: Aug 14, 2022
tags:
summary: "This page is to show how to setup MQTT on the WiFi Gateway and Node-RED"
sidebar: mydoc_sidebar
permalink: gatewaymqtt.html
folder: mydoc
---

# JemRF WiFi Wireless Gateway MQTT

The JemRF WiFi Wireless Gateway provides a built-in MQTT Client. The Gateway can both send to the PrivateEyePi Server for it to store and display readings and it can also  connect to a MQTT Broker and publish the sensor readings.  It can do both at the same time, or just send to the Server or the Broker. You can now use tools like Node-Red to build your own monitoring displays

The settings to publish the sensor readings to an MQTT broker are done on the MQTT Detail Tab as seen in Figure 1.


<img src="images/mqtt-figure-1-start.jpg" width="425"/>
**Figure 1  MQTT Details Setup.**

## Getting Started
Enter the MQTT Broker, in my case my local server, the MQTT Port, for me is the standard MQTT Port. Next is the optional Username and Password.

The Gateway comes perset to Port 1883 and has jemrf for the default username and mqtt4jemrf as the default password.

Once Enabled, the Gateway will try and connect, if the connection is successful the screen will refresh and show Connected.  If there is a problem connecting, the gateway display will stay frozen for up to one minute while the Gateway tries to connect.  If the Gateway can not connect in the allotted time, the screen will display it has failed, the Enabled will be set to Not Enabled  and a Red Failed message will appear.

## Publishing Format
Using the MQTT standard protocol the Gateway will publish data to the broker using the subscription that is the combination of the Gateway Name and the sensor message.
-Subscription
Using the Gateway shown Figure 1, that Gateway name is JRF03516124.
Using the sensor show in Figure 2

<img src="images/mqtt-figure-2-sample.jpg" width="425"/>
**Figure 2, Sample Temperature Gateway Display**

Sensor 11  is being received by the Gateway. It is a Temperature sensor  (TMPC) and it has a value of 22.37 degrees C.
The actual message from the sensor was in the form 11TMPC22.37.
The Gateway separates the Device Id to make it easy, then the MQTT Key with the last value to see the sensors it is receiving.

For the MQTT Message, the sensor message is the MQTT Key (11TMPC) with the value 22.37.

The Gateway would publish that as: JRF03516124/[MQTT KEY] which in this example would be: JRF03516124/11TMPC with value 22.37.

When you Subscribe to the Broker to receive the messages, you would subscribe to: JRF03516124/11TMPC

If you want to see all of the sensors, you could subscribe to: JRF03516124/# and get them all.

## Node-RED Dashboard
I used Node-Red to create a simple Dashboard. The configuration was:


<img src="images/mqtt-figure-3-config.jpg" width="425"/>
**Figure 3 Node Red subscribing to Gateway and Sensor 11**

With that configuration, it created the Dashboard shown below

<img src="images/mqtt figure 4-dashboard.jpg" width="425"/>
**Figure 4 Sample Node-RED Dashboard**

Note: Because my Gateway is set to do Celsius to Fahrenheit conversion, my readings are in Fahrenheit. That the differences in values being shown vs the value received by the Gateway.

