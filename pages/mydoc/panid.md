---
title: PANID
keywords: ID, PANID
last_updated: July 3, 2016
tags:  
summary: "This page describes the PANID setting and how to change it."
sidebar: mydoc_sidebar
permalink: panid.html
folder: mydoc
---

The Personal Area Network ID (PanID) defines the ID associate with the network of sensors. As defined in the [Overview Section](index.html) you can have groups of sensors assigned to different networks. This enables you to sub-divide your sensor networks and direct traffic to specific receivers. The PanID is a 5 digit numeric (00000-99999).   

For two devices to communicate they must have the same [Frequency](frequency.html) and [channel](channel.html) and PanID. 
  

## PanID Default Settings
The standard PanID is set to 23205.

## How to change the Device ID 

The PanID can be changed using the ATID command. 

**Command:** ATID[*p1*] <br>
**Response:** ATID[*p1*]

*Where*: p1 = The new 5 digit all numeric number (00000 to 99999)

The below example changes the PanID to 12345:

```
python rf_config.py 03 ATID12345
SENT     : 03ATID12345
RECEIVED : 03ATID12345
```

The device requires a reboot to enable the new PanID.