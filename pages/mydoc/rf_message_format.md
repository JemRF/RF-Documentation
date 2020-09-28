---
title: Message Format
keywords: message format, llap, protocol, message protocol, api, json, interface
last_updated: July 3, 2016
tags:  
summary: "This page explains the message format used by the JemRF devices"
sidebar: mydoc_sidebar
permalink: rf_message_format.html
folder: mydoc
---

## Format Overview
Each message is made up of 12 characters made up of three sections:

```
[a] - Message start indicator that is used to detect the start of a message

[id] - 2 character device ID identifying the device the message is intended for

[message] - 9 characters message content
```

An example of a message is: `a45HELLO----`

Where the device ID is 45 and the message content is `HELLO----`

## Lightweight Logical Application Protocol (LLAP)

{% include note.html content="LLAP was created by Miles Hodkinson for the CISECO RF devices. Below are excerpts from his documentation describing the protocol." %}

LLAP can be used to convey all sorts of short messages, but in our world, we use it to send short human readable messages between sensors, controllers and actuators in control systems.

LLAP messages are simple text messages and completely independent from the underlying infrastructure and transmission media used to convey the messages. That means that LLAP can be used anywhere you can exchange text. In particular, a user can type in a LLAP message in a terminal window on a Windows, Linux or Mac based computer, or on a Raspberry Pi for instance and receive a response from devices in the device network to which that computer is connected.

It is assumed that messages either arrive completely and without errors or don’t arrive at all. The communication infrastructure should provide for message integrity (e.g. via CRC) and message security (e.g. 128 bit encryption) and messages that get corrupted or fail security checks must be intentionally lost by the infrastructure. 

When you send a message, you should not expect any acknowledgment from the communications infrastructure as to whether it was sent or not. The only way to know if a message was received is by the recipient sending you a response LLAP message.

## Rationale for using LLAP

The heart of this protocol is it's simplicity. The messages are easily human readable and the compact nature makes them desirable for radio communications. LLAP is also perfectly suitable for IoT applications where sensors and actuators need to rapidly and securely communicate small amounts of information using a very low amount of power. The simplicity of LLAP also benefits a non technical end-user wanting to implement fast, secure and long range radio messaging to their applications.    



   