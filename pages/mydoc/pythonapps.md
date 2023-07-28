---
title: Python JemRF Applications
keywords: python3 python applications
last_updated: July 27, 2023
tags:
summary: "This page describes the Python application provided by JemRF to test and use RF Sensors on Raspberry Pi's and Orange Pi Zero microcomputers."
sidebar: mydoc_sidebar
permalink: pythonapps.html
folder: mydoc
---

The Python Applications provided by JemRF are available for download from the JemRF Github repository.

{% include note.html content="There are common programs in each repository: bme280.py, rflib.py, rfsensor.py, rfsettings.py are the same across all repositories."%}

## RF-Apps
JemRF Apps for RF devices

These applications are simple projects to get started using the JemRF Wireless RF devices.
More details on Project Site  https://projects.jemrf.com

Download to Pi:

    git clone https://github.com/JemRF/RF-Apps.git


#### Program and current Version or Date stamp if marked.
* alarm.py            15
* alarmfunctionsr.py  16
* bme280.py
* callback.py
* dallas.py           16
* dht22.py            16
* globals.py          12
* lcd_hd44780.py
* lcd_nokia.py
* lcdtest.py          2
* publish.py
* README.md
* restarter.py
* rf2mqtt.py          3
* rflib.py            7/19/2023
* rfsensor.py
* rfsettings.py       26
* rfthermtest.py      1.20
* subscribe.py        3
* verdanab.ttf
* webcam.py           4

## rf_tools
JemRF Applications to test and operate the Wireless RF devices.

More details on RF Documents  https://documents.jemrf.com/

Download to Pi:

    git clone https://github.com/JemRF/rf_tools.git

#### Programs and Current Version/Date if tagged

Programs Version
bme280.py
README.md
rf_config.py
rf2adafruitio.py    2
rf2blynk.py         3
rf2ha.py            3
rf2X.py
rflib.py            7/19/2023
rfsettings.py
serial_mon.py


## Data Logger
Data-logging instructions can be found at http://projects.privateeyepi.com/home/create-a-database-logger.php

Download to Pi:

    git clone https://github.com/JemRF/Data-logging.git

#### Programs and Current Version/Date if tagged
bme280.py
dblogger.php
index.php
python3
README.md
rf2serial.py
rflog_db.py
rfsensor.py
rfsettings.py

All but two apps are Python 2 and 3 compatible.
The python3 folder contains the Python 3 version of two application: rf2serial.py and rflog_db.py

{% include note.html content="The programs: bme280.py, rflib.py, rfsensor.py, rfsettings.py are the same in all repositories."%}

## Python MQTT
This application is now included in the RF-apps collection.

MQTT interface for JemRF sensors : https://www.jemrf.com/collections/all

This application publishes data from RF messages using JSON (example payload below) to a topic of [device_prefix]_[device id]

The device_prefix is set in the config below

The device id is the device id of your RF sensor

Example topic : "myhome/RF_Device04"

Example payload: {"TMP": "25.39", "HUM": "60.20"}

{% include note.html content="The MQTT format is not the same format provided with the WiFi RF Gateway and WiFi Sensor."%}