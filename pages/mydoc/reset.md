---
title: RESET
keywords: reset, factory, default, security
last_updated: Sep 28, 2020
tags:
summary: "This page describes how to reset your device back to default settings"
sidebar: mydoc_sidebar
permalink: reset.html
folder: mydoc
---

There may be a time where you have lost communication with your device, particularly when doing configuration of frequency, channel, PanID and encryption. You can use the RESET command to reset the device back to default settings. The RESET command can only be sent through the serial port (this is a security feature). If you are unsure how to connect connect your device's serial port please refer to the [hardware and firmware](hardware_and_firmware.html) section of this documentation.

## How to use the RESET command

Connect your device to the micro-controller's serial port.

Unlike all other commands, the RESET command takes no Device ID.

```
python rf_config.py RESET -V
SENT     : RESET
RECEIVED : OK-------
```

