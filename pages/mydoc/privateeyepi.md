---
title: PrivateEyePi Integration
keywords: interface, integrate, integration, PrivateEyePi
last_updated: Mar 4, 2022
tags:
summary: "This page explains how to integrate our RF Modules with PrivateEyePi"
sidebar: mydoc_sidebar
permalink: privateeyepi.html
folder: mydoc
---

[PrivateEyePi](https://projects.privateeyepi.com) is a cloud based alarm and monitoring solution for Raspberry Pi or Orange Pi.

## What you will need
* Any model Raspberry Pi with Python 2/3 and PIP installed
* [IoT Gateway](iot_gateway.html) for Raspberry Pi or Flex RF Module
* Any [wireless sensor](https://www.jemrf.com/collections/all/rf-sensors)

## What you need to know beforehand:
* How to operate a Raspberry Pi or Orange Pi Zero V2
* You have already set up your [IoT Gateway](iot_gateway.html) and [tested your sensor](sensor_testing.html)
* Some Python programming knowledge is preferable but not mandatory as we provide you with the source code and instruction on how to run it

## Installation

Below are the minimal steps to install PrivateEyePi and run the PrivateEyePi interface for the RF Sensors. More information can be found on the website (projects.privateeyepi.com)

{% include note.html content="Follow [this link](orangepi.html) to setup an Orange Pi Zero 2 to run PEP Applications."%}

{% include important.html content="The current Application downloads are for Python 3, they also include the older Python 2 for reference."%}

1. If you have not already installed PrivateEyePi, do so as follows:

    Open a command prompt on the Raspberry Pi and create a directory for PrivateEyePi:

    E.g.

    ```
    cd /home/pi
    mkdir pep
    cd pep

    wget -N www.privateeyepi.com/downloads/install.sh
    ```

2. Create an account on PrivateEyePi
    The following steps must be completed on a web browser:
    * Go to www.privateeyepi.com website
    * Click on the "New User" link
    * Type in the details and click the "Update" button
    * From the User menu option create a new token and copy it to your clipboard

3. Copy the token to the globals.py file
    ```
    cd /home/pi/pep
    sudo nano globals.py

    Look for token="" and paste the token in between the braces.

    Save using Ctrl-x followed by 'y'

    ```
 4. Run rfsensor.py

    ```
    python rfsensor.py
    ```

