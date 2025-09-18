---
title: The JemRF ESP32 WIFI Sensor Updates
keywords: getting started introduction, WiFI Sensor
last_updated: Sept 20, 2025
tags:

sidebar: wifi_sidebar
permalink: wifi32s-iot-updates.html
folder: mydoc
---

## JemRF ESP32 WIFI Sensor - Firmware Upload

The JemRF ESP32 WiFi Sensor over the Internet when instructed.

When new firmware is available, an update option will appear at the bottom of the Setup Details screen shown below.
{% include image.html file="wifigwsetup-online-update.jpg" alt="WiFi Sensor Update Available "%}

The "Update Request" selection will appear when it checks with the download server and finds a software update. When you are ready to update the Sensor, select YES and Save.
When the update starts, the screen will clear and a green status bar will appear:
{% include image.html file="wifiupdatebar.png" alt="WiFi Sensor Updating"%}

Once update is complete:
- It should reconnect to the Internet then restore the AP update page.
- Some wireless networks have issues using the internal 192.168.4.1 address. If your WiFi Sensor shows updates even after doing an update, try using the local WLAN IP address to do the update.
