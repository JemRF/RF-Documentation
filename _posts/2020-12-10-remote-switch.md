---
title: "Remote switch"
tags: 
keywords: remote control, control, switch, flex
sidebar: mydoc_sidebar
permalink: remote-switch.html
summary: "A remote switch constructed using a Flex radio module and developer board"
---

## Description

Below are some pictures of a remote switch project that is used to switch on/off whatever is connected to the power output of the extension power cable. The extension power cable has been cut in the middle and spliced with this remote controlled switch. Useful for controlling lights.

The case is a beautiful weather resistant and rugged project box with transparent case. Inside are a number of components described in the second picture and listed below. 

<img src="images/IMG_0192.jpg" width="425"/>

<img src="images/IMG_0194.jpg" width="425"/>

{% include warning.html content="This project does require knowledge in working with high voltage. If you are not experienced in this regard you should avoid this project or get assistance from a qualified electrician. It should go without saying but I'll say it anyway : High voltages can kill you or cause fires"%}

## Parts

1. Case - Wireless Switch Tool Accessories Case Outdoor Cable IP66 Waterproof Junction Box For Lights Smart Home Practical Wire Connector. [Aliexpress link](https://www.aliexpress.com/item/4000101862722.html?spm=a2g0s.9042311.0.0.27424c4dYoWxCo).
2. [Flex Radio module](https://www.jemrf.com/collections/rf-sensors/products/flex-rf-module).
3. [Wireless developer board](https://www.jemrf.com/collections/rf-sensors/products/wireless-developer-board-case).
4. [110V AC to 5V DC step down](https://www.ebay.com/itm/AC-DC-110V-220V-230V-to-3-3V-5V-9V-12V-15V-24V-Step-Down-Converter-Power-Supply/192281294606?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649).
5. [5v to 3.3V step down](https://www.jemrf.com/collections/accessories/products/dc-5v-to-3-3v-step-down).
6. [Relay Module](https://www.jemrf.com/collections/accessories/products/relay-for-raspberry-pi-or-arduino-1-channel-5v-relay-module-250v-10a).
7. NPN222A transistor.
8. 10k resistor.
9. 2 connector screw terminals.
10. A standard extension power cable that has been cut in half and wires stripped.

## Wiring
This [tutorial](https://www.jemrf.com/pages/how-to-use-the-flex-module-for-remote-control) describes how to use the Flex radio module for remote control and how to construct the circuit. Note that some of the parts in the list above are not displayed in the above picture because the parts are on the underside or the developer board.

## Application integration
See the integration section of the [JemRF Documentation](https://www.jemrf.com/pages/documentation) for details on how to integrate this remote switch with the application of your choice (e.g. Home Assistant, AdafruitIO, Blynk, PrivatetePi, Thingsboard etc...).

## Code
See [this example](https://github.com/JemRF/rf_tools/blob/master/rf2ha.py) code for how to integrate this remote switch with Home Assistant. This will allow you to switch the device on/off from the Home Assistant dashboard and also create automations like switching a light on on sunset and light off on sunrise. 





