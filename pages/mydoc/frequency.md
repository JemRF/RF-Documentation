---
title: Frequency
keywords: frequency
last_updated: July 3, 2016
tags:  
summary: "This page describes the Frequency setting and how to change it."
sidebar: mydoc_sidebar
permalink: frequency.html
folder: mydoc
---

There are six frequencies supported by our devices:


|Frequency Number|Frequency|
|----------------|---------|
|1 | 433 MHZ|
|2 | 915 MHZ (US & Canada)|
|3 | 868.3 MHZ (Europe)|
|4 | 868 MHZ|
|5 | 903 MHZ|
|6 | 315 MHZ|


For two devices to communicate they must have the same Frequency and [channel (ATCN)](channel.html) and [PanID](panid.html). 

## Frequency Default Settings
Default is 915 MHZ, but should be changed to the open frequency in your region.  

## How to change the Frequency 

The Frequency can be changed using the ATCH command. 

**Command:** ATCH[*p1*] <br>
**Response:** ATCH[*p1*]

*Where*: p1 = A number between 1 and 6 per the Frequency Number in the above table

The below example changes the Frequency to 433 MHZ:

```
python rf_config.py 03 ATCH1
SENT     : 03ATCH1
RECEIVED : 03ATCH1----
```

The device requires a restart in order to effect the new frequency.