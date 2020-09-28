---
title: Channel
keywords: channel
last_updated: July 3, 2016
tags:  
summary: "This page describes the channel setting and how to change it."
sidebar: mydoc_sidebar
permalink: channel.html
folder: mydoc
---

Each Frequency has ten channels that can be used to sub divide radio traffic. There are ten channels supported by our devices.

For two devices to communicate they must have the same [Frequency](frequency.html) and Channel and [PanID](panid.html). 

## Channel Default Setting
Default is 1.

## How to change the Channel 

The Channel can be changed using the ATCN command. 

**Command:** ATCN[*p1*] <br>
**Response:** ATCN[*p1*]

*Where*: p1 = A number between 1 and 10

The below example changes the Channel to 4:

```
python rf_config.py 03 ATCH4
SENT     : 03ATCH4
RECEIVED : 03ATCH4----
```

The device requires a restart in order to effect the new Channel.