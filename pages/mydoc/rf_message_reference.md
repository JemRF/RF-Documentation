---
title: Message Reference
keywords: message reference, llap, protocol, message protocol, api, json, interface, messages
last_updated: Sep 28, 2020
tags:  
summary: "This page explains all the supported LLAP messages used by the JemRF devices"
sidebar: mydoc_sidebar
permalink: rf_message_reference.html
folder: mydoc
---

| Message | Action | Return Message |
|-------|--------|---------|
| `+++` | Use this command to determine if a device is up and running. This command can only be sent over the serial interface. If you want to test the presence of a remote device use the HELLO command. This command does not require message start indicator, or device ID (refer Message Format section). | `OK-------`|
| `ANAA` |	Analog value 0-32767 from Analog A (Flex Module Pin17) | `a99ANAA99999` |
| `ANAB` | Analog value 0-32767 from Analog B (Flex Module Pin18)  | `a99ANAB99999` |
| `ATCH[num] E.g. ATCH5` | Configures the device Frequency. Only accepts a number 1 to 6 and sets the desired frequency per chart below. Device requires a restart to apply the new frequency. For two devices to communicate they must have the same frequency and channel (ATCN). Device requires a restart to apply the new channel. <br/> 1 - 433 MHZ  <br/> 2 - 915 MHZ (default US & Canada) <br/> 3 - 868.3 MHZ (default Europe) <br/> 4 - 868 MHZ <br/> 5 - 903 MHZ <br/> 6 - 315 MHZ | `a99ATCH9----` |
| `ATCN[num] E.g. ATCN5` | Configures the transmission channel. Only accepts numbers 0-9. Each frequency (ATCH) has 10 channels. For two devices to communicate they must have the same frequency and channel. Device requires a restart to apply the new channel. Default is 0. | `a99ATCN9----` |
| `ATEE[num] E.g. ATEE1` | Configures whether to encrypt message. <br/> ATEE1 = encryption on. <br/> ATEE0 = encryption off. <br/> Default is off. <br/> Refer ATEA for the related encryption key. | `a99ATEE9----` |
| `ATEA[16 chars] E.g.ATEAThisMyPrivateKey` | A 16 character private key used for encryption. Wireless messages are limited to 12 characters so only 5 character pass-phrase can be sent over the air. 16 character pass phrase can be set through the serial port. When encryption is turned on all devices with the same private key can communicate with each other. Default is 16 spaces. | `a99ATEA[5 chars] The 5 chars are the first 5 characters of the key. **` |
| `ATID[5 num]` |  A 5 digit numeric value that sets the PanID of the device. All devices of the same PanID will communicate with each other. A reboot is required to apply the new PanID. Default is 23205. | `a99ATID99999` |
| `AWAKE (up to Version 2 - most temperature and switch sensors are on V2)` |  Takes the device out of sleep mode. There is a 5 second window after a device is restarted when this command can be used to wake up sleeping devices. |  `a99AWAKE---` |
| `WAKE (Version 3 and up - Flex modules and light sensor are on version 3 and up)` | Takes the device out of sleep mode. There is a 5 second window after a device is restarted when this command can be used to wake up sleeping devices. | `a99WAKE----` |
| `BATT` | Transmits the input voltage. A battery message is transmitted every 10 intervals (see INTVL) or every 10 requests. | `a99BATT9.99-` |
| `BME280 (Version 7 and up)` | Transmits a temperature reading in Celsius, a humidity reading % and environment pressure reading in Pascals from the external BME280 sensor. | `a99TMPA99.99 a99HUM99.99-  a99PA9999.9-` |
| `CHDEVID[2 numbers]` | E.g.: CHDEVID85 Changes the device ID to a new ID. Make sure you send two characters. | `a99CHDEVID99` | 
| `CYCLE` | Puts the device into a cyclic sleep and is awoken to send a sensor reading every INTVL minutes. This command does not apply to Type 2&7 sensors which cannot sleep (refer TYPE). | `a99CYCLE----` |
| `a99ERR------` | Returned when a command is unrecognized or the message is not correctly formatted as specified in the Message Reference. | `NA` |
| `GPIO` | Used to set GPIO pins 3,4 and 5 on the FLEX RF module high or low. <br/> GPIOA1 - switch GPIO A on <br/> GPIOA0 - switch GPIO A off <br/> GPIOB1 - switch GPIO B on <br/> GPIOB0 - switch GPIO B off <br/> GPIOC1 - switch GPIO C on <br/> GPIOC0 - switch GPIO C off  | `a99GPIOA1---` |
| `HELLO` | Replies HELLO | `a99HELLO----` |
|  `HTU21 (Version 7 and up)` | Transmits a temperature (Celsius) and humidity (%) from the HTU21 external sensor. | `a99HUM99.99-` <br/> `a99TMPA99.99` |
| `INTVL[3 nums]` <br/> `E.g. INTVL005` |  A 3 digit numeric value that sets the timer interval to 1-30 minutes. See Timer section  for more details. Default is 0. | `a99INTVL999-` |
| `M[8 chars]` <br/> `(Version 5 and up)` | This command can be used to send custom messages to the MAX7219 display. 8 digits to be displayed on the display. <br/> Characters supported: <br/> A,B,C,D,E,F,G,H,I,J,L,N,O,P,R,S,T,U,Z <br/>  a,b,c,d,e,f,g,h,i,j,l,n,o,p,r,s,t,u,v,w,x,y,z <br/> 0,1,2,3,4,5,6,7,8,9 <br/> UNDERSCORE, <br/> SQUARE BRACKETS, <br/> SPACE <br/>  Decimals are coded by subtracting 13 from the ASCII number. For example “5.” = “(” or “25.75c” = “2(75c”. | `a99MMESSAGE-` | 
| `MX[4 chars]` <br/> `(Version 5 and up)` |  Provides configuration for the wireless display MAZ7219. The four character configuration is as follows: 1 : “T” = display incoming temperature and humidity readings 2&3 : the ID of the sensor transmitting the temperature and humidity readings 4 : the suffix (e.g. “c” or “F”). Can be any character (means display temperature readings from sensor ID 99 in Fahrenheit) | `a99MXT99F---` |
| `NOMSG[num]` <br/> `E.g. NOMSG3` | A numeric value between 1 and 9 that specifies how many messages to be sent after each trigger or request. |  `a99NOMSG9---` |
| `PREAMBLE[num]` | A numeric value 1 or 0. If set to 1 then the device will add additional message data to the serial port. <br/> [Index][PanID][Message][RSSI][LQI] <br/> Index - Packet Length <br/> PanID - Refer PanID section <br/> Message - 12 character message <br/> RSSI - Received Signal Strength Indicator in dBm <br/> LQI - The Link Quality Indicator estimates how easily a received signal can be demodulated | `a99PREAMBLE9` |
| `RELAYAON` |  Switches Relay A on | `a99RELAYAON-` |
| `RELAYAOFF` |  Switches Relay A off | `a99RELAYAOFF` |
| `RELAYBON` |  Switches Relay B on | `a99RELAYBON-` |
| `RELAYBOFF` |  Switches Relay B off | `a99RELAYBOFF` |
| `RBSON` <br/> `(Version 7.2 and up)` |  Report Button Status - ON. Use this command to always send the button status (refer Button Sensor section) every INTVL minutes when in CYCLE sleep mode regardless of the TYPE. This is useful for when you are using a RF module for multiple purposes (e.g. temperature sensor and button sensor) and you want a temperature reading as well as button status every INTVL | `a99RBSON----` |
| `RBSOFF` <br/>  `(Version 7.2 and up)` |  Report Button Status - OFF. Use this command to switch off RBS (see RBSON). | `a99RBSOFF---` |
| `REBOOT` | Restarts the device | `a99REBOOT---` | 
| `RESET` | Resets the device settings back to factory default. This command can only be sent over the serial port. This command does not require a message start indicator, or device ID (refer Message Format section). | `OK-------` |
| `SHT21` <br/> `(Version 6 and up)` |  Transmits a temperature (Celsius) and humidity (%) from the SHT21 external sensor. | `a99HUM99.99-` <br/> `a99TMPA99.99` |
| `SLEEP` | Puts the device into Sleep Mode. See Sleep Mode section for more details. This command only applies to devices in sensor mode.| `a99STATEON/OFF` <br/> `(NOMSG times)` <br/> `a99SLEEPING` |
| `TEMP` | Transmits a temperature reading in Celsius from the 10k thermistor | `TMPA99.99---` <br/> `(NOMSG times)` |
| `TEMPB` | Transmits a temperature in Celsius and humidity readings from DHT22 | `TMPB99.99---` <br/> `HUM99.99----`  <br/> `(NOMSG times)` |
| `TEMPC` | Transmits a temperature reading in Celsius from the DS18B 20 sensor | `TMPC99.99---` <br/> `(NOMSG times)` |
| `TYPE[num]` <br/>  `E.g. TYPE2` |  1=Thermistor Temperature Sensor <br/> 2=Gateway  (enables serial comms TX and RX) <br/> 3=DHT22 Humidity Sensor <br/> 4=DS18B20 Temperature Sensor <br/> 5=AnalogA <br/> 6=AnalogB <br/> 7=Relay <br/> 8=SHT21 Humidity and Temperature Sensor <br/> 9=BME280 Pressure, Humidity and Temperature Sensor <br/> 10=HTU21 Humidity and Temperature Sensor | `a--TYPE99---`

\* ‘9’ represents a number, e.g. 9.99 is a single digit number with two decimals, or 99 is a two digit number without decimals.




   