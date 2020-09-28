---
title: Configuration Overview
keywords: configuration, configure, change, alter, update, setting
last_updated: July 3, 2016
tags:  
summary: "This page introduces sensor configuration."
sidebar: mydoc_sidebar
permalink: configuration_overview.html
folder: mydoc
---

All our RF modules (sensors & IoT Gateway) are configured by sending them [configuration commands](rf_message_reference.html). You can use the [rf_config](utilities.html) tool to send configuration changes to the RF module simply by addressing the device_id of the target RF module followed by the configuration change. For example the following command changes the cycle interval of device 75 to 10 minutes:

```
python rf_config.py 75 INTVL010 
```

The sensor will echo back the command (ie: a75INVTL010) if the change was successful or it will send an error (ie: a75ERR) if there was a problem with the command.

In this section of the documentation we will cover the most common configurations in detail. The full list of configurations can be found in the [message reference](rf_message_reference.html).  
