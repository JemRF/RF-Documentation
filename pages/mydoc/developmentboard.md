---
title: Development Board
keywords: Flex, General purpose, Development, prototyping
last_updated: Mar 2, 2022
tags:
summary: "This page is the JemRF FLEX Development board"
sidebar: mydoc_sidebar
permalink: developmentboard.html
folder: mydoc
---
{% include image.html file="devboard1.jpg" alt="Development Board"%}

## Product Descriptions
The Development Board was designed to work with the [FLEX Module](flex.html) providing a 20 pin header for FLEX RF Module.
It provides maximum access to all the feature with the Flex Module.
For a wide range of prototyping options.

## Product Specifications
* The PCB is mounted in the case via two supplied screws
* The elegant cream colored case
* The case has vents to allow for environment monitoring (temperature humidity)
* 20 pin header for FLEX RF Module (Flex RF Module sold separately)
* 2 breadboard arrays of 6 rows with 5 connections each
* Power and Ground strips, each with 6 connections.
* Power Select for 1.5 volt, 3.3 volt or 5 volt power.
* Can use power from USB interface for the 3.3 and 5 volt needs.
* Can operate on a 1.5 volt AA battery and provide 1.5 and 3.3 or 5 volts.

{% include image.html file="devboard1layout.jpg" alt="Development Board Layout"%}

### Electrical
* Power options are 1.5V, 3.3V and 5V through three different power converters:
  - 1.5V to 3.3V converts 1.5V from the on board AA battery to 3.3V required for the FLEX RF Module, or
  - 5V to 3.3V converts 5V from the on board mini USB port to 3.3V required for the FLEX RF module. You need an external power supply via a USB cable for this option (e.g. an old phone charger)
  - 1.5V to 5V (sold separately) converts 1.5V to 5V for any sensors that require 5V. This converter will only supply the prototyping area, so you will also need the 1.5V to 3.3V converter to power the FLEX RF Module

### Functional
* Socket for Dallas DS18B20 one-wire digital thermonitor Sensor
* Socket for DHT22 one-wire thermonitor and humidity Sensor
* Connections for Analog A and Analog B (Like a light sensor)
* Connections for three GPIO I/O Pins
* Connections for Relay A and Relay B (GPIO I/O Pins to drive a Relay/LED)
* Connections for the Serial Tx/Rx interfaces.
* Connections for a 10K thermistor or 10K light sensor
* The Power rail is connected to the jumper block for selecting 1.5. 3.3 pr 5 volt power.
* The FLEX RF module will run for years on a single AA battery when in deep sleep mode. When the module is fully awake then it will last a few days on a AA battery. See section 14 of the manual for more details.

### Physical
* 68mm x 50mm PCB size (2 11/16" x 1 15/16")
* Case dimensions 2.91"(74mm) x 2.16"(55mm) x 1.10"(28mm)
* Pin spacing 2.54mm (0.1")

