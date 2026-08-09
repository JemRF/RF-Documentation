---
title: The JemRF WIFI Sensor Pro and Gateway Pro Updates
keywords: getting started introduction, WiFI Sensor
last_updated: Sept 20, 2025
tags:

sidebar: wifi_sidebar
permalink: wifi32s-update.html
folder: mydoc
---

## JemRF WIFI Sensor Pro and Gateway Pro - Firmware Upload

The JemRF WiFi Pro Series updates over the Internet when instructed.
This setup process is using the WiFi Sensor Pro screen shots, but the process is the same for the WiFi Gateway Pro devices as well.

When new firmware is available, an update option will appear at the bottom of the Setup Details screen shown below.
{% include image.html file="jemrfesp32ssetupupdate.jpg" alt="WiFi Sensor Update Available "%}

The "Update Request" selection will appear when it checks with the download server and finds a software update. When you are ready to update the Sensor, select YES and Save.
When the update starts, the screen will clear and a green status bar will appear:
{% include image.html file="wifiupdatebar.png" alt="WiFi Sensor Updating"%}

Once update is complete:
- It should reconnect to the Internet then restore the AP update page.
- Some wireless networks have issues using the internal 192.168.4.1 address. If your WiFi Sensor shows updates even after doing an update, try using the local WLAN IP address to do the update.

## Validation Testing
The JemRF S32 Sensor support a hidden option to download Validation Firmware to help evaluate corrections and new features.

The download of validation firmware is initated by typing **getvalidation** in the url bar after the device address, example: \
http://192.168.254.66/getvalidation

The Updating Inprogress screen will appear like normal while downloading the update.

## Releases

| Version | Date | Description |
|---------|------|-------------|
| 1.1.1 | 11/21/2025 | Baseline release with getvalidation option  For the Sensor|
| 1.1.6 | 08/08/2026 | Baseline release for the Gateway Series|



