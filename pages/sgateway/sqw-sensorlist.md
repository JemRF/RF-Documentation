---
title: "JemRF Smart Gateway"
keywords: getting started introduction, Smart Gateway Jemrf, Gateway, rf Sensor
last_updated: July 23, 2024
sidebar: wifi_sidebar
permalink: sgw-sensorlist.html
summary: JemRF Smart Gateway Sensor List Tab.
---
# Sensor List
The Sensor List page shows the last messages received from each sensor for which the Gateway is processing data. There is the Sensor ID the raw message type received and the value associated with that message. There is a Message Count to show how many messages of that type from that sensor have been received. The timestamp was the time the last message was received.


<img src="images/sgw-sensorlist.png" width="425"/>
**Figure 1  The Sensor List screen.**

The option at the bottom of the Sensor List page are to support export of the sensor information captured on a specific date. The Export Start Date is the export all the received messages for that date starting an midnight local time based on the timezone in the Network Settings.  The Show command will show that last 30 messages received in the Export format. The screen shot shows the bottom of the 30 messages and the option to Export that days report. The is also an option to set the delimiter used in the CSV output file. The default is a comma(,).

<img src="images/sgw-sensorlist-bottom.png" width="425"/>
**Figure 2  Bottom of the Sensor Show screen.**

The daily sensor list can be a scheduled export. The Export Settings button will bring up the page shown below.
<img src="images/sgw-export.png" width="425"/>
**Figure 3  Export Prior Daily Report.**

The Export options are:
* In the top section is Enable Export at selected time with the status of the date and time of the last Export. The color Green indicates the last export was successful.
* The center section is for credentials needed to connect to a remote server to export the logs to.
* The bottom section allows for selection of the Transfer Method. There are two export methods, the first uses a Secure File Transfer protocol (SFTP). This is useful it the remote server is not located locally.
  - Figure 4 show the additional fields for the SFTP export option.
  - The second method show in Figure 3 is using a Windows file server, with the additional fields needed to connect to a Windows Server.

At the bottom of the page is the option to <b>Save</b> the Settings, <b>Test the Saved</b> Settings, this will immediately export the logs for the current day and <b>Reset Form</b> clearing all settings.

<img src="images/sgw-export-sftp.png" width="425"/>
**Figure 4  Export using SFTP protocol.**

Figure 4 also shows an example in yellow of a change that was entered and not yet saved.





