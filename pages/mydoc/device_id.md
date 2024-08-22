---
title: Device ID
keywords: ID, device, change id, change number, number, CHDEVID
last_updated: Sep 28, 2020
tags:
summary: "This page describes the Device ID and how to change it."
sidebar: mydoc_sidebar
permalink: device_id.html
folder: mydoc
---

The Device ID is a two character unique identifier for each device. The ID is appended to each [radio message](rf_message_format.html) so that the receiver of the message can determine which sensor sent the message. The Device ID is also used to address a device when sending a command. When a device receives a message (whether it arrives through the serial port or over the radio) the device compares the Device ID of the in-coming message to its own Device ID. If there is a match then the device will action the command.

{% include note.html content="You can use numerics as well as alphabet characters 0-9, b-z, A-Z in the Device ID which gives a total possible 3,721 unique ID's. If you need more ID's then have a look at the [PANID](panid.html) setting." %}

## Message ID Default Settings
The standard Device ID of a IoT Gateway is 01 and the standard Device ID of sensors is a random number between 01 and 99.

## How to change the Device ID

The Device ID can be changed using the CHDEVID command.

**Command:** CHDEVID[*p1*] <br>
**Response:** CHDEVID[*p1*]

*Where*: p1 = The new two character ID

The below example changes the Device ID from 03 to 05:

```
python rf_config.py 03 CHDEVID05
SENT     : 03CHDEVID05
RECEIVED : 03CHDEVID05
```

{% include note.html content="We suggest you use alphanumeric characters only. Although the devices will support ASCII codes 32-122, the supporting interface applications may not handle non-alphanumeric characters very well." %}
