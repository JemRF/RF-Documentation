---
title: The JemRF WIFI Sensor Pro Offline Usage
keywords: getting started introduction
last_updated: Sept 20, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-offline.html
folder: mydoc
---

## Interfacing JemRF WiFi Sensor Pro
If you want to monitor the JemRF WiFi Sensor Pro with your own applications, offline from the Internet there are two options.

### Here is how you do it:

Be sure to connect your sensor to your WIFI network.If you don't know how to do that look [here](/wifi-iot-setup.html) first.

### Get sensor readings.
The JemRF S32 WiFI Sensor has the option for serveral different sensors.

#### To see a web page of the all the onboard sensors in a web page enter:\

/sensors after the network address of your sensor, like:\
If the ip-address of your sensor is 192.168.0.25, then type the following into a browser: http://192.268.0.25/sensors.


The http://your-ip-address/sensors page will return the following:
{% include image.html file="jemrf32sensorreadings.jpg" alt="Sensor list"%}

#### To get Sensor results as JSON

/sensors?json=1

The current readings as shown in the web page above, will be returned as:\
```
{
  "DS18B20": {
    "283d2b44": {
      "Value": 81.8375,
      "Unit": "F"
    }
  },
  "HTU21D": {
    "Temperature": {
      "Value": 78.07647,
      "Unit": "F"
    },
    "Humidity": {
      "Value": 40.63849,
      "Unit": "%"
    }
  },
  "Relay": {
    "1": "OFF",
    "2": "OFF"
  }
}
```

You can change the readings between Celsius or Fahrenheit using the configuration setting on the Config menu of the sensor.

### The onboard Relays

There are two electronic switches used to control external 5 volt relays.\
The relay switches can be externally commanded on and off using  the following commands:\
relayoff and relayon followed by the ID of the relay 1 or 2.\

http://192.168.4.1/relayoff?relay=1   will turn Relay 1 switch Off

If successful it will report:  "Relay: 1 was turned Off"

http://192.168.4.1/relayon?relay=1    will turn Relay 2 switch On

If successful it will report: "Relay: 2 was turned On"


