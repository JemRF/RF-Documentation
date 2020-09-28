---
title: PrivateEyePi Integration
keywords: interface, integrate, integration, PrivateEyePi
last_updated: Sep 28, 2020
tags:  
summary: "This page explains how to integrate our RF Modules with PrivateEyePi"
sidebar: mydoc_sidebar
permalink: privateeyepi.html
folder: mydoc
---

[PrivateEyePi](projects.privateeyepi.com) is a cloud based alarm and monitoring solution for Raspberry Pi. 

## What you will need
* Any model Raspberry Pi with Python 2 and PIP installed
* [IoT Gateway](iot_gateway.html) for Raspberry Pi or Flex RF Module
* Any [wireless sensor](https://www.jemrf.com/collections/all/rf-sensors)

## What you need to know beforehand:
* How to operate a Raspberry Pi
* You have already set up your [IoT Gateway](iot_gateway.html) and [tested your sensor](sensor_testing.html)
* Some Python programming knowledge is preferable but not mandatory as we provide you with the source code and instruction on how to run it

## Installation

Below are the minimal steps to install PrivateEyePi and run the PrivateEyePi interface for the RF Sensors. More information can be found on their website (projects.privateeyepi.com)

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
  
  