---
title: The WIFI Sensor Updates
keywords: getting started introduction, WiFI Sensor
last_updated: Jan 12, 2024
tags:
summary: "The Internet Of Things (IOT) is where everyday things (cars, homes, household appliances, plants) are being connected to the Internet where we can monitor, control and alert in ways not possible before."
sidebar: wifi_sidebar
permalink: wifi-iot-updates.html
folder: mydoc
---

## WIFI Sensor - Firmware Upload

Over The Air (OTA) downloads are enabled in 3.3.09 release!
This release Eliminates the need for Future Manual Downloads
Go to Step 9 for Details.

### Manual Update using Windows Application

1. Connect FT232RL FTDI USB 3.3V/5.5V module to the WIFI sensor (set jumper to 3.3V) and the USB to your Windows PC.

Make sure you have crossed over TX and RX as shown by the red circle in the diagram
    for boards prior to WIFI Hardware Release 4.0
For WIFI Hardware Release 4.0 boards and newer
    the 3.3V FTDI can plug directly into the header on the PCB, the TX and RX do are Not crossed.

2. On the Sensor, set dip switch 3 and 4 (marked FLASH) to ON

3. Check the device manager to determine the com port assigned to the FTDI

4. Download, unzip and run the ESP Flasher (file attached below)

5. Set the COM port, select the bin file (files attached below)

6. Reset the device by setting dip switch 1 ON then OFF, then click Download.
-- Note: Messages will start tracking the install which will take about a minute.

7. The device will automatically restart after the new firmware is uploaded. Set dip switches 3 and 4 back to the OFF position.

8. Its generally a good idea to reset the device using the Reset on the Login Details screen. Sometimes when we add new code we use different parts of the device memory so you may see erratic data displayed on the config screens. Resetting the device will reset the memory on the device to work with the new version. If the config screens are not visible you can also reset the device using the URL : http://192.168.4.1/reset

9. Over The Air (OTA) downloads are enabled in 3.3.09 release!
Release 3.3.09 once installed, Eliminates the need for Future Manual Downloads
A Reset after install is required.

## Release Notes
### Version 3.4 (01/11/2024)  (Current Release)
  - Provide DNS for Static IP settings
  - Fix issue with slow DS18B20 sensors
  - Add ReStart to Sensor Configuration page for Static IP settings
  - Fix Screen formats to be consistent on iPhone

### Version 3.3.6 (08/17/2023)
  - Provide MQTT Support

### Version 3.3.2 (07/31/2023)
  - Fix bug in URL to select folder for custom server URL
  - Change Temperature Sensor, DS18B20 digital sensor Id from 6 digits to full 11 digits.
  - -- NOTE: This does not affect the Temperature and Humidity Sensor Id.
  - Corrected Sensor Config page to use full area for sensor information.

### Version 3.3.09 (06/24/2023)
  - Update Server field with pep.jemrf.com as option
  - Add - Check-in every 5 minutes, independent of sensor send rate, to show online.
  - Add - Over The Air UPdates, all future updates will be from update Server directly to Sensor.
  - Current OTA release is 3.3.1 which is the official current release. (3.3.1 is same as 3.3.09 with new Version to show Download works.)
  - Download [WiFi 3.3.09 June 24, 2023](https://projects.privateeyepi.com/WIFI-Sensor/downloads/WIFIv4_3309.bin)

Version 3.2.8 (05/20/2023)
  - Update Fix C to F limit check. If the sensor is reporting Fahrenheit, the max temperature is 125F and not 230F. The result is the sensor fails to report any temperature over 125F. The Sensor using Celsius reports correctly up to 125C.
  - Update for subfolder support in URL
  - Add The WiFi SSID dropdown display local WiFI with signal strenght. You can select an SSID from the list or type in a private SSID.
  - Download [WiFi 3.2.8 May 20, 2022](https://projects.privateeyepi.com/WIFI-Sensor/downloads/WIFIv4_328.bin)

Version 3.2.0 (03/8/2022)
  - Update for slower sensor causing reads errors
  - Download [WiFi 3.2.0 March 8, 2022](https://projects.privateeyepi.com/WIFI-Sensor/downloads/WIFIv4_320.bin)

Version 3.1.1 (01/19/2022)
  - Detect bad sensor reads and retry before sending
  - Update copyright notice

Release Notes
Version 3.10 (11/23/2021)
  - Improve to Sensor Detection on Hardware Release 4.0
  - Add HostName(SSID) to Banner

Version 3.00
  - Bug fixes to BETA releases
  - Establish Baseline Software Release with support for Hardware Release 4.

1.9.9 BETA
 - Added new function for Analog sensors see advanced options
 -  Dropped support for battery level to be sent to the server (unfortunately the chip doesn't support analog sensors and battery level at the same time). We assume this is a good compromise as this device is mostly used with full power and not batteries.
 - Fixed some formatting bugs with email messages
 - Fixed bugs with some GPIO's not working with relays
 - Made the config screen load faster

1.9.8 BETA
  - Added support for EMAIL alerts. Rules configured on PrivateEyePi website with an EMAIL action associated with a WIFI sensor will now work.

1.9.7 BETA
 - Added new functionality to support switching sensor like door switches (reed switches), motion sensors and water sensors. See advanced options for details on GPIO allocations. There are 8 GPIO pins available on the WIFI sensor, but you need to plan how you intend using them. The table in advanced config will help you understand the GPIO allocations and which ones to use (especially if you intend having a temperature sensor and a switch on the same device). We will develop some tutorial explaining how to wire switches, but here is how to use the switch functionality:
 - Connect a GPIO pin to GND and a switch closed message is sent to PrivateEyePi
 - Disconnect a GPIO pin from GND then a switch open message is sent to PrivateEyePi
 - You can query the GPIO status using http://your_device_ip/gpiostatus?pin=PinNumber
where PinNumber is the GPIO number (e.g. 14)
 - Alarm rule action can be used to trigger an external buzzer/alarm off pin 5
 - Chime rule action can be used to trigger an external buzzer/alarm off pin 5


1.9.6
  - Fixed issue with IOS devices having problems loading the SensorConfig page

1.9.5
 - Fixed bug with sleep mode not working

1.9.4 BETA Release contains the latest relay functionality
 - Allows the use of the PrivateEyePi token identity for greater security
 - New setting to allow/disallow external control of the relays (GPIO)
 - Integration with the new PrivateEyePi dashboard (www.privateeyepi.com/control.php) used to switch relays from the internet

1.9.3 BETA Relay & Multiple DS18B20 Sensor Release (obsolete rather use latest)
 - Updated the http://your-ip/temp page to return all values when using multiple DS18B20 sensors. See here for more details.

1.9.2 BETA Relay & Multiple DS18B20 Sensor Release (obsolete rather use latest)
 - Multiple DS18B20 follow wiring as described in figure 2 here, attach the data line to GPIO13 of the WIFI sensor

1.9.1 BETA Relay Release (obsolete rather use 1.9.4)
  - Fixed a bug which causes the device to restart randomly, which causes the relay switches to reset

1.9 BETA Relay Release (obsolete rather use 1.9.4)
  - Dashboard added as the home page that contains temperature, humidity and switches for the relay switches
 - A configuration screen to add relay switches and associate descriptions for each relay
 - Control the relays via the dashboard, PrivateEyePi rules, or URL (e.g. http://.../relayon?pin=12 , http://.../relayoff?pin=12)

1.8.1 Stable Release
  - Bug with disabling AP mode fixed

1.8 Stable Release
  - Miscellaneous bugs fixed

1.7 BETA
   - Additional enhancements made for re-establishing WIFI connection when WIFI is  intermittent
  - Resolved AP mode disappearing after WIFI connection is dropped

1.6 BETA
  - Re-connect the sensor to the WIFI network if it is dropped or out of range for some time. This mainly affects users who poll the WIFI sensor for temperature readings. When running the sensor with a cyclic temperature transmission ("Send to server" setting is set) the sensor will automatically re-establish a WIFi connection after it has been dropped.
 - Ability to set a Static IP. This is also useful for users polling the sensor and don't want the IP address to change.
 - Ability to disable AP mode. Once you have your device setup you can disable AP mode so that it no longer appears as a WIFI access point. I would advise you to set a static IP before disabling the AP.

1.5
  - Fix to allow for blank WIFI password

1.4
  - Fix for http://192.168.0.4/temp page when using DHT22 sensor

1.3
 - Fix for IOS Safari browser which did not work. If you want a workaround that will work on v1.0-1.2 use a Chrome browser on Apple devices.

1.2
 - Changed the wake up pin to GPIO 14

1.1
 - Fixed bug where RAM reset when WIFI connection intermittent
 - Better handling of intermittent WIFI connection to the internet
 - Fixed bug where Fahrenheit temperature displaying centigrade symbol on the PrivateEyePi website
 - Added a new webpage to display the temperature only (192.168.4.1/temp)
 - Fixed bug where the server name on the config page did not save correctly
 - Added support for Temperature and Humidity
 - Added a new page (192.168.4.1/log) to view the error log

1.0
 - Beta Release

[WiFi 3.4 Jan 11, 2024](https://projects.privateeyepi.com/WIFI-Sensor/downloads/WIFIv4_3309.bin)