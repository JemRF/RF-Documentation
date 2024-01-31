---
title: "RF Sensor Introduction"
keywords: getting started introduction
last_updated: Jan 30, 2024
sidebar: home_sidebar
permalink: rfintroduction.html
summary: JemRF radio modules are easy to use wireless data transmission modules where all the error checking, encoding, packetization and CRC done for you. Build prototypes in minutes. Requires no programming and no drivers. Long range communication up to 1 KM within line of sight. Supports point-to-multi-point, multi-point-to-point, multi-point-to-multi-point or point-to-point network topologies. All devices have built-in 128-bit AES encryption for secure over the air transmissions.The devices are configurable through the serial interface or over the air.
---
## Using RF Devices
Click here: [For overview of getting started using JemRF RF devices](getting_started.html).

## Introduction to RF Networks
The different network topologies the JemRF RF sensors support.

### Star Network
Any number of nodes transmitting and receiving data from one central hub. Sensor nodes can sleep to
conserve battery power. No direct communication between the sensor nodes.

{% include image.html file="Slide1.jpg" alt="Star Network"%}

### Multiple Star Networks
Start networks can be combined by creating multiple star networks on their own PanId’s. Messages can
be directed to specific gateways by assigning PanId’s to each sensor.

{% include image.html file="Slide2.jpg" alt="Multiple Star Networks"%}

### Redundant network
Multiple gateways can be configured on the same PanId to create a redundant network. All radio traffic
travels to all gateways so if you lose a gateway then you have a hot backup. Additional gateways can also
be installed in areas of poor reception to improve network coverage. Message de-duplication logic must be
built either within the gateway or further down in back end systems connected to the network.

{% include image.html file="Slide3.jpg" alt="Redundant Network"%}

### Point-to-point Communications
Two or more MCU’s can communicate directly with each other as shown below.
{% include image.html file="Slide4.jpg" alt="Point-to-Point"%}