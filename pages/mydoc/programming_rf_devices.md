---
title: Under Construction
keywords: construction, under construction
last_updated: Sep 28, 2020
tags:
summary: "This page is under construction - stay tuned for updates"
sidebar: mydoc_sidebar
permalink: under_construction.html
folder: mydoc
---

To update an RF device (sensor, IOT Gateway or Flex IO) requires connecting the device as to a computer as shown in [Hardware & Firmware](hardware_and_firmware.html).
Once complete you will need a ccti-programmer applicaition.
To download an executable for Windows [Windows CCTI Programmer](link_to_programmer).
To download an executable for Raspberry Pi [Raspberry Pi CCTI Programmer](link_to_programmer).

To compile your own download [ccti-prog zip](ccti-prog.zip).
```
wget tool command
```
To compile
```
make
gcc -o ccti-prog -Wall ccti-prog.c hex.c
```
Make a new RF bin file using the cmp.bat file (called iot2.hex below) and copy it to the RaspberryPi. Make sure you upped the version in the code. Change 7.2 below in BOTH locations to a new version

```
if (strncmp(command, "VERSION", 5) == 0) {
        strncpy(command, "VER7.2---", 9);
        cons_llap("VER7.2---");
        sendllap(command,0,1,0);
        return(3);
        }
```

Make sure an RF Gateway is attached to the Pi and nothing is using the serial port (e.g. rfsensor.py).

Run the utility:

pi@raspberrypi:~/pep/cctl-prog2 $ sudo ./cctl-prog  -d /dev/ttyAMA0 -f iot2.hex
Waiting 10s for bootloader, reset board now
...Bootloader detected
Erasing page 1
Erasing, programming and verifying page 2
Erasing, programming and verifying page 3
Erasing, programming and verifying page 4
Erasing, programming and verifying page 5
Erasing, programming and verifying page 6
Erasing, programming and verifying page 7
Erasing, programming and verifying page 8
Erasing, programming and verifying page 9
Erasing, programming and verifying page 10
Erasing, programming and verifying page 11
Erasing, programming and verifying page 12
Erasing, programming and verifying page 13
Erasing, programming and verifying page 14
Erasing, programming and verifying page 15
Erasing, programming and verifying page 16
Erasing, programming and verifying page 17
Erasing, programming and verifying page 18
Erasing, programming and verifying page 19
Erasing, programming and verifying page 20
Erasing, programming and verifying page 21
Erasing, programming and verifying page 22
Erasing, programming and verifying page 23
Erasing page 24
Erasing page 25
Erasing page 26
Erasing page 27
Erasing page 28
Erasing page 29
Erasing page 30
Erasing page 31
Programming complete

The chip now has a new production version installed. Verify it worked by checking the version (rf_config.py 01 VERSION).

To verify your new version, send the device the Version command.
The default device id is 03.

Example:

```
python rf_config.py 03 VERSION
SENT     : 03VERSION
RECEIVED : 03VER7.x---
```


| Type Number| Description | Mode |
|------------|-------------|
| 1  | Thermistor Temperature Sensor| Sensor Mode |
| 2  | Gateway | Gateway Mode|
| 3  | DHT22 Humidity Sensor |Sensor Mode|
| 4  | DS18B20 Temperature Sensor |Sensor Mode |
| 5  | Analog A | Sensor Mode|
| 6  | Analog B | Sensor Mode|
| 7  | Relay | Actuator Mode |
| 8  | SHT21 Humidity and Temperature Sensor| Sensor Mode |
| 9  | BME280 Pressure, Humidity and Temperature Sensor| Sensor Mode |
| 10 | HTU21 Humidity and Temperature Sensor| Sensor Mode |


**Command:** TYPE[*p1*] <br>
**Response:** TYPE[*p1*]

*Where*: p1 = Type Number from the above table

Example:

```
python rf_config.py 03 TYPE1
SENT     : 03TYPE1
RECEIVED : 03TYPE1----
```


