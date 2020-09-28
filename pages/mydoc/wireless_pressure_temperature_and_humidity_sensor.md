---
title: Wireless Pressure, Temperature and Humidity Sensor
keywords: wireless temperature, temperature, sensor, 10k, thermistor
last_updated: Sep 28, 2020
tags:  
summary: "This page explains the JEMRF Wireless Pressure, Temperature and Humidity Sensor"
sidebar: mydoc_sidebar 
permalink: wireless_pressure_temperature_and_humidity_sensor.html
folder: mydoc
---

<img src="images/temperature and humidity sensor 1 smallSep 28, 2020" width="425"/>

<img src="images/BME280 Pressure, Humidity and Temperature smallSep 28, 2020" width="425"/>

## Product Description
Wireless environmental sensor with temperature, barometric pressure and humidity. The sensor provides a high degree of accuracy (+-3% humidity, +-1hPa and 1C). Very low power and can last 6 months on a single CR2032 coin cell battery when configured to send readings every 10 minutes. 

## Installation
Install battery and close enclosure as described [here](sensor_installation.html).

## Sensor testing
* See the [testing section](sensor_testing.html) of this documentation 

## Product Specifications
* +-1hPa barometric pressure accuracy
* ~1°C temperature accuracy
* +-3% humidity accuracy
* Based on BOSCH BME280 sensor
* [Device specifications](rf_device_specs.html)

### Electrical
* 2.2-3.3V 
* Powered by CR2032 coin cell battery
* Can be externally powered by soldering to the 3V3 and GND through holes on the PCB

### Functional
* Standard JemRF wireless sensor, refer [RF Communications section](rf_basics.html) for all the details
* [Highly configurable](configuration_overview.html)
* If the RF module cannot find the BME280 sensor then it will report back (NOSENSOR). Check the wiring and power to the BME280 module.


### Messaging details

Unlike all our other sensors, this sensor transmits illegible raw data from the BME280 over 5 [LLAP](rf_message_format.html) messages. Each message follows the traditional message format of start character, followed by the ID and then 9 bytes of data.  Data from this sensor is transmitted 40 bytes in total and shown in the table below:

{% include image.html file="BME280 message details.PNG" alt="BME280 message details"%}

The host application needs to decode the 40 bytes to derive the pressure, temperature and humidity. Our [RF Tools](utilities.html) have been updated to do this conversion and output the following standard LLAP messages:

* PA9999.9- (pressure reading in hPa)
* TMPA99.99 (temperature reading in Celcius)
* HUM99.99 (humidity reading in %)
* BME280 (the BME280 command requests the sensor to transmit a pressure, temperature and humidity reading)

{% include warning.html content="Upgrade to the latest [RF Tools](utilities.html) that are compatible with this sensor. If you are using an older version of serial_mon.py, or another serial monitor application, then you will see the 5 messages of raw data which is meaningless without conversion." %} 

{% include note.html content="You can find the python code for the conversion in bme280.py for an example of how to do the conversion." %} 

**If you are interested in writing your own code for this sensor then the following will help, but as long as you are using our [utilities](utilities.html) then all of this is irrelevant.**

```
“BMP--” is the marker for the start of a BME280 sensor reading. The 40 bytes, indicated in red in the above diagram, represent the data elements from the sensor. In this manual we will not go into the conversion of these data elements to the actual temperature, humidity and pressure readings but these details can be found in bme280.py, or in the Bosch BME280 datasheet. When the number of messages (NOMSG) setting is set to more than 1 then duplicates need to be removed before decoding the 40 bytes. Refer rflib.py for an example on how to remove
duplicates. It is recommended to use a NOMSG setting of 2 or 3 to improve transmission reliability. We have incorporated bme280.py into our utilities (serial_mon.py and rf_config.py) so that BME280 sensor data is converted to a standard human readable radio message format shown above.
```

{% include note.html content="You may be wondering why we decided to transmit raw sensor data over the air instead of doing the conversion on the radio device before transmission. The reason for this is due to the computational overheads (i.e. memory) required to perform the conversion is beyond what we can afford in the RF module." %} 

### Physical
* 51mm x 36mm x 20mm case size (2" x 1.42" x .79") 

## Default configuration
* Type 9 ([Type](types.html) 9 sensor)
* NOMSG1 (Sends 1 set of 5 LLAP messages with sensor raw data)
* INTVL005 (Sends a temperature reading every 5 minutes)
* CYCLE (put the device into a [timed sleep cycle](sleep_modes.html))
* Refer [device configuration](configuration_overview.html) for more details


