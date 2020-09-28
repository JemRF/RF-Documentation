---
title: Encryption
keywords: encryption, key, security
last_updated: July 3, 2016
tags:  
summary: "This page describes the encryption related configurations and how to enable encryption."
sidebar: mydoc_sidebar
permalink: encryption.html
folder: mydoc
---

128-bit AES encryption can be enabled between RF devices using a 16 character private key that is sent to each device before enabling encryption.

The 16 Character encryption key should be sent to each device through the serial port. Refer the [hardware and firmware](hardware_and_firmware.html) section of this documentation for serial port connection details for the device you have.   

## Frequency Default Setting
Encryption is off by default and and the 16 character password is 16 spaces. 

## How to enable encryption 

1. Configure the encryption key pass-phrase 

    **Command:** ATEA[*p1*] <br>
    **Response:** ATEA[*p2*]

    *Where*: p1 = is a 16 character pass-phrase
             p2 = the first 5 characters of the pass-phrase

    The below example sets the pass-phrase to MyPassPhrase1234:

    ```
    python rf_config.py 03 ATEAMyPassPhrase1234 
    SENT     : 03ATEAMyPassPhrase1234
    RECEIVED : 03ATEAMyPas
    ```

2. Enable Encryption

    **Command:** ATEE[*p1*] <br>
    **Response:** ATEE[*p1*]

    *Where*: p1 = is 1 for on and 0 for off

    The below example enables Encryption:

    ```
    python rf_config.py 03 ATEE1 
    SENT     : 03ATEE1
    RECEIVED : 03ATEE1
    ```

The device with device ID 03 will now encrypt all outgoing messages and decrypt incoming messages  