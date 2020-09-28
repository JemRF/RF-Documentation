---
title: Sleep Modes
keywords: sleep, battery, cycle, cyclic, cyclic sleep, lifetime, consumption, type, intvl, ,wake, wake up
last_updated: July 3, 2016
tags:  
summary: "This page describes the two sleep modes."
sidebar: mydoc_sidebar
permalink: sleep_modes.html
folder: mydoc
---

Sleep mode is essential to conserve battery life. When the device is sleeping the radio and all non-essential processors and sensors are shut down so they do not consume power. Once asleep there are two events that can cause the device to wake up and transmit data:

1. **A timed cycle** where the device wakes up after a specified interval has expired and a sensor reading is taken, transmitted over the radio, and then sleep mode resumes until the timer expires again and so on.

1. **A switch** is triggered that causes the device to wake up, transmit the event over the radio and resume sleeping. 

## Timed Sleep Cycle Command

There are two commands required to set a timed sleep cycle:

1. **INTVL** - The sleep cycle interval (in minutes)
1. **CYCLE** - The command that tells the sensor to enter a cyclic sleep

The two command in the example below set a timed cycle of 5 minutes:

```
python rf_config.py 03 INTVL005
SENT     : 03INTVL005
RECEIVED : 03INTVL005-

python rf_config.py 03 CYCLE
SENT     : 03CYCLE
RECEIVED : 03SLEEPING-
```

Now every 5 minutes the device will wake up and send the sensor data that is associated with the [sensor's type](types.html).

## Sleep Command

The SLEEP command simply puts the RF module to sleep. The device will wake when the button sensor contacts are bridged on the sensor.

Use the INTVL command to set the interval you want to set for the button state to be sent. When the device is put to sleep using the SLEEP command then it will wake every INTVL minutes to report the state (a03STATEON-- or a03STATEOFF-) of the button contact. 

{% include important.html content="When the button contacts are bridged the device will wake and transmit the event over the radio **regardless of whether the device is in CYCLE sleep mode or SLEEP sleep mode**. This is an important feature of our devices because it allows you to combine functionality of a contact switch based sensor (like a door sensor, motion sensor or water sensor) with a cycle sleep mode sensor like temperature, pressure, humidity and analog. See the [multi-function sensor section](multi_function_sensors.html) of this documentation for more details." %} 

The example below sets the reporting interval to 25 minutes and puts the device to sleep:

```
python rf_config.py 03 INTVL025
SENT     : 03INTVL025
RECEIVED : 03INTVL025-

python rf_config.py 03 SLEEP
SENT     : 03SLEEP
RECEIVED : 03SLEEPING-
```
 
Every 25 minutes the state of the button contact will get reported and the device will also wake and transmit when the button contact is bridged, followed by sleep again. 

{% include note.html content="From Version 7.2 upwards you can use the RBSON command to send button status when device is asleep using the CYCLE command. This is also another feature of [multi-function sensors](multi_function_sensors.html) to be able to report cyclic sensor readings as well as report the button status every INTVL minutes." %}  

{% include important.html content="You cannot communicate with a sensor when it is asleep. The radio will only get activated when it is time to transmit data. See below WAKE command that is used to wake a device from sleep." %}

## WAKE Command

The WAKE command (previously AWAKE command for versions 1 and 2) is used to wake up a sensor. You cannot wake a device without getting physical access to the device to power off and back on (this is a security feature). Once the device is powered back up you have a 5 second internal to issue the WAKE (or AWAKE for version 1 and 2) command.

The steps to wake up a device are as follows:

1. Power off and on the device 
1. Send the WAKE command within 5 seconds: 

    ```   
    python rf_config.py 03 WAKE
    SENT     : 03WAKE
    RECEIVED : 03WAKE-----
    ```

1. Send the HELLO command to check if the device is awake 

    ```   
    python rf_config.py 03 HELLO
    SENT     : 03HELLO
    RECEIVED : 03HELLO----
    ```

Now the device is awake and available for configuration. You can put the device back to sleep using the CYCLE and SLEEP commands described above. 

{% include important.html content="When a device is awake and powered by coin cell battery it will only have a battery lifespan of about 30 minutes. So be sure to be quick when configuring a battery powered sensor. Alternatively give the sensor external power (e.g. two AA batteries) when doing configuration." %}


  

