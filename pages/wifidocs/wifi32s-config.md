---
title: The JemRF ESP32 WIFI Sensor Advance Options
keywords: getting started introduction
last_updated: Sept 20, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-config.html
folder: wifidoc
---

## JemRF ESP32 WIFI Sensor Advance Options
Once you have completed the [setup of WIFI Temperature Sensor](/wifi-iot-setup.html) you may be interested in some of the advanced features of the device.

On the "Sensor Config" menu there are a number of options which we will describe further here.


{% include image.html file="wifi-sensor-config.jpg" alt="WiFi Sensor Configuration"%}


### Send To Server
You used this option to tell the sensor to send the reading from the on board DS18B20 temperature or HTU21d temperature and humidity sensor to be sent to the server.  Click the check box to send, and un-click it to stop sending.

Messages to the server send the Sensor ID (for the DS18B20) sensors with their associated temperature.  Message to the server for the DHT22 sensor will send the temperature and humidity will use the WiFi Device ID (the numbers afer **JEM** Name).

If the DS18B20 or DHT22 sensor fails then controller will report a temperature 999  to the server.

### Temperature Send Interval
This is the interval between temperature reading transmissions. For example if set to 300 then the sensor will send a reading every 5 minutes. Take note that if you are using the free PrivateEyePi service then setting it to below 300 may result in you exceeding the maximum daily message allowance. JemRF Monitoring will support 60 second updates.

{% include note.html content="With default value of 0, no messages will be sent to the servers. "%}

### Temperature Calibration

The DS18B20 is accurate from  -55°C to +125°C or Fahrenheit equivalent -67°F to +257°F, ±0.5°C accuracy from -10°C to +85°C.

However you may want to adjust the readings to offset external influences.  Use this option to add or subtract a value from every temperature reading. For example if you set it to 2, then it will add 2 to every temperature reading, or -2 will subtract from every reading.

The on board WIFI chip will generate heat if powered on for long periods of time so you may find that this will skew readings. You can avoid this but using the sleep option described below or work around it by using the temperature calibration option to lower the reading. Another option is to remove the DS18B20 sensor and replace it with an external sensor.

### Display in Fahrenheit

The default temperature reading is in Celsius. Click this option to change the temperature readings to Fahrenheit.

### Static IP Address

Enter the IP Address you wish to allocate to the sensor. This is useful if you are polling the device from another computer and do not want the IP Address to ever change.

### Gateway, Subnet & DNS

These settings are mandatory if you want to set a static IP address. If you do not know the subnet mask and gateway of your router you can easily get it as follows:

Windows - Open a command prompt windows and type ipconfig, then page up and look for Subnet Mask and Gateway

Linux - Open a terminal session and type  netstat -nr. This will give you the Gateway. Now type ifconfig, and look for the Mask.

### ReStart
The ReStart button performs a power restart, needed to set on clear the

Reboot (power off and on) the sensor in order for these settings to take affect.