---
title: The Internet Of Things (IOT) WIFI Sensor
keywords: getting started introduction
last_updated: Jan 12, 2024
tags:
summary: "The Internet Of Things (IOT) is where everyday things (cars, homes, household appliances, plants) are being connected to the Internet where we can monitor, control and alert in ways not possible before."
sidebar: wifi_sidebar
permalink: wifi-iot-offline.html
folder: mydoc
---

## Interfacing with the WIFI Sensor
You don't need to use the PrivateEyePi server for collecting sensor readings or controlling the GPIO ports. You may want to send the readings to another server or save it on your own device (like a Raspberry Pi). You can also easily switch the GPIO ports.

### Here is how you do it:

1. Make sure the firmware of your sensor is 1.5 or higher. You can see the firmware version at the bottom of each of the sensor configuration pages. You can upload the latest firmware from here.

2. Connect your sensor to your WIFI network.If you don't know how to do that look [here](/wifi-iot-setup.html) first.
Get temperature readings.
You can get the temperature from the /temp page on the sensor. For example if the ip-address of your sensor is 192.168.0.25, then type the following into a browser: http://192.268.0.25/temp.

The /temp page will return the following:


#### Firmware version less than 1.9.3:

3 values separated by a comma:

e.g. 23.6,NA,NA

Parameter 1 = DS18B20 temperature
Parameter 2 = DHT22 temperature
Parameter 3 = DHT22 humidity

#### Firmware version 1.9.3 onward support the ability to have multiple DS18B20 sensors:

DS18B20
Parameter 1 = DS18B20
Parameter 2 = Sensor Id
Parameter 3 = Temperature

DHT22
Parameter 1 = DHT22
Parameter 2 = Temperature
Parameter 3 = Humidity

Here is an example of the data returned from a WIFI sensor that has 6 DS18B20 sensors

DB18B20, 203151 , 22.62 , DB18B20, 221466 , 22.25 , DB18B20, 203244 , 22.44 , DB18B20, 203145 , 22.81 , DB18B20, 420393 , 22.56 , DB18B20, 214213 , 22.87

Here is an example of the data returned with 1 DHT22 sensor:

DHT22, 23.40 , 45.10

### Write some Python code to fetch the temperature:

cd /home
sudo gettemp.py

Paste, or type the following code. Enter the IP-address of your sensor where it is highlighted in red.

import urllib2
str_data=urllib2.urlopen("http://192.168.0.25/temp").read()
list_data = str_data.split(",")
print "Parameter 1 ="+list_data[0]
print "Parameter 2 ="+list_data[1]
print "Parameter 3 ="+list_data[2]

Press Ctrl-X followed by Y to save

Now run the program by typing:

python gettemp.py


In this example I have 6 DS18B20 sensors  It will print something like this:
Parameter 0=DS18B20

Parameter 1=203151

Parameter 2=22.69

Parameter 3=DS18B20

Parameter 4=221466

Parameter 5=22.31

Parameter 6=DS18B20

Parameter 7=203244

Parameter 8=22.44

Parameter 9=DS18B20

Parameter 10=203145

Parameter 11=22.87

Parameter 12=DS18B20

Parameter 13=420393

Parameter 14=22.62

Parameter 15=DS18B20

Parameter 16=214213

Parameter 17=22.94


You can change the readings  between Celsius or Fahrenheit using the configuration setting on the Config menu of the sensor.

### Using the Web Page Addresses of the WIFI Sensor

You may be interested in knowing the various paths to each of the WIFI sensor we pages.

http://192.168.4.1/ - Login Details screen

http://192.168.4.1/config - Config screen

http://192.168.4.1/log" - Log screen

http://192.168.4.1/clearlog - Clear log

http://192.168.4.1/temp - Screen that outputs only temperature and humidity

Switch GPIO ports.
Only available from version 1.9.3 and above.

Switch GPIO 0 off:

http://192.168.4.1/relayoff?id=0



Switch GPIO 0 on:

http://192.168.4.1/relayon?id=0



Check GPIO Status

http://192.168.4.1/gpiostatus?pin=0

 - Will return 0 if pin is connected to ground (GND) or 1 when not connected to ground