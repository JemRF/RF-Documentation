---
title: The JemRF S32 WIFI Sensor Manual Updates
keywords: getting started introduction, WiFI Sensor
last_updated: Sept 20, 2025
tags: ESP32, Updates, Jemrf sensor, WiFi Sensor
sidebar: wifi_sidebar
permalink: wifi32s-manual-update.html
folder: mydoc
---

## JemRF S32 WIFI Sensor - Manual Firmware Upload

This document outlines the process for manually updating a JemRF S32 WiFi Sensor from a desktop PC. This procedure is for new installs and to reload a device that received a bad update.

### Download tools
A folder must be installed on the local PC's root disk drive "C:". [Download the tools here.](\firmware\Espressif.zip) The download is a compressed file Espressif.zip, open the file with Windows Explorer and drag the folder inside "Espressif" to "This PC, OS (C:).
Downloading and installing the tools is a one-time task.

### Run Updates
Left-click on Start and select "Terminal". A new window will appear on the desktop like Figure 1. 
<center>{% include image.html file="espressif1.jpg" alt="WiFi Sensor Update Available "%}
Figure 1.</center>


Next, you need to change to the location of the tools as shown in Figure 2 and Figure 3.
<center>{% include image.html file="espressif2.jpg" alt="WiFi Sensor Update Available "%}
Figure 2.</center>


<center>{% include image.html file="espressif3.jpg" alt="WiFi Sensor Update Available "%}
Figure 3.</center>

 
To show the list of tools, type "ls" as shown in Figure 4.
<center>{% include image.html file="espressif4.jpg" alt="WiFi Sensor Update Available "%}
Figure 4.</center>


The next task is to identify what interface your WiFi Sensor is plugged into. To do this, we will list the ports in use on your computer, then plug the WiFi Sensor in and rerun the command to show the new port used by your sensor. Figure 5 shows the before (with your sensor unplugged) and after plugging in the sensor and running the "pyserial-ports.exe" command again, showing the new port (in this example, COM6).
<center>{% include image.html file="espressif5.jpg" alt="WiFi Sensor Update Available "%}
Figure 5.</center>


The last step is to install the firmware via the COM port on your computer. Enter the command "./loader.ps COM6" as shown in Figure 6, replacing COM6 with the COM value on your PC. Note that it is case-sensitive, so use uppercase when typing "COM". If there are no issues connecting to the device, you will see the loading process start as seen in the bottom half of Figure 6.
<center>{% include image.html file="espressif6.jpg" alt="WiFi Sensor Update Available "%}
Figure 6.</center>


Once the update completes, the process will start a monitor application, and you should start seeing messages like shown in Figure 7.
<center>{% include image.html file="espressif7.jpg" alt="WiFi Sensor Update Available "%}
Figure 7.</center>


When you are done, press the Control (Ctrl) key and the "]" key at the same time, and that should exit the monitor as shown in Figure 8.
<center>{% include image.html file="espressif8.jpg" alt="WiFi Sensor Update Available "%}
Figure 8.</center>

### Validation 
After following the Startup process to get connected to the WiFi 32s Sensor local WiFi, you should see Figure 9, and at the bottom, it will show Version 1.1.1. You can now update over the air using the "Update Available, Install" option.
<center>{% include image.html file="jemrfesp32ssetupupdate.jpg" alt="WiFi Sensor Update Available "%}
Figure 9.</center>

## Releases

This is the baseline release:
| Version | Date | Description |
|---------|------|-------------|
| 1.1.1 | 11/21/2025 | Baseline release with getvalidation option |

[For current Release information click here](wifi32s-update.html#releases)



