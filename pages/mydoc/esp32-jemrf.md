---
title: "ESP32 PrivateEyePi - Install tutorial"
tags: 
keywords: iot, gateway, iot gateway, privateeyepi
sidebar: mydoc_sidebar
permalink: esp32-jemrf.html
summary: "How to install the PrivateEyePi sketch on ESP32 development board to interface to PrivateEyePi"
---

## What you will need
 - ESP32 Development board. There are many variants available but make sure GPIO pins 16 (TX2) and 17 (RX2) (Serial Port 2) are exposed. The ESP32 has two hardware serial ports and we will be using Serial Port 2 to connect the Flex RF module, so that you can use Serial Port 1 for debugging.
 - [FlexRF Module](https://www.jemrf.com/collections/rf-sensors/products/flex-rf-module) (optional if you want to interface JemRF wireless sensors). 
 - [Breadboard](https://www.jemrf.com/collections/accessories/products/400-point-prototyping-breadboard)(optional if you want to interface JemRF sensors) for easy installation. Both the ESP32 Development Board and the Flex Module are designed for prototyping breadboards but, of course, could be soldered together if that is your preference. 
 - [Jumper wires](https://www.jemrf.com/collections/accessories/products/jumper-wires)
 - Micro USB to USB 2.0 connector to connect the ESP32 to a PC
 - A PC is required to load firmware on the ESP32. We will be using the Arduino IDE that has client available for Windows, Mac or Linux.

## What you need to know
 - Some basic low voltage electrical experience is advantageous but not necessary. The electrical construction is very basic and could be achieved with no knowledge of electronics.
 - Some basic programming knowledge and prior experience with the Arduino IDE. Again not absolutely necessary but it will make the learning curve a bit easier. 

## Step 1 - Install and configure the Arduino Integrated Development Environment
 - Visit the [Arduino site](https://www.arduino.cc/en/software) and download and install the software. Follow their guide for installation. Its quite easy to install - next, next, finish etc.. They also have a very well documented [getting started guide](https://www.arduino.cc/en/Guide) that will help you if required. Note that the Arduino IDE is primarily designed for their Arduino ATMega platforms but they also support a number of other development boards, including ESP32! 
 
 {% include note.html content="We chose the Arduino development environment primarily for this tutorial because of its ease of use, but you can also program the ESP32 on Lua or Micro-Python, but we do not provide the software for those platforms."%}
 
 - In the Arduino IDE go to **File->Preferences and enter:<br>**
 `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`
 
<img src="images/preferences.png" style="width:400px;height:400px;"/>

{% include note.html content="If you already have other preferences in the input box then you can separate the URLs with a comma."%}
 
 - Open the Boards Manager and select the `ESP32 Dev Module`  **Tools->Boards->Boards Manager...** and click **Install**
 
 <img src="images/esp32 boards manager.png"/>
 
  - Select the board **Tools->Board->ESP32 Dev Module**

<img src="images/esp32 dev module.png"/>

 - Connect the ESP32 to the PC using the USB cable then select the port **Tools->Port** and then select the COM port from the list. 

{% include note.html content="The COM port number will vary. I am using COM port 7 but your will likely be a different number."%}

<img src="images/ESP32-port.png"/>

Thats it! Now you are ready to load firmware onto the ESP32 Development Board.

## Step 2 - Download the JemRF Arduino software

 - Download the library from here: [https://github.com/JemRF/rflib.git](https://github.com/JemRF/rflib.git)
 
  <img src="images/download jemrf.png"/>
 
 - Open up the Arduino IDE and click on **Sketch->Include Library->Add** .ZIP library and select the library downloaded in the previous step
 
 <img src="images/add zip file.png"/>
 
 - Close all instances of the Arduino IDE and restart the IDE

<BR>
<p style="text-align: left"><a href="esp32-temperature.html"><- Back</a></p> <p style="text-align: right">