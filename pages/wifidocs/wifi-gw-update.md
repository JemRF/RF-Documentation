---
title: Updating the WiFi Gateway
keywords: WiFi Wireless Gateway, Over the Air,
last_updated: July 14, 2023
tags:
sidebar: wifi_sidebar
permalink: wifi-gw-update.html
folder: mydoc
---
### Online Firmware Download and Update
The WiFi Wireless Gateway Version 2 can be updated directly to the Gateway using the Internet. It is not updated automatically.
When new firmware is available, an update option will appear at the bottom of the Setup Details screen shown below.

{% include image.html file="wifigwsetup-online-update.jpg" alt="WiFi Gateway Update Flag" width=400px%}


The <b>"Update Gateway"</b> selection will appear when it checks with the download server and finds a software update. When you are ready to update the Gateway, select <b>YES</b> and Save.
When the update starts, the screen will clear and a green status bar will appear.
{% include image.html file="wifiupdatebar.png" alt="WiFi GW Updating"%}

Once update is complete:
- It should reconnect to the Internet then restore the AP update page.
- Some wireless networks have issues using the internal 192.168.4.1 address. If your Gateway Shows updates even after doing an update, try using the local WLAN IP address to do the update.

### Manual updates using Windows
If you have an issue with Over-The-Air updates, or you want to load an older version, you can update the Gateway Manually. The firmware versions are listed at the bottom.

##### 1. Connecting the Gateway to a computer
The FT232RL FTDI USB 3.3V/5.5V module is one option to connect the WIFI Gateway to the computer. You need to set jumper to 3.3V or you could damage the Gateway. You can plug the

{% include image.html file="IMG_5083 (320x240).jpg" alt="WiFi GW"%}
For the Wireless Gateway Hardware the 3.3V FTDI can plug directly into the header on the PCB.


##### 2. Set Gateway to Program Mode
On the Gateway, set dip switch 3 and 4 (marked FLASH) to ON

{% include image.html file="IMG_5086 (320x282)8750.jpg" alt="WiFi update cable"%}
##### 3. Check the device manager to determine the com port assigned to the FTDI

{% include image.html file="ftdi control panel (640x463)f823.jpg" alt="WiFi update cable2"%}

##### 4. Download, unzip and run the ESP Flasher (file attached below)

##### 5. Set the COM port, select the bin file (files attached below)
{% include image.html file="ESP Download1d59.png" alt="WiFi Download"%}

##### 6. Reset the device by setting dip switch 1 ON then OFF, then click Download.
-- Note: Messages will start tracking the install which will take about a minute.
{% include image.html file="IMG_5087 (320x277)84b8.jpg" alt="WiFi PGM sw On"%} Reset ON
{% include image.html file="IMG_5086 (320x282)181f.jpg" alt="WiFi Sw off"%} Reset OFF
##### 7. The device will automatically restart after the new firmware is uploaded. Set dip switches 3 and 4 back to the OFF position.

<span style="color:red ">Its generally a good idea to reset the device using the <span style="color:black;font-weight: bold ">Reset</span> on the Login Details screen. Sometimes when we add new code we use different parts of the device memory so you may see erratic data displayed on the config screens. Resetting the device will reset the memory on the device to work with the new version. If the config screens are not visible you can also reset the device using the URL : http://192.168.4.1/reset </span>


Release Notes:
#### Version 2.6.2 (07/05/2025)
- Option to change the RF Channel for large networks
- Info field for note on location of the Gateway
- Added Sorting of the Sensor List
[Download Release 2.6.2 ](firmware\wifi-gw\wifigw8266-2-6-2.bin )

#### Version 2.6.0 (07/03/2025)
- Support for RF4 (4-character Device ID) Sensors.
- Add MQTT status to all screens.
- Add option to send a message to Sensors to change their Update Interval

[Download Release 2.6.0 ](firmware\wifi-gw\wifigw8266-2-6-0.bin )

#### Version 2.5.1 (05/29/2025)
- Update to fix compatibility issue with HomeAssistant and MQTT JSON.
- Add RF Transceiver firmware version and channel to the page footer

#### Version 2.4.9 (06/20/2024)
- Support MQTT Broker user defined publish and Client Id
- Sensor List show GMT time when refreshing

[Download Release 2.4.9 ](firmware\wifi-gw\wifigw8266.2.4.9.bin )

#### Version 2.3.0 (12/27/2022)
- Support MQTT Broker user defined publish and Client Id
- Sensor List show GMT time when refreshing

#### Version 2.2.0 (07/27/2022)
- Load for Version 2 hardware
- Supports web firmware download and Update from Setup Page
- Supports MQTT Agent to send to MQTT Broker

#### Version 1.1.5 (03/22/2022)
- Operational Baseline Load

### Firmware and Programmer Downloads

[Download bulk Erase Image ](firmware\erase_flashc6c4.bin)

[Download ESP 8266 Flash Programmer ](firmware\esp8266_flashere381.zip )
