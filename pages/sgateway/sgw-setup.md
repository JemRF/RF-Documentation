---
title: "JemRF Smart Gateway"
keywords: getting started introduction, Smart Jemrf, Gateway, rf Sensor
last_updated: July 23, 2024
sidebar: wifi_sidebar
permalink: sgw-setup.html
summary: JemRF Smart Gateway Setup Tab.
---

# Setup Details
The Setup Details is the home screen and is used to configure the operation features of the Gateway.

To connect to the local network, there are two options. Option 1 is to configure the connection to the local WiFi. The second option is using the hardwired Ethernet interface.

The remote server uses web services to send measurements, which are normally the JemRF Monitoring Services.

Measurements are taken in centigrade. There is the option to send temperature readings in Fahrenheit instead.

There is an option for automatic updates.

System Health details: Green indicates the system is working. The Details button shows more details on the System Health.


<img src="images/sgw-setup.png width="425"/>
**Figure 1  The Setup Details screen.**

If the option is No, a second screen appears to pull updates or upload updates to the Gateway manually.

<img src="images/sgw-updates.png" width="425"/>
**Figure 2  Manual OS Update options.**

The current release is in the status bar at the bottom of the page. Updates on the latest releases are in the Update Information section. The Gateway must have an Internet connection to show the updated information.
There is also an upload updates option for Gateway without an Internet connection.

## The Gateway System Health Page
<img src="images/sgw-health.png" width="425"/>
**Figure 3  System Health tab.**
Gateway System Health so the health of the internal function that makes the Gateway operational. There are four sections on the System Health page to cover all parts of the Gateway operations.  The screenshot below shows a healthy Gateway.

### Section 1
Five internal control applications perform different functions. The HTTP server connection updates the JemRF Monitoring or other remote data collectors service with the Gateway's health and status.
The Sensor Receiver listens for and logs the messages received from the sensors. The receive log contains the date/time the message was received.

The HTTP/MQTT Sender application connects to the JemRF monitoring service or other external server using web services to send measurements. It also handles sending measurements to an MQTT Broker. The Sender also monitors to see if the system health status should be sent. If configured, it also sends the MQTT Health Status messages to the MQTT Broker using the MQTT connection.

The Health Check application generates the status used to determine the health of the Gateway. It monitors the message processing, temperatures, and applications to ensure that everything is working correctly.

The Status Light application monitors the Gateway's health and updates the LEDs with their current status. It also controls the external Relay state, which reflects the Gateway's health.

### Section 2
Section 2, the Sensor Status section, presents alerts for any sensors that are having issues.  This is used to detect an issue with a sensor with low battery power. It has only enough power to make an initial connection but not enough to send measurements. The result is the sensor keeps sending Starting messages that can block measurements from working sensors.
The screenshot below shows sensor 93 is having problems.
Sensors can generate temporary alerts and then return to normal. A Reset button is provided to clear the list. If a sensor reappears, it should be taken off-line and checked.


<img src="images/sgw-health-issue.png" width="425"/>
**Figure 4  System Health tab showing Sensor 93 is having issues.**

### Section 3
The third section of the Health page shows the internal temperatures of the Processors. The RF Receiver status shows the current count of messages processed. This is the same total count shown at the bottom of the Sensor List page.  It also shows a restart date for the RF processor if an error is detected and the RF receiver has to be reset.

### Section 4
The last section enables sending system health messages to the MQTT Broker A zero (0) disables the function. Values are in minutes.  The full set of system health messages is sent on the initial connection. After that, only the health messages indicating a change in status are sent.

