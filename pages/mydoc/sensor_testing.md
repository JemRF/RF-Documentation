---
title: Sensor Testing
keywords: test, testing, install, installing
last_updated: July 3, 2016
tags:  
summary: "This page explains how to test your wireless sensor. We will cover all our RF sensor types."
sidebar: mydoc_sidebar
permalink: sensor_testing.html
folder: mydoc
---

{% include note.html content="
Before following these steps make sure you have already setup and
 [configured the Gateway](iot_gateway.html) and are familiar with how to [install and remove the sensor battery](sensor_installation.html).  
" %}

1. Open a terminal window on the Raspberry Pi where the Gateway is installed.

1. Download the serial monitor application:

```
git clone https://github.com/JemRF/rf_tools.git
```

1. Run the serial monitor

```
python serial_mon.py 
```

The serial monitor is now running. Any messages received by the Gateway's radio will be displayed on the screen. You can exit the serial monitor anytime by pressing ctrl-c.

1. Insert the battery into the sensor with the flat side (+ve) facing upwards. The sensor will send 5 STARTED-- messages followed by a 5 second pause and then it will go to sleep.

{% include note.html content="
If you have a wireless switch do not open/close the switch during the first 5 seconds as this will cause the device to start sending messages and cancel the startup sequence and prevent the device from entering sleep mode.  
" %}

{% include important.html content="
Make sure the sensors more than 5 feet away from the receiver when testing otherwise you may miss some or all RF messages  
" %}

The following sections cover the sensor data that will be displayed for each type of sensor. Each example shows the sensor reading(s) before going to sleep. We have configured the sensors to send a reading every 5 minutes. If you wait for 5 minutes then the sensor will awake from sleep and send another temperature reading and then go back to sleep. You can configure the interval to another setting if you wish ([see sensor configuration section of this documentation](configuration_overview.html)).


### TEMPERATURE SENSOR

```
python serial_mon.py 9600

Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--

...5 second pause...

Sat Oct 28 20:57:36 2017 02 TMPA22.05
Sat Oct 28 20:57:36 2017 02 SLEEPING-
```

### TEMPERATURE and HUMIDITY SENSOR

```
python serial_mon.py 9600

Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--

...5 second pause...

Sat Oct 28 20:57:36 2017 02 TMPA22.05
Sat Oct 28 20:57:36 2017 02 HUM56.55-
Sat Oct 28 20:57:36 2017 02 SLEEPING-
```

### PRESSURE, TEMPERATURE and HUMIDITY SENSOR
```
python serial_mon.py 9600

Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--

...5 second pause...

Sat Oct 28 20:57:36 2017 02 TMPA22.05
Sat Oct 28 20:57:36 2017 02 HUM56.55-
Sat Oct 28 20:57:36 2017 02 PA1001.55-
Sat Oct 28 20:57:36 2017 02 SLEEPING-
```

### SWITCH SENSOR, MOTION SENSOR, or WATER SENSOR

```
python serial_mon.py 9600


Sat Oct 28 21:05:03 2017 02 STARTED--
Sat Oct 28 21:05:03 2017 02 STARTED--
Sat Oct 28 21:05:03 2017 02 STARTED--
Sat Oct 28 21:05:03 2017 02 STARTED--
Sat Oct 28 21:05:03 2017 02 STARTED--
Sat Oct 28 21:05:06 2017 02 STATEOFF-
Sat Oct 28 21:05:07 2017 02 SLEEPING-
```

In the above example the sensor sent the state of the switch (a02STATEOFF-) before going to sleep. Every time the switch changes state (ie: opens or closes) then the sensor awakens from sleep and transmits the new state of the switch.

Try testing this by closing and opening the switch or bridging the contacts shown in the picture below. This will also work if your sensor is configured for Temperature sensing.

{% include image.html file="switch contacts.webp" alt="Switch contacs"%}

**Red circle shows the button switch contacts**

Messages transmitted when contacts bridged (switch closed):

```
Sat Oct 28 21:50:41 2017 02 AWAKE----
Sat Oct 28 21:50:41 2017 02 BUTTONON-
Sat Oct 28 21:50:41 2017 02 BUTTONON-
Sat Oct 28 21:50:41 2017 02 SLEEPING-
```

Messages transmitted when contacts not bridged (switch open):

```
Sat Oct 28 21:50:43 2017 02 AWAKE----
Sat Oct 28 21:50:43 2017 02 BUTTONOFF
Sat Oct 28 21:50:43 2017 02 BUTTONOFF
Sat Oct 28 21:50:43 2017 02 SLEEPING-
```

{% include note.html content="
In the above example two BUTTONON/OFF messages are sent every time the switch state changes. This is merely precautionary in case one message is missed by the receiver. The number of messages can be configured using the NOMSG command (see the sensor configuration section of this documentation for more details).  
" %}

### LIGHT SENSOR

Messages transmitted when sensor is started:

```
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--
Sat Oct 28 20:57:31 2017 02 STARTED--

...5 second pause...

Sat Oct 28 20:57:36 2017 02 ANAA1456-
Sat Oct 28 20:57:36 2017 02 SLEEPING-
```

Messages transmitted every 5 (or INTVL) minutes thereafter.

```
Sat Oct 28 21:50:43 2017 02 AWAKE----
Sat Oct 28 21:50:43 2017 02 ANAA1456-
Sat Oct 28 21:50:43 2017 02 ANAA1456-
Sat Oct 28 21:50:43 2017 02 SLEEPING-
```

ANAA refers to Analog Sensor A.

1456 is the light reading.

To change the interval of the transmissions (or other configurations) refer the configuration section of this documentation.

