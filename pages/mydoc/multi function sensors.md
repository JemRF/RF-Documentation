---
title: Multi-function Sensors
keywords: hardware, firmware, update, download
last_updated: Sep 28, 2020
tags:
summary: "This page explains the JEMRF hardware and firmware"
sidebar: mydoc_sidebar
permalink: multi function sensors.html
folder: mydoc
---

A wireless temperature sensor and wireless waterproof temperature sensor can also be used as a wireless switch, or a motion sensor, or a water sensor...and vice versa.

See below board schematic. There are connections for temperature sensor and button. Both can be use simultaneously without any firmware updates.

{% include image.html file="Board Layout.png" alt="Board Layout"%}

## Convert your temperature sensor to multi-sensor

If you have a temperature (or waterproof temperature) sensor then you can connect an external switch to the button contact points on the board. You don't need to make any configuration changes for the switch to work.


## Convert your switch sensor to multi-sensor

If you have a wireless switch sensor, motion sensor, or water sensor then you can add a 10k thermistor and 1k resistor in the TMP and 1K positions on the board for temperature sensing. You will need to solder those two parts in place and also  make configuration changes to put the device into a cyclic sleep mode so that the temperature is reported every INTVL minutes (refer [sleep modes](sleep_modes.html)).

{% include note.html content="
One of the features of a switch sensor is it sends the state every INTVL minutes regardless of whether the switch was triggered. However if you have configured either of the two above multi-sensor combinations then you no longer receive the switch state. We added a new configuration in version 7.2 called RBSON('Remote Button State') that makes the sensor send both temperature and button state every INTVL minutes. If you need to update your sensor to 7.2 or current contact sales@jemrf.com."%}
