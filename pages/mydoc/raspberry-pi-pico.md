---
title: Interfacing JemRF radios with Raspberry Pi PICO
keywords: raspberry pi, raspberry pi pico, pico, flex
last_updated: Feb 02, 2021
tags:  
summary: "Step by step instructions explaining how to interface the JemRF Flex module with the Raspberry PI PICO microprocessor"
sidebar: mydoc_sidebar 
permalink: raspberry-pi-pico.html
folder: mydoc
---

<img src="images/raspberry pi pico pinout.png" width="425"/>

## Description
As you can see from the diagram above the Raspberry Pi PICO is a very capable microcontroller board with many interfaces. In this tutorial we will be making use of the Serial Port - `uart0` (pins 1 and 2) by default but you can easily also use pins `uart1` (pins 11 and 12) on the PICO board. We will show you how to download the JemRF software for the PICO board which leverages the [c/c++ Raspberry Pi PICO SDK](https://datasheets.raspberrypi.org/pico/getting-started-with-pico.pdf). There are many different development environment options you can use for development on the Raspberry Pi PICO. If you have not set up a development environment for the Raspberry Pi PICO then please first review the [Raspberry Pi PICO Getting Started](https://datasheets.raspberrypi.org/pico/getting-started-with-pico.pdf) page for details on how to do that. Familiarize yourself with how to compile code and download applications to the PICO module.   

## Wiring

 - Connect pins 15 and 16 of the [JemRF Flex Module](flex.html) to pins 1 and 2 (or pins 11 and 12 for uart1) of the Raspberry Pi PICO. 
 - Connect pins VCC and GND as shown in the diagram. You can power the Flex module from a separate power source if you prefer, but make sure the two modules share the same GND.

<img src="images/Flex RF Module Raspberry Pi PICO.png" width="425"/>

## Download

- Download the library from here: [https://github.com/JemRF/rflib.git](https://github.com/JemRF/rflib.git)
 
 <img src="images/download jemrf.png"/>

 - Unzip the compressed folder into a folder in your Raspberry Pi PICO development environment

## Example code

From the examples folder open up the source code for the Raspberry Pi Pico .cpp file called rfsensor.cpp. This example shows how to set up an application to listen for a specific message from a remote sensor and switch on an LED. Compile the code (refer to the getting started documents from Raspberry Pi if you don't know how to compile), and copy the UF2 file from the `build` directory to Raspberry Pi PICO. 

If you are using `uart1` then you need to change the RX and TX pins that are defined near the top of the rflib.h file.


## RFLIB Libary
This example code uses the RFLIB library, which is described here. You can also look through all the other examples that were written for the Arduino/ESP32 platforms for guides on how to use the RFLIB library. The other examples won't compile for the Raspberry Pi PICO but they will show you how to use the various aspects of the RFLIB library.
