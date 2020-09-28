---
title: Utilities
keywords: utilities, serial_mon, rf_config, rfconfig, monitor, config, configure
last_updated: July 3, 2016
tags:  
summary: "This page explains our Python utilities that can be used to monitor radio message traffic as well as send commands and requests to other RF modules"
sidebar: mydoc_sidebar
permalink: utilities.html
folder: mydoc
---

### Install GIT if you don't have it
```js
sudo apt-get install git
```

### Download the utilities

Navigate to the directory where you wish to install the tools
Download command :

```js
git clone https://github.com/JemRF/rf_tools.git
```

### Upgrade

Navigate to the rf_tools directory

```js
git pull origin
```

{% include note.html content="
if the original installation did not use the git clone command above then you will receive an error. In this case just delete the rf_rools directory and us the download command above. 
" %}
 
## RF_CONFIG.PY

### Description
Used to transmit RF messages and display a response.

### Usage
```js 
python rf_config.py [ID] [COMMAND]
```

**Where:** <br/>
    [ID]      - 2 character unique identifier for the intended recipient of the message <br/>
    [COMMAND] - 9 character command <br/>
    
{% include note.html content="Refer the [message reference](rf_message_reference.html) for description of all commands." %}

### Example
```js
python rf_config.py 03 HELLO

The response is:
a03HELLO---
``` 

## SERIAL_MON.PY

{% include note.html content="If you have not installed the IoT Gateway, refer [IoT Gateway for Raspberry Pi](iot_gateway.html) for instruction on how to install the gateway. You can also use the Flex module as a gateway." %}


###  Description
Used to monitor RF message traffic. All messages received are displayed on the screen. 
Usage

```js
python serial_mon.py
```

### Example

The below output was transmitted from a wireless pressure, temperature and humidity sensor and displayed by `serial_mon`.

```js
Thu Feb 27 15:02:51 2020 95 AWAKE----
Thu Feb 27 15:02:51 2020 95 TMPA20.87
Thu Feb 27 15:02:51 2020 95 HUM28.11
Thu Feb 27 15:02:51 2020 95 PA1127.8
Thu Feb 27 15:02:51 2020 95 SLEEPING-
```

