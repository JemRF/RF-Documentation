---
title: Thingsboard Integration
keywords: interface, integrate, integration, thingsboard
last_updated: July 15, 2024
tags:
summary: "This page explains how to integrate our WiFi MQTT with Thingsboard."
sidebar: mydoc_sidebar
permalink: thingsboard2.html
folder: mydoc
---
# Description
Connecting to the Community Edition of ThngsBoard using WiFi Sensor and WiFi RF Gateway MQTT feature and JSON data format.

## Step 1 Power up the WiFi Device and connect to is WiFi
First power up the WiFi Sensor or WiFi Gateway. It will create a WiFi network called PEP<number> for the WiFi Sensor and JRF<number> for the WiFi Gateway. Connect to the listed network and enter the device password. , when it shows connect open web browse and access the device configuration website http://192.168.4.1/.

## Step 2 Connect the WiFI Device to the Internet
In this portal, you enter the local WiFi network credentials in the Login Details tab to connect to the Internet and then press Save.


In step 4, you will need the number following the PEP or JRF in the upper right corner.

## Step 3 Configure the Wi-Fi sensor or Gateway
 a) On the JemRF device configuration website, after connecting the device to the local network, go to the "Sensor Config" tab and check the "Send To Server" box. Optionally you can change the sending interval time in the "Temperature send interval" field. Normal Send to Server is 300 seconds, it can be as often as 60 seconds and as long as you want.  Finally, to save the data, press the Save button.


b) In the MQTT tab, you must enter all the necessary data to connect to the ThingsBoard MQTT broker and press the Save button.
<img src="images/jemrf_tb_3.png" width="425"/>

## Step 4 Setup ThingsBoard Device Profile panel
a) Under "Device Profile" you create a transport type of MQTT. Additionally, in the "Telemetry topic filter" field, you must add the identification number that the JemRF device concatenates to the end of the topic when sending data.  <img src="images/jemrf_tb_2.png" width="425"/>

b) A new "device" must be created that has the new profile created set to it. On the other hand, the device token must be copied using the "Copy Access Token" button to use it in the device configuration in step 2) b).
<img src="images/jemrf_tb_1.png" width="425"/>

## Step 5 Setup ThingsBoard Device Telemetry
 Finally, in the "Last telemetry" tab of the device in ThingsBoard, you can see the messages sent under the temperature, humidity, and unit_of_measurement fields.
<img src="images/jemrf_tb_4.png" width="425"/>
