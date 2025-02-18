**JemRF Monitoring User Guide**

**JemRF Monitoring (Monitoring)** is a system of three components: The Sensor, The Gateway, and The Cloud. The Sensor is designed to measure and monitor the temperature of a desired location (i.e. door, refrigerator, freezer, or water pipes). The Sensor reports the measurements a Gateway. The Gateway logs the information, appends a date, and location code, then sends the information to the Monitoring Cloud. The cloud is the user interface where the information is monitored. The user can set alerts for out of tolerance samples, or simply plot the last days of measurements.

This document is on the Elno Cloud it will help with getting started, entering your business information, managing who can access your information and much more.

Table of Contents

[**Elno User Guide** 1](#_Toc522470315)

[Document Revision History 1](#_Toc522470316)

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Document Revision History](#document-revision-history)

<!-- /code_chunk_output -->


[**Getting Started** 2](#_Toc522470317)

[**Gateways** 5](#_Toc522470318)

[Change Gateway Description and controls 5](#_Toc522470319)

[**Sensors** 7](#_Toc522470320)

[Change Sensor description and controls 8](#_Toc522470321)

[**Notifications** 10](#_Toc522470322)

[Notifications Create and Edit Options 11](#_Toc522470323)

[**Online/Offline Notifications** 12](#_Toc522470324)

[**Charts** 13](#_Toc522470325)

[Sample Picture of Temperature Gauges 13](#_Toc522470326)

[Sample Plot 14](#_Toc522470327)

### Document Revision History

August 19, 2018 First published User Guide with the new web site layout.

**Getting Started**

The first task is to visit the Elno home page to review the documents and create an account. Go to [Monitoring Home page](%20Monitoring%20Home%20page) (**<https://Monitor.jemrf.com>**) and you will be presented with the portal page.

![email1](data:image/jpeg;base64,/

With the options across the top, you can view information about us, the project, pricing and types of sensors.

To get started you will first need to register. On the portal top right side is Register, click Register and you will be presented with the Registration page below. Enter an account name, your contact Email Address and create a password for your account.

![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/
<br/>Once registered your will get an Email confirmation and will be able to sign in.

Now that you have and account, on Portal or Home Screen, click Login you will get a login screen below.

![](data:image/png;base64,

The email you used to register is the email login name with the password you created or was created for you.

Once logged in, an options menu will appear on the left side of the page and your screen should look like:

![email1](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/

The new options provide links to details about the Gateway, Sensors, Notifications and Charts. The options allow you to change display information about your gateway and the connected sensors.  You can change the temperature alert limits, set who gets notifications by email for the daily reports and who gets text or email messages when a sensor goes out of limits.

**Gateways**

When you click on the Gateway tab you will see this display screen. It shows the location label that will be included in your daily emails and show up on the real time charts.  It shows a tracking Id to help support work issues with your gateway and its online, offline status.

![email1](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/

Change Gateway Description and controls

When you click Edit you get the detail page below where you can enter the Location text.  For sites with poor internet connections there the Alert Timeout adds a delay before sending a notification the gateway is offline.

If the internet where the Gateway is located is having problems going off and on, Mute Alerts disables sending the offline/online status, so you are not flooded with messages until the internet issues have been corrected.  

The Active option will stop all logging from this gateway.  It is for those with multiple gateways that might be moving support from one to another.

If your organization owns more than one Gateway, or you manage Gateways for different organizations, each Gateway will be listed with these options.

To set options, click on the Edit button and the following screen will appear.

![email1](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/

Here you can change the report Gateway Title, how long to wait (in seconds) before waiting for alerts. If you want Alerts muted or if you just want to set it inactive and remove it from the status reports and real time display.

<br/>

**Sensors**

To see status and set names and controls for the Sensor you select the Sensors option.

The following is the Sensors status page.  

![email1](data:image/png;base64,

Here you can see the Display Name of the Sensor, the System Id for tech support help, the last value from the sensor, if it is Active, Disabled, online or offline (aka. Reports Lost communications). The last column provides status of the option for this sensor to send a notification if it is out of tolerance or goes offline.  Here you can see the different Notification states, Alerts Silenced, Notifications Active, and Disabled.

Change Sensor description and controls

To change or set the values click on the Edit button and the following screen will appear.

![email1](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/

This screen shows your organization as the owner of this sensor.  The nice display name of the sensor, if Enabled or not, if Sending Alerts is enabled or not, and what position in the Real time report you want this sensor to be displayed.  For local Internet problems, the Sending of Offline Alerts can be disabled.

The next two sets of settings are the temperature limits and length of time in minutes above that temperature before sending an alert notification.  
The Lower limit Alert is triggered if the temperature goes below that temperature for the given time, in minutes.

These limits are displayed on the Chart graph.  Alerts will not be sent if Send Alerts is No.

**Notifications**

The Notifications option will show the following screen.  There you can see all Notification.

Notifications are not specific to a Sensor; any event will trigger the assigned notification(s).

In this example there are two types of Notifications, the first is Send a Text Message to the listed phone number, if a Sensor goes out of tolerance and the second is to send a summary status report for the past 24 hours by Email at 7pm to the listed contact email.

![email1](data:image/png;base64,

Notifications Create and Edit Options

The Create New Notification button on top right or the row edit button will display the screen below where you can configure that Notification.

At the top is the Organization name, Then the Notification will be sent if this is a daily report, Which Report to send, here the option is Real Time Event Notification, or send the Contact an Alert via Text Message when a sensor goes out of tolerance.

The last option allows you to disable a notification but keep it in the list for later use.

![email1](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/

**Online/Offline Notifications**

The online/offline notifications messages are sent by Email to the organization email. (Future: Send to Real-time Notification contacts)

The gateway is flagged as offline when failing to check-in within 5 minutes.  This allows chatter from network drops to not generate false alerts.  
The sensors are flagged as offline if they fail to send samples every 8.1 minutes because some sensors do not send checking status but once every 8 minutes.

Because a generic sensor only reports in every 8 minutes, the long generic delay eliminates false alerts.  

**Charts**

The last option is Charts, this provides a near real time reading of your temperatures

At the top is the Gateway Name “Seltron Ky”,

At the top of each meter is the Name of the sensor and the last time a value was received.

Under the meter is the current value, the limits and a status area showing it online and if Alerts are disabled.  No display is off in this chart.

Sample Picture of Temperature Gauges

![email1](data:image/png;base64,

At the bottom of each meter is the option to plot a graph of the last 12 or 24 hours of data received from that sensor.

Sample Plot

Example shown here is for “Frig 1”.   Red is the critical, Orange the Upper and Blue the Lower alert notification limits.

![email1](data:image/png;base64,