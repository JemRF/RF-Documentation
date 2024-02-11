---
title: JemRF Monitoring Guide
keywords: communication, communications, relay, basic, radio, spec, wifi, sensor
last_updated: Feb 11, 2024
tags:
summary: "This Document provides overview of JemRF Monitoring"
sidebar: mydoc_sidebar
permalink: monitorintro.html
folder: monitoring
---

## Introduction to JemRF Monitoring System
JemRF Monitoring provides a professional monitoring site scaled to support organizations or businesses of all sizes.
It provide free accounts with every purchase to get started. With services available and adaptable for operating from multiple locations.

If you have not created an account, for the instructions [here](jemrfregister.html).

After you have created an account and logged in, Monitoring starts with the user Dashboard that is phone friendly. It shows a graphic scale for each of your temperature sensors. It also provide graphic icons to show doors, windows and switches in open and closed states.

{% include image.html file="monitor-dashboard.png" alt="PEP Login Page"%}

The Sensor tab is used to set the alarm alerts values for upper and lower limits.

{% include image.html file="monitor-sensorlist.png" alt="PEP Login Page"%}

The Sensor tab details
1. Shows if the sensor alarms have been muted
2. Shows an Icon when you move the mouse pointer over that spot, to Plot the Sensor.
3. Shows an Icon for the Signal Strength of that sensor by the receiver.
4. Shows an Icon of a battery at different levels, mousing over the Icon will show last reading.

{% include image.html file="monitor-sensorlist-details.png" alt="PEP Login Page"%}

Access the Sensor Edit
{% include image.html file="monitor-sensor-menu.png" alt="PEP Login Page"%}

Selecting the Sensor Information tab will show

{% include image.html file="monitor-sensor-information.png" alt="PEP Login Page"%}

Selecting sensor History will show the actual readings for the last few hours
{% include image.html file="monitor-sensor-history.png" alt="PEP Login Page"%}

The Edit button shows an edit window to change the sensor parameters.
{% include image.html file="monitor-sensor-edit.png" alt="PEP Login Page"%}

## Gateway

Selecting the Gateway Tab at the top will present a list of know Gateways for that account.

{% include image.html file="monitor-gateway.png" alt="PEP Login Page"%}

The menu button will list the option for the gateway.
1. Show Gateway Information
2. Edit the Gateway Settings
3. Remove the Gateway from the account list

{% include image.html file="monitor-gateway-menu.png" alt="PEP Login Page"%}

The Gateway Information shows:
1. Status Active/InActive
2. When was the last time the Gateway did a Check-in
3. The Alert Timeout is how many minutes is a Gateway or Sensor reports in before it is flagged as Off-line
4. Mute Alarms Yes/No is messages when the Gateway goes On or Off line
5. Active is a control to disable alerts and updates on about that Gateway
6. The remaining Items, IP Address, WiFi, FmVersion and Signal Strength are diagnostic information about that Gateway.

{% include image.html file="monitor-gateway-information.png" alt="PEP Login Page"%}

The Edit option will allow you to move the Gateway to another account (if you manage more that one).
1. You can Assign or Edit the Location information for that Gateway
2. The Alert Timeout is used to trigger an Offline event for the Gateway or Sensors being processed by that Gateway.
The default Alert Timeout is 5 minutes. The value should be twice the normal checking time for a sensor plus one minute.
An example would be for sensors that check-in every 10 minutes the timeout should be 21 minutes. That will allow one
updated to be missed and not trigger an Offline alert until the second message is not received. Your environment my need different settings.
3. You can have On/Off line messages for the Gateway Muted.
4. You can disable all reporting on the Gateway by setting Active to No.

{% include image.html file="monitor-gateway-edit.png" alt="PEP Login Page"%}

## Communications
Selecting the Communication tab will present the current list of people contacted on and events in their account(s),

{% include image.html file="monitor-communications.png" alt="PEP Login Page"%}

1. Device Alerts is used to assign who gets the Alerts when a Sensor exceeds it limits.
That person does not need an account on the system to be in the list.
{% include image.html file="Device Alert Add-Edit.png" alt="PEP Login Page"%}
2. Device Online/Offline Alerts is used to assign who gets notified when the device goes Offline and comes back Online.
If no contacts a in this list, the Device Alert contacts get notified.
This is useful for automated system to handle Device limits but not have to process On/Offline changes.
3. Monitoring generates a Summary Report for all the sensors in the account. This lets you assign who gets the summary.
You select the contact, when you want the summary and if you want the summary for the last 12 hours or last 24 hours.
{% include image.html file="Device On-Offline Alert Edit.png" alt="PEP Login Page"%}

4. System Alerts is the contact assigned to get Server broadcast messages, such as system down-time event, or update event.
If no one is assigned, no one gets notified for that account.
