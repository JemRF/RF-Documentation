---
title: The JemRF S32 WIFI Sensor Manual Updates
keywords: getting started introduction, WiFI Sensor
last_updated: Dec 12, 2025
sidebar: wifi_sidebar
permalink: wifi32s-manual-update.html
folder: mydoc
---

## JemRF S32 WIFI Sensor - Manual Firmware Upload

This document outlines the process for manually updating a JemRF S32 WiFi Sensor from a desktop PC. This procedure is for new installs and to reload a device that received a bad update.

## Download tools
Software must be installed on the local PC's root disk drive "C:". [Download the tools here.](\firmware\Espressif.zip) The download is a compressed file **Espressif.zip**.  Open the Zip folder in File Explorer and drag the folder “**Espressif**” to “This PC, OS (C:).

Note, the downloading and installing the tools is a one-time task.

## Run Updates

Left-click on **Start** and select "**Terminal**". A new window will appear on the desktop like Figure 1. 
<center>{% include image.html file="espressif1.jpg" alt="WiFi Sensor Update Available "%}
Figure 1.</center>

### Open Windows PowerShell

Next, you need to change the location you are viewing to the location of the tools. Enter the command 'CD' followed by space '\' like **"cd \ "** and then do an "**ls**" as shown in Figure 2 and Figure 3 to see the files.
<center>{% include image.html file="espressif2.jpg" alt="WiFi Sensor Update Available "%}
Figure 2.</center>

### Change the location you are viewing

<center>{% include image.html file="espressif3.jpg" alt="WiFi Sensor Update Available "%}
Figure 3.</center>

Verify you see the **Espressif** folder then enter "**cd .\Espressif**" followed by "**ls***" to show the list of tools are as shown in Figure 4.  If the folder is not there review and repeat the Download Tools step.
<center>{% include image.html file="espressif4.jpg" alt="WiFi Sensor Update Available "%}
Figure 4.</center>

### Identify Interface

To identify what interface (COM Port) your WiFi Sensor is plugged into, we will list the ports in use on your computer.\
1. With the sensor unplugged run the "**.\pyserial-ports.exe**" command.\
2. With the WiFi Sensor plugged in, Re-run the command to show the new port used by your sensor. \
Figure 5 shows the before (with your sensor unplugged) using the "**.\pyserial-ports.exe**" command. Then running it again, showing the new port (in this example, COM6).
<center>{% include image.html file="espressif5.jpg" alt="WiFi Sensor Update Available "%}
Figure 5.</center>

### Install Firmware

The last step is to install the firmware on the sensor via the COM port on your computer.\Type the command "**.\loader.ps1 COM6**" as shown in Figure 6, replacing **COM6** with the **COM** value on your PC.\ 
**Note that COM is case-sensitive**, so use uppercase when typing "**COM**". If there are no issues connecting to the device, you will see the loading process start as seen in the bottom half of Figure 6.

<center>{% include image.html file="espressif6.jpg" alt="WiFi Sensor Update Available "%}
Figure 6.</center>

<center>{% include image.html file="espressif6b.jpg" alt="File blocked "%}
Figure 6b.</center>

{% include note.html content="If you get an error like shown in Figure 6b, it means that Windows has blocked the application and it will need to be Unblocked. In Windows Explorer, in the C:\Espressif folder, right click on loader.ps1 and check the Unblock box. Then repeat with right click on the Esptools.exe and check the Unblock box. You can repeat the above step and the loader command should now work." %}

Once the update completes, the process will start a monitor application, and you should start seeing messages like shown in Figure 7.
<center>{% include image.html file="espressif7.jpg" alt="WiFi Sensor Update Available "%}
Figure 7.</center>


When you are done, to exit the monitor program, press the Control (Ctrl) key and the "]" key at the same time, and that should exit the monitor as shown in Figure 8.
<center>{% include image.html file="espressif8.jpg" alt="WiFi Sensor Update Available "%}
Figure 8.</center>

### Validation 
To validate the update and it is working, follow the [Startup process](wifi32s-setup.html) to get connected to the WiFi 32s Sensor local WiFi. When connected, you should see Figure 9\. Look at the bottom banner to see Version 1.1.1. Now you can update over the air using the “**Update Available, Install?**” option to get the latest version.
<center>{% include image.html file="jemrfesp32ssetupupdate.jpg" alt="WiFi Sensor Update Available "%}
Figure 9.</center>

## Releases

This is the baseline release:

| Version | Date | Description |
|---------|------|-------------|
| 1.1.1 | 11/21/2025 | Baseline release with getvalidation option |


[For current Release information click here](wifi32s-update.html#releases)
