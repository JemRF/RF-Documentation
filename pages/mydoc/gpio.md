---
title: GPIO
keywords: gpio
last_updated: Sep 28, 2020
tags:  
summary: "This page describes the GPIO functionality of the Flex RF module."
sidebar: mydoc_sidebar
permalink: gpio.html
folder: mydoc
---

There are three general purpose IO pins on the Flex module that are configured for output and set on/off using the GPIO command. This is useful for switching LED's on/off or interfacing with external circuitry.

The GPIO pins are Pin 3,4 and 5 (refer below diagram) 

<img src="images/flex pinout v2.png" width="425"/>

## GPIO Default Setting
Each GPIO pin is configured for output and off by default.

## How to use the GPIO command 

**Command:** GPIO[*p1*][*p2*] <br>
**Response:** GPIO[*p1*][*p2*]

*Where*: <BR> 
p1 = A,B or C pin indicator from the above pinout diagram <BR>
p2 = 0 for off and 1 for on <BR>

The below example explains how to set GPIOA on:

```
python rf_config.py 03 GPIOA1 
SENT     : 03GPIOA1
RECEIVED : 03GPIOA1
```

