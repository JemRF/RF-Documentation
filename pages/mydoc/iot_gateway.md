---
title: IoT Gateway for Raspberry Pi
keywords: gateway, base station, IoT, iot gateway, raspberry pi, raspberry, pi, serial, rs232
last_updated: Feb 15, 2023
tags:
summary: "This page explains how to install and operate the IoT Gateway"
sidebar: mydoc_sidebar
permalink: iot_gateway.html
folder: mydoc
---

## IoT Gateway Models
The IoT Gateway is a 10 Pin device that conects to the top 10 pins of the GPIO Bus for both the Orange Pi Zero 2 and Raspberry Pis'.

{% include note.html content="All IoT Gateway models can fit on any Raspberry Pi Model." %}

The picture below show how the gateway fits on to the Raspberry Pi.

<img src="images/RF_Base_Station.webp" width="425"/>

{% include warning.html content="Make sure you fit the gateway the right way around and and perfectly aligned with the pins of the Raspberry Pi as shown in the above pictures. You could damage the gateway if fitted incorrectly." %}

## Installation steps

1. Power off the Raspberry Pi

2. Carefully align the header as shown in Figure 1 and push the gateway all the way down onto the Raspberry Pi GPIO header.

3. In order to remove the gateway from the raspberry Pi power off the Raspberry Pi and then hold the Raspberry Pi firmly with one hand and gently wiggle the Gateway loose with your other hand. Wiggling it from side to side is easier than pulling it directly upwards.

4. The gateway receiver uses the Raspberry Pi serial port in order to communicate.

{% include important.html content="Follow [this link](configure_serial_port.html) to configure the Raspberry Pi serial port"%}

{% include note.html content="Follow [this link](orangepi.html) to use an Orange Pi Zero 2 }

## Testing the Gateway

{% include note.html content="If you have not installed the utilities, refer the [Utilities](utilities.html)" %}

Open up a Raspberry Pi terminal window and test connectivity to the Gateway.

```js
cd rf_tools

python rf_config.py 01 HELLO

SENT : 01HELLO
RECEIVED : 01HELLO----
```

As shown above the rf_config.py tool sent the command a01HELLO and it received a response a01HELLO---. That means it is working.

If the tool was unable to communicate with the gateway then you would see two failed attempts to send the HELLO command as shown here:

```js
python rf_config.py 01 HELLO
SENT : 01HELLO
SENT : 01HELLO
```

Another good test to perform is to validate that the Gateway radio is functioning correctly. You can do this by powering up a sensor and watching for the sensor STARTED messages.

```js
python serial_mon.py

Now startup the sensor...

Thu Feb 27 15:02:51 2020 95 STARTED--
Thu Feb 27 15:02:51 2020 95 STARTED--
Thu Feb 27 15:02:51 2020 95 STARTED--
Thu Feb 27 15:02:51 2020 95 STARTED--
Thu Feb 27 15:02:51 2020 95 STARTED--
```

{% include note.html content="If you have a wireless switch do not open/close the switch during the first 5 seconds as this will cause the device to start sending messages and cancel the startup sequence and prevent the device from entering sleep mode."%}

{% include note.html content="Ideally put the sensors more than 5 feet away from the receiver when testing otherwise you may see message corruption or incomplete messages. These devices are tuned to transmit at a high DB in order to penetrate walls and for long distance line of sight so we have found when a sensor is very close to the receiver (e.g. 1-2 feet) then we see incomplete messages."%}




