---
title: RF4 Message Reference
keywords: message reference, llap, protocol, message protocol, api, json, interface, messages
last_updated: June 10, 2025
tags:
summary: "This page details the LLAP messages and adjustments for RF4, (4 character Ids) used by the JemRF devices"
sidebar: mydoc_sidebar
permalink: rf4_message_reference.html
folder: mydoc
---

The RF4 message formats extend the original 2 character IDs to 4 characters. \
In the document below shows the device Id as 9999. The device Id can be any character 0-9, A-Z, or a-z. As example b09aBHELLO is for device 09aB.

Using the rf_config.py application to send commands, to send a Version request to sensor 09aB would be python rf_config.py 09aB VERSION. \
The return would be b09ABVER9.xx.\

### RF4 Message Formats and Responces

| Message | Action | Return Message |
|-------|--------|---------|
| `+++` | Use this command to determine if a device is up and running. This command can only be sent over the serial interface. If you want to test the presence of a remote device use the HELLO command. This command does not require message start indicator, or device ID (refer Message Format section). The return message is OK followed by the current channel the IOT gateway is listening on, and the firmware version. | `OKcv.vv`|
| `AA` | Analog value 0-32767 from Analog A (Flex Module Pin17) | `b9999AA99999` |
| `AB` | Analog value 0-32767 from Analog B (Flex Module Pin18)  | `b9999AB99999` |
| `ATCH[num] E.g. ATCH5` | Configures the device Frequency. Only accepts a number 1 to 6 and sets the desired frequency per chart below. Device requires a restart to apply the new frequency. For two devices to communicate they must have the same frequency and channel (ATCN). Device requires a restart to apply the new channel. <br/> 1 - 433 MHZ  <br/> 2 - 915 MHZ (default US & Canada) <br/> 3 - 868.3 MHZ (default Europe) <br/> 4 - 868 MHZ <br/> 5 - 903 MHZ <br/> 6 - 315 MHZ | `b9999ATCH9--` |
| `ATCN[num] E.g. ATCN5` | Configures the transmission channel. Only accepts numbers 0-9. Each frequency (ATCH) has 10 channels. For two devices to communicate they must have the same frequency and channel. Device requires a restart to apply the new channel. Default is 0. | `b9999ATCN9--` |
| `ATEE[num] E.g. ATEE1` | Configures whether to encrypt message. <br/> ATEE1 = encryption on. <br/> ATEE0 = encryption off. <br/> Default is off. <br/> Refer ATEA for the related encryption key. | `b9999ATEE9--` |
| `ATEA[16 chars] E.g.ATEAThisMyPrivateKey` | A 16 character private key used for encryption. Wireless messages are limited to 12 characters so only 5 character pass-phrase can be sent over the air. 16 character pass phrase can be set through the serial port. When encryption is turned on all devices with the same private key can communicate with each other. Default is 16 spaces. | `b9999AE[5 chars] The 5 chars are the first 5 characters of the key. **` |
| `ATID[5 num]` |  A 5 digit numeric value that sets the PanID of the device. All devices of the same PanID will communicate with each other. A reboot is required to apply the new PanID. Default is 23205. | `b9999PI99999` |
| `WAKE` | Takes the device out of sleep mode. There is a 5 second window after a device is restarted when this command can be used to wake up sleeping devices. | `b9999WAKE---` |
| `BATT` | Returns the input voltage. A battery message is transmitted every 10 intervals (see INTVL) or every 10 requests. | `b9999BAT9.99` |
| `BUTTON` | Returns the current Button State, as STATE ON/OFF. | `b9999STATON` <br />`b9999STATOFF` |
| `CHDEVID[2 numbers]` | E.g.: CHDEVID85 Changes the device ID to a new ID. Make sure you send two characters. | `b9999CID9999` |
| `CYCLE` | Puts the device into a cyclic sleep and is awoken to send a sensor reading every INTVL minutes. This command does not apply to Type 2&7 sensors which cannot sleep (refer TYPE). | `b9999CYCLE--` |
| `b9999ERR------` | Returned when a command is unrecognized or the message is not correctly formatted as specified in the Message Reference. | `NA` |
| `HELLO` | Replies HELLO | `b9999HELLO--` |
|  `HTU21 ` | Returns a temperature (Celsius) and humidity (%) from the HTU21 external sensor. | `b9999HM99.99` <br/> `b9999TM99.99` |
| `INVL[3 nums]` <br/> `E.g. INVL005` |  A 3 digit numeric value that sets the timer interval to 1-30 minutes. See Timer section  for more details. Default is 0. | `b9999INVL999` |
| `INFO`  |  Request report on internal settings for TYPE xx, NOMSG yy, and INTVL zzz. | `b9999Ixxyzzz` |
| `NOMSG[num]` <br/> `E.g. NOMSG3` | A numeric value between 1 and 9 that specifies how many messages to be sent after each trigger or request. |  `b9999NOMSG9` |
| `PRESS` | Returns reading from Pressure Sensor  | `b9999PR999.9` |
| `RELAYA` |  Returns the status of relay A | `b9999RELAON-` or `b9999RELAOFF` |
| `RELAYB` |  Returns the status of relay B | `b9999RELBON-` or `b9999RELBOFF` |
| `RELAAON` |  Switches Relay A on | `b9999RELAON-` |
| `RELAAOFF` |  Switches Relay A off | `b9999RELAOFF` |
| `RELABON` |  Switches Relay B on | `b9999RELBON-` |
| `RELABOFF` |  Switches Relay B off | `b9999RELBOFF` |
| `RBSON`|  Report Button Status - ON. Use this command to always send the button status (refer Button Sensor section) every INTVL minutes when in CYCLE sleep mode regardless of the TYPE. This is useful for when you are using a RF module for multiple purposes (e.g. temperature sensor and button sensor) and you want a temperature reading as well as button status every INTVL | `b9999RBSON--` |
| `RBSOFF`|  Report Button Status - OFF. Use this command to switch off RBS (see RBSON). | `b9999RBSOFF-` |
| `RSSION`|  Report RSSI Status - ON. This is Only a IOT Gateway receiver option. Use this command to have the IOT Gateway to send the RF Signal Strength Indicator (RSSI) level when a sensor message is received by the IOT Gateway. Like bars on Cell phone, the more positive the better. A sensor will RSSI of -70 is like 1 bar on cell phone.  | `b9999RSSION---` |
| `RSSIOFF` |  Report RSSI Status - OFF. Use this command to switch off RSSI message from the IOT Gateway. (see RSSION). | `b9999RSSIOFF--` |
| `REBOOT` | Restarts the device | `b9999REBOOT-` |
| `RESET` | Resets the device settings back to factory default. This command can only be sent over the serial port. This command does not require a message start indicator, or device ID (refer Message Format section). | `OK-----` |
| `SLEEP` | Puts the device into Sleep Mode. See Sleep Mode section for more details. This command only applies to devices in sensor mode.| `b9999SLEEPIN` |
| `TEMP` | Returns a temperature reading in Celsius from the 10k thermistor | `b9999TM99.99` <br/> `(NOMSG times)` |
| `TYPE[num]` <br/>  `E.g. TYPE2` |  1=DS18B20 Temperature Sensor <br/> 2=Gateway  (enables serial comms TX and RX) <br/> 3=Pressure <br/> 4=DS18B20 Temperature Sensor <br/> 5=AnalogA <br/> 6=AnalogB <br/> 7=Relay <br/> 8=Voltate <br/> 9=AC Detect <br/> 10=HTU21 Humidity and Temperature Sensor | `b9999TYPE99-` |
| `VERSION` | Returns the Firmware Version  | `b9999VERx.xx` <br/>|
| `VOLTAGE` | Returns reading from Volatage Sensor  | `b9999VT99.99` |
| | | |
| ******* | *********************** | **** |
| | | |
| `REPLIES` | This is a list of messages the Sensor sends at the start of a cycle or on an event.| Format |
| `AWAKE` | When a sensor wakes up from sleeping, it sends the AWAKE message then sends its sensor information. | `b9999AWAKE---` |
| `SLEEPIN` | After a sensor has sent its readings, before returning to sleeep is sends the Sleeping message.| `b9999SLEEPIN` |
| `STATON` | When a sensor is sleeping and there is an event, Button pressed, Door Opened, Water Detected, AC Detected, ... it sends the current contact state.| `b9999STATON` or <br />  `b9999STATOFF` |

\* ‘9’ represents a number, e.g. 9.99 is a single digit number with two decimals, or 99 is a two digit number without decimals.




