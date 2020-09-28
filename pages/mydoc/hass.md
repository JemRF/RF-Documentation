---
title: Home Assistant Integration
keywords: interface, integrate, integration, home assistant, hass
last_updated: Sep 28, 2020
tags:  
summary: "This page explains how to integrate our RF Modules with Home Assistant"
sidebar: mydoc_sidebar
permalink: hass.html
folder: mydoc
---

<img src="images/hass.webp" width="425"/>

Home Assistant is an open source home automation platform. It has a vast amount of interfaces (over 740 when this article was written). 

They have a well documented Getting Started Guide for Raspberry Pi so we will not cover installing Home Assistant on your Raspberry Pi in this tutorial. Here is the link for common Home Assistant tasks on Raspberry Pi.

### What you will need
* Any model Raspberry Pi with preferably the full Raspbian distro 
* [IoT Gateway](iot_gateway.html) for Raspberry Pi or Flex RF Module
* Any [wireless sensor](https://www.jemrf.com/collections/all/rf-sensors)

### What you need to know beforehand
* How to operate a Raspberry Pi
* You have already set up your [IoT Gateway](iot_gateway.html) and [tested your sensor](sensor_testing.html)
* Some Python programming knowledge is preferable but not mandatory as we provide you with the source code

### STEP 1: DOWNLOAD THE JEMRF MQTT LIBRARY

```
git clone https://github.com/JemRF/MQTT

cd MQTT
```

### STEP 2: INSTALL MQTT (IF YOU HAVEN'T ALREADY)
```
sudo pip install paho-mqtt
```

### STEP 3: CONFIGURE YOUR IP ADDRESS
```
sudo nano rf2mqtt.py
```

Page down and edit the ip_address in the Configurations section.

```
#Configurations===============
DEBUG = True
Fahrenheit = False
mqtt_server = "192.168.2.201" #Enter the IP address of your MQTT server 
topic = "myhome"
device_prefix = "RF_Device"
#=============================
```

Pres CTRL-X to exit and save.

### STEP 4: EDIT THE HOME ASSISTANT YAML FILE AND CONFIGURE MQTT AND YOUR SENSORS
Type: 

```
sudo nano /home/homeassistant/.homeassistant/configuration.yaml
```

﻿Then add the following section to the bottom of the file:

```
mqtt:
broker: 192.168.2.201

# Example configuration.yaml entry temperature & humidity sensor with a DeviceID of 04:

sensor:
  - platform: mqtt
    name: "Temperature"
    state_topic: "myhome/RF_Device04"
    unit_of_measurement: '°C'
    value_template: "{{ value_json.TMP }}"


  - platform: mqtt
    name: "Humidity"
    state_topic: "myhome/RF_Device04"
    unit_of_measurement: '%'
    value_template: "{{ value_json.HUM }}"
```

Remember to restart the Home Assistant service:
```
sudo systemctl restart home-assistant@homeassistant.service
```
### STEP 5: RUN THE INTERFACE
```
python rf2mqtt.py
```

You should see output like this:

```
pi@raspberrypi:~/MQTT $ python rf2mqtt.py
Sat Aug 4 18:50:12 2018 a04STARTED--
Sat Aug 4 18:50:12 2018 a04STARTED--
Sat Aug 4 18:50:18 2018 a04TMPB25.39
Sat Aug 4 18:50:18 2018 a04TMPB25.39
Sat Aug 4 18:50:18 2018 a04TMPB25.39
Sat Aug 4 18:50:18 2018 a04HUM58.70-
Processing data : DevId=04,Type=4,Value1=25.39,Value2=58.70
{"TMP": "25.39", "HUM": "58.70"}
Sat Aug 4 18:50:18 2018 a04HUM58.70-
Sat Aug 4 18:50:18 2018 a04HUM58.70-
Sat Aug 4 18:50:18 2018 a04SLEEPING-
```
