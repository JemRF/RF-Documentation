---
title: "How to build a home alarm system with ESP32 and PrivateEyePi"
tags: 
keywords: iot, gateway, iot gateway, privateeyepi, esp32, alarm, alarm system
sidebar: mydoc_sidebar
permalink: esp32-alarm-system.html
summary: "How to build an alarm system with ESP32 development board and interface to PrivateEyePi"
---

<img src="images/ESP32-Alarm-System-Schematic.png"/>

## What you will need
 - ESP32 Development board. There are many variants available but any one will do. If you plan also connect [JemRF wireless sensors](esp32-jemrf.html) then make sure GPIO pins 16 (TX2) and 17 (RX2) (Serial Port 2) are exposed. 
 - Micro USB to USB 2.0 connector to connect the ESP32 to a PC.
 - A PC is required to load firmware on the ESP32. We will be using the Arduino IDE that has client available for Windows, Mac or Linux.
 - Arduino ESP32 development environment setup (covered in the [previous tutorial](esp32-install.html)).
 - Alarm system switches (reed switches, or any tactile switch circuit that open and closes a circuit - e.g. a motion sensor like [this](https://www.jemrf.com/collections/accessories/products/pir-motion-sensor)), and some wire.
  - [Prototyping breadboard](https://www.jemrf.com/collections/accessories/products/400-point-prototyping-breadboard) (optional). 
 
 {% include note.html content="Although the above diagram has only two alarm switches, you can connect as many switches as there are digital inputs on your ESP32 development board."%}

## What you need to know
 - Some basic low voltage electrical experience is advantageous but not necessary. The electrical construction is very basic and could be achieved with no knowledge of electronics.
 - Some basic programming knowledge and prior experience with the Arduino IDE. Again not absolutely necessary but it will make the learning curve a bit easier. 

## Step 1 - Connect switches to the ESP32 Development Board

Following the wiring shown in the top picture connect the two connectors of the tactile switch. One wire goes to a free `GPIO` pin labeled `DXX` on the ESP32 Development Board (any one will do), and the other wire goes to GND. The ESP32 Development Board has two GND connectors you can use. If you have multiple switches then connect all the GND wires together (as shown with the two black wires in the picture) and connect to a single GND on the ESP32 Development Board.

## Step 2 - Configure the sketch with your WIFI and PrivateEyePi details

In the [previous tutorial](esp32-install.html) we showed you how to setup up the development environment and you downloaded the [JemRF RFLIB](https://github.com/JemRF/rflib) library. Now open up the `privateeyepi` sketch from the `examples` folder (**File->Examples->rflib-master->privateeyepi**).

{% include note.html content="If you do not see the `rflib-master` example folder then you may not have shut down the Arduino IDE and started it up again."%}

<img src="images/open-privateeyepi-sketch.png"/>

Now save a copy of the example sketch by selecting **File->Save As** from the main menu and giving it a new name. This will create a new folder in your Arduino directory with the name you gave to it, as well as an .ino file in the new directory.

Near the top of the sketch you will see the following code:

```
{% raw %}
const char* pep_token = ""; //Enter your PrivateEyePi token between quotes
const char* ssid      = ""; //Enter your WIFI router SSID between quotes
const char* password  = ""; //Enter your WIFI password SSID between quotes
//Enter wired sensors here
//Add ,{xx,'s',0} settings for every wired sensor whee xx is the GPIO number
//GPIO 15 and 19 are configures as follows:
uint8_t wired_sensors[20][3] = {{15,'s',0},{19,'s',0}}; 
{% endraw %}
```

Make the following changes:
1. Enter your PrivateEyePi token in between the quotes after `pep_token =`.

{% include note.html content="You need to [configure a PrivateEyePi account](http://projects.privateeyepi.com/home/home-alarm-system-project/installation/register-user-andpassword) if you have not done so already."%}

2. Enter your WIFI SSID name in between the quotes after `ssid =`. The SSID is the name your WIFI router advertises.
3. Enter your WIFI password in between the quotes `password =`.
4. Lastly change the following line to reflect the GPIO numbers you want to connect to reed switches. 

```
{% raw %}
uint8_t wired_sensors[20][3] = {{15,'s',0},{19,'s',0}}; 
{% endraw %}
```

For example in the picture at the top of this tutorial the two switches are connected to `D25` and `D33`. Therefore you would change the configuration to be the following:

```
{% raw %}
uint8_t wired_sensors[20][3] = {{25,'s',0},{33,'s',0}}; 
{% endraw %}
```

If you wanted to have three switches and add another switch to `D32` then you would change the configuration to the following:

```
{% raw %}
uint8_t wired_sensors[20][3] = {{25,'s',0},{33,'s',0},{32,'s',0}}; 
{% endraw %}
```

## Step 3 - Load the privateeyepi sketch onto the ESP 32 Development Board

Click the right arrow button near the top left of the Arduino IDE.

<img src="images/esp32-download-sketch-button.png"/>

The sketch will compile and you will a green progress bar as it is loaded onto the ESP32 Development Board. Once the upload is complete you will see `Done uploading.` in the status bar.

## Step 4 - Test the alarm system

Click the serial monitor on the top right of the Arduino IDE and observe the messages on the screen. 

<img src="images/esp32-serial-monitor.png"/>

Set the baud rate to `9600` using the drop down box on the bottom right of the monitor window:

<img src="images/arduino-monitor-baud-rate.png"/>

Push the `EN` button the ESP32 Development Board to reset the device.

<img src="images/esp32-reset-board.png"/>

 Monitor the progress as it logs into your WIFI router and configures the switches you configured in Step 2. You should see something like this:
 
 <img src="images/esp32-monitor-startup.png"/>
 
  Open and close one of the your switches to confirm that the device is able to detect the open/close and data is being sent OK to PrivateEyePi. You should see something like this:
 
 <img src="images/esp32-door-open-close.png"/>
 
Lastly log in to PrivateEyePi and verify the switch status indicators are changing from green to red as the switches open.

<BR>
<p style="text-align: left"><a href="esp32-install.html"><- Back</a></p> <p style="text-align: right"><a href=" esp32-temperature.html">Next - Build Temperature Monitor -></a></p>