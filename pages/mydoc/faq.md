---
title: Frequently Asked Questions
keywords: help, trouble, faq, tip, tips, 
last_updated: Oct 1, 2020
tags:  
summary: "This page contains frequently asked questions and answers"
sidebar: mydoc_sidebar
permalink: faq.html
folder: mydoc
---

## Frequently asked questions

### What do I do if a sensor stops communicating?
 - If all your sensors are not communicating then it is likely an issue with the IoT Gateway

 - Check the battery

If you have your sensors communicating to PrivateEyePi you can check the battery status on the dashboard by doing a mouse over on the battery indicator. You will see the last time the battery voltage was recorded as well as the last known voltage. If the value is below 2.2V then a new battery is required.

 - Check distance between sensor and receiver

Reduce the distance between the sensor and the receiver to see if that resolved the issue. Do not put the sensor within 5 feet of the receiver because that will result in lost messages.

 - Do a communication check

The best way to perform a communications check is to using the serial monitor ([serial_mon.py](utilities.html)). Open up a terminal windows on you Raspberry Pi and go to the rf_tools directory you created during the IoT Gateway.

 - Move the problematic sensor within line of sight of the IoT Gateway and either wait for a transmission to occur or force a transmission by opening closing the switch (for rf switch) or removing and re-inserting the battery (also see "Why doesn't my sensor restart when I remove and re-insert the battery" below too).

When the sensor starts up you should see:
```
aXXSTARTED
```

 - Depending on the type of the sensor you will see sensor data being transmitted (e.g. aXXTMPA23.40 or aXXBUTTONON, aXXAWAKE, aXXSLEEPING)

 - Now move the sensor further away repeating this test so you can find best placement for the gateway and receiver.

### What is causing a flood of "STARTED" messages in serial_mon?

 - The most likely cause of this is a low battery from one of your sensors. When the battery runs low this causes the device to restart continuously because it is unable to maintain a charge to stay alive.


### What to do I do if I have lost contact with my IoT Gateway

 - This is most frequently caused by a configuration sent to the gateway (e.g. CHDEVID which changes the device ID, or frequency, channel or PanID were changed). You can fix this by resetting your IoT Gateway back to factory setting using the RESET command:

```
python rf_config.py RESET -V
```
 
### Why doesn't my sensor restart when I remove and re-insert the battery?

- The sensors have a capacitor that can retain a charge that keeps the sensor alive. Removing the battery does not discharge the capacitor. You can safely discharge the capacitor by removing the battery and then shorting the 3V and GND marked pads. Alternately you can remove the battery and wait a few minutes for the capacitor to discharge naturally.

### My IoT Gateway does not appear to be working
### or get the following error: "Permission denied: /dev/ttyAMA0"
### or get the following error: "Inappropriate ioctl for device"
 - Run serial_mon.py and power up a sensor (making sure the sensor is more than 3 feet away from the gateway). If you see STARTED messages then the Gateway is likely working. 
 - Make sure you have [configured the serial port correctly](configure_serial_port.html)
 - Check if there are multiple applications using the serial port. Only one application can use the serial port at a time. Do a "ps ax" and look for other programs like rfsensor.py or serial_mon.py using the serial port. You can kill background processes using the "sudo kill [pid]" command. If you have a cron job configured to autostart rfsensor.py then disable the cron job (sudo service cron stop). 
 - Check the serial port is installed (dir /dev) and look for the ttyAMA0 port. If it is not installed then revert back to the serial port configuration in point 1 above. 
 - Do a loop-back test to test if the port is working