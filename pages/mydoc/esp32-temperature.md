---
title: "ESP32 PrivateEyePi - DS18B20 Temperature Sensor tutorial"
tags: 
keywords: iot, gateway, iot gateway, privateeyepi, ds18b20
sidebar: mydoc_sidebar
permalink: esp32-temperature.html
summary: "How to create a temperature sensor with the ESP32 Development Board and DS18B20 temperature sensor and display it on the PrivateEyePi dashboard"
---

<img src="images/privateeyepi-temperature.png"/>

{% include note.html content="This is the third tutorial in the series. Please ensure you have [setup the ESP32 development environment](esp32-install.html) and have downloaded the `privateeyepi` sketch (steps 2 and 3 of [alarm system tutorial](esp32-alarm-system.html))"%}

## What you will need
 - ESP32 Development board. There are many variants available but make sure GPIO pins 16 (TX2) and 17 (RX2) (Serial Port 2) are exposed. The ESP32 has two hardware serial ports and we will be using Serial Port 2 to connect the Flex RF module, so that you can use Serial Port 1 for debugging.
 - [Breadboard](https://www.jemrf.com/collections/accessories/products/400-point-prototyping-breadboard)(optional if you want to interface JemRF sensors) for easy installation. Both the ESP32 Development Board and the Flex Module are designed for prototyping breadboards but, of course, could be soldered together if that is your preference. 
 - [Jumper wires](https://www.jemrf.com/collections/accessories/products/jumper-wires).
 - Micro USB to USB 2.0 connector to connect the ESP32 to a PC.
 - A PC is required to load firmware on the ESP32. We will be using the Arduino IDE that has client available for Windows, Mac or Linux.
 - A [DS18B20 sensor](https://www.jemrf.com/collections/accessories/products/ds18b20-dallas-1-wire-digital-temperature-sensor-and-resistor), or [DS1820 waterproof sensor](https://www.jemrf.com/collections/accessories/products/copy-of-ds18b20-dallas-1-wire-digital-temperature-sensor-and-resistor). 
 - 4.7k Ohm resistor.

## What you need to know
 - Some basic low voltage electrical experience is advantageous but not necessary. The electrical construction is very basic and could be achieved with no knowledge of electronics.
 - Some basic programming knowledge and prior experience with the Arduino IDE. Again not absolutely necessary but it will make the learning curve a bit easier. 
 
## Step 1 - Wiring
 - The DS18B20 sensor has three connections : VDD, DATA and GND. As per the following picture make the four connections between the DS18B20 sensor and the ESP32 Development Board:
 
    <img src="images/esp32-ds18b20.png"/>
 
 1. Connect ESP32 GND to the leftmost pin on the DS18B20 (or the black wire on waterproof sensor).
 2. Connect ESP32 D4 pin to the middle pin on the DS18B20 (or yellow wire on the waterproof sensor).
 3. Connect ESP32 3V3 pin to the rightmost pin on the DS18B20 (or red wire on the waterproof sensor).
    <img src="images/ds18b20.png"/>
    <BR><BR>
 4. Connect the 4.7k Ohm resistor between VDD and DATA.
    <BR><BR>
    <img src="images/4700ohms-resistor.png"/>
 
 <img src="images/esp32-ds18b20-wiring.png"/>
 
## Step 2 - Install the DallasTemperature library

 - Open the Arduino IDE and select **Sketch->Include Libraries->Manage Libraries** option.
 
<img src="images/arduino-include-library.png"/>
 
  - Search for the `DallasTemperature` or `DS18B20` library and then click `Install`

<img src="images/esp32-ds18b20-library.png"/>

## Step 3 - Configure the `privateeyepi` sketch
 
  - Open File Explorer (or your equivalent file manager on your OS) and open up `~\Adruino\Libraries\rflib-master\pep.h` with your favorite file editor.
  - Look for the following line near the top:
  
  ```
  //#define DS18B20
  ```
  
  - Remove the `//` and save the file. Removing this tells the compiler to include the DS18B20 library in the compile.
  - You can also configure the send frequency using the line below:
  
  ```
  #define DS18B20_INTERVAL 300000 //5 minutes
  ```
  - The default interval that temperature readings are sent to PrivateEyePi is 5 minutes (or 300000 ms). You may want to lower it to make testing easier, but **be sure to set it back to 5 minutes otherwise the PrivateEyePi server could lock your account if you send too many readings per minute.**
  - Connect your ESP-32 Development Board to the USB connected to your computer. 
  - Open up your `privateeyepi` sketch you created in [step 2 of the previous tutorial](esp32-alarm-system.html) and click the upload button in the Arduino IDE.

<img src="images/esp32-download-sketch-button.png"/>


  - Once the sketch has loaded then open up the Arduino serial monitor by clicking magnifying glass icon on the top right.
  
<img src="images/esp32-serial-monitor.png"/>
 
  - Press the reset button on the ESP32 Development Board.

<img src="images/esp32-reset-board.png"/>

 - Check whether the DS18B20 sensor is being detected. You should see something like this:

<img src="images/esp32-ds18b20-startup.png"/>

{% include note.html content="As you can see in above picture, we have wired two DS18B20 sensors. You can see how to wire multiple DS18B20 sensors later in this tutorial."%}

 - Highlighted in red above you can see that two sensors were detected and the sensor unique identifier is also highlighted in red. This is the identifier used as the sensor number to send to PrivateEyePi. 
  
 - Verify that the data is being sent to PrivateEyePi correctly.
 
 <img src="images/esp-32-ds18b20-privateeyepi.png"/>
 
## How to wire multiple DS18B20 sensors to an ESP32 Development Board

One of the great advantages of the DS18B20 sensor is its ability to wire them together and share the same single data wire. Each DS18B20 sensor has a unique 64bit address burned into the sensor that allows you to address each sensor individually over a common data wire. This allows you to connect as many DS18B20 sensors as you like and only use one GPIO pin on the ESP32 Development Board. 

To add  multiple DS18B20 sensors simply wire them up to the existing circuit you built in Step 1 above. **You do not need to add another resistor.** No other configuration is required in the software. It will automatically detect the new sensor. 

<img src="images/esp32-multiple-ds18b20-wiring.png"/>

 
<BR>
<p style="text-align: left"><a href="esp32-alarm-system.html"><- Back</a></p> <p style="text-align: right"><a href="esp32-jemrf.html">Next - Connect JemRF Sensors -></a></p>