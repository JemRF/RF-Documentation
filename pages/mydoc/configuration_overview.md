---
title: Configuration Overview
keywords: configuration, configure, change, alter, update, setting
last_updated: Sep 28, 2020
tags:  
summary: "This page introduces sensor configuration."
sidebar: mydoc_sidebar
permalink: configuration_overview.html
folder: mydoc
---

## Older RF2 Modules

All our older RF2 modules (sensors & IoT Gateway) are configured by sending them [configuration commands](rf_message_reference.html). You can use the [rf_config](utilities.html) tool to send configuration changes to the RF module simply by addressing the device_id of the target RF module followed by the configuration change. For example the following command changes the cycle interval of device 75 to 10 minutes:

```
python rf_config.py 75 INTVL010 
```

In this section of the documentation we will cover the most common configurations in detail. The full list of configurations can be found in the [message reference](rf_message_reference.html).  

## RF4 Modules
All our RF4 modules (sensors & IoT Gateway) are configured by sending them [configuration commands](rf4_message_reference.html). You can use the [rf_config](utilities.html) tool to send configuration changes to the RF module simply by addressing the device_id of the target RF module followed by the configuration change. For example the following command changes the cycle interval of device 0075 to 10 minutes:

```
python rf_config.py 0075 INVL010 
```
The sensor will echo back the command (ie: b0075INVL010) if the change was successful or it will send an error (ie: b0075ERR) if there was a problem with the command.

```
The RF4 rf_config.py application has been updated to support RF4 format, restricts the device Id to a-z,A-Z, and 0-9 characters or lenght of 2 or 4 characters.  RF2 devices will only accept 2 character IDs and RF4 will only accept 4 character Ids.
```

In this section of the documentation we will cover the most common configurations in detail. The full list of configurations can be found in the [message reference](rf4_message_reference.html).  
