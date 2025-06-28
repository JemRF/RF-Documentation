---
title: "JemRF Smart Gateway"
keywords: getting started maintenance, Smart Gateway Jemrf, Gateway, rf Sensor
last_updated: July 26, 2025
sidebar: wifi_sidebar
permalink: sgw-maintenance.html
summary: JemRF Smart Gateway Hardware Maintenace.
---
# Hardware Upgrade Modules
The Smart Gateway hardware is made up of the following internal modules.
- The Core Processor, the Core Processor manages all functions of the Smart Gateway.
- The POE Power converter which converts the 45 volt Power over Ethernet levels to the 5 volts needed for the Gateway.
- The RF Transceiver used to receive messages from the RF Sensors and send to the Core Processor.
- The Real-Time clock module to provide time on power up of the Smart Gateway if it can not reach a online Time Server.
- The Dry Contact Relay module that provides an open or closed contact on Gateway Internal Failures.
- The LED status panel is the front panel of the SGW with the LightsL 1. Showing the SGW is up and working; 2. A Serve light showing it is connected to the HTTPS server and sending data; 3 The MQTT light indicating it is connected and sending data to the MQTT Broker.

{% include warning.html content="Before performing any hardware maintenace follow the **Shutdown** and **Power Off Procedures**."%}
## Smart Gateway Internal
Turn upside down and remove the four screews.
<img src="images/sgw-under.jpg" width="425"/>
Once the screws are removed trun the SGW over and remove the top. There is nothing attached to the top, be carefull not to pull the LED or Network panels off with the lid.
You should now see the insides of the SGW.
<img src="images/sgw-inside.jpg" width="425"/>
The arrows point to:
1. Front Panel Lights
2. Transceiver
3. Real Time Clock Module
4. Dry contact Relay Module
5. Core Processor
6. POE Converter (Not shown)

## Replaceing the Core Processor
At this time that requires the Smart Gateway to be returned to manufacturing.
- Future updates will provide testing options to determine if the Core Processor has failed.

## Install/Replacing POE Power Converter
At this time that requires the Smart Gateway to be returned to manufacturing.
- Future updates will provide testing options to determine if the POE converter has failed.

## Replacing RF Transceiver
The RF Transceive plugs into the Core Processor edge connector and provides the interface to the Internal Battery backed up clock if installed. You will only need a phillips screw driver to open the case.

### Exchanging the Transceiver

The Transceiver is plugged into the left end of the interface bus. For reference, the other end of the interface bus has the connections for the LED Status Panel. 
<img src="images/sgw-transc-rpi.jpg" width="425"/>
Note the arrow is to show the module is connected on the interface bus correctly.

This image shows the Transceiver Module with the cables to connect to the Real-Time Clock module if installed.
<img src="images/sgw-transc-rtc.jpg" width="425"/>
To remove the Transceiver just pull it up and off the interface bus.  Then slide the connector appart that connects it to the RTC module. 
<img src="images/sgw-rtc-alignment.jpg" width="425"/>

Next connect the replacement transceiver to the RTC if used and then plug it onto the interface bus.
The following three images shows some common mistakes. You should NOT see pins as pointed to or the connector should not be forward as pointed to.
<img src="images/sgw-trans-bad-poe.jpg" width="425"/>
<img src="images/sgw-trans-bad-rpi-1.jpg" width="425"/>
<img src="images/sgw-trans-bad-rpi-2.jpg" width="425"/>
{% include warning.html content="Warning if it is not plugged in correctly, it can damage the Transceiver module."%}


The antenna should go up and to the far corner as show below
<img src="images/sgw-inside-close.jpg" width="425"/> 

### Power Up verification
Once you have verified it is plugged in correctly, you can put the top cover back on and power it up.
To verify it is working, check the Sensor List tab to see that your sensors start showing in the list. If they do not show after a few minutes the System Gateway Ready Led will turn red indicating it does not see any sensors.
Shutdown and check the installation of the transceiver module.

## Install/Replace the Battery Backup Clock Module
At this time that requires the Smart Gateway to be returned to manufacturing.
- Future updates will provide testing and installation of the RTC.

## Install/Replace the Dry Contact Relay Module
At this time that requires the Smart Gateway to be returned to manufacturing.
- Future updates will provide testing and installationi of the Dry Contact Relay Module.

## Replacement of Front Panel Lights
At this time that requires the Smart Gateway to be returned to manufacturing.
- Future updates will provide details on replacing the Front Panel lights.

