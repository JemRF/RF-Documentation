---
title: Arduino RFLIB library
keywords: help, trouble, faq, tip, tips, 
last_updated: Oct 1, 2020
tags:  
summary: "This page explains the Arduino RFLIB library"
sidebar: mydoc_sidebar
permalink: rflib.html
folder: mydoc
---

### Description
The RFLIB library makes sending and receiving radio messages easier. Sending and receiving messages through a JemRF radio is easily achieved by reading and writing to the serial port (see this example) but this library has some more advanced features that you may need:

 - **Multiprocessing** on an Arduino is inherently difficult due to its single processor. Therefore monitoring the serial port for incoming messages as well as carrying out other tasks (e.g. switch a light on/off) can become difficult. This library implements a non-blocking, also sometimes called "round-robin", technique to ensure you never miss an in-coming radio message and can also do other processing.
 
 - **Messaging Receipt Reliability** or also sometimes called "request-reply" messaging will retransmit messages not received by the intended recipient, and timeout after some predefined amount of retry attempts. This is useful for time when you want to ensure your messages are being received and take some action if they are not received. 
 
 - **Serial Port Abstraction** hides the technicality of opening closing, reading and writing to the serial port. This library has a simple transmit method you can use to transmit radio messages and a callback function that is called when a message is received.
 
 - **Call back function for messages received** The library automatically monitors the serial port for messages and calls a call-back function in your code whenever a message is received. 
 
 - **Debug** your code using the debug feature that will output debug information to the serial monitor.
 
 - **Duplicate filtering** will filter duplicate messages being received.

### Example code

More examples can be found here : [https://github.com/JemRF/rflib/tree/master/examples](https://github.com/JemRF/rflib/tree/master/examples)

```
/*
  A simple example to receive radio messages and print them to the serial_port

  This example uses the rflib library to receive RF messages

  For use with radio modules from www.jemrf.com
*/

#include <rflib.h>

RFLIB rflib;

void myFunc() {

  Serial.println("Got message...");
  Serial.println(rflib.message_in);

}

void setup() {
  Serial.begin(9600);
  rflib.RegisterCallback(myFunc);
  rflib.begin();
}

void loop() {
  //Important to call profess_rf() frequently and have no delays in this loop
  rflib.process_rf();
}
```
 
### Installation

 - Download the library from here: [https://github.com/JemRF/rflib.git](https://github.com/JemRF/rflib.git)
 - Open up the Arduino IDE and click on Sketch->Include Library->Add .ZIP library and select the library downloaded in the previous step
 - Close all instances of the Arduino IDE and restart the IDE
 
### Methods

#### begin(void)
 - Should be called once in the setup() routine
 - Opens the software serial port and initializes variables

#### transmit(char * message, int retries)

**Where:**
 - *message* - 12 character message that will be sent to the radio for transmission. The message should be in [LLAP format](rf_message_format.html).
 - *retries* (Optional) - When set, the message will be transmitted *retries* times when an acknowledgment is not received from the destination node. If no acknowledgment is received after *retires* times then the no_ack property is set to true.
 
**Example:**
```
rflib.transmit("a62RELAYA---",3);
```
 
#### process_rf(void)
 
 - This method should be placed in the loop() function within your Arduino code. Do not put code that could slow down or block this routine from being executed, otherwise you may miss some in-coming radio messages. See [Automation 1](automation1.html) for an example on how to write non-blocking code. 
 
### Properties

#### *filter_duplicates*
 - When set to *true* duplicate messages are filtered away so the callback routine is only called once per unique message.

#### *got_ack*
 - This is set to *true* when an acknowledgment is received from the destination node after calling the *transmit* method.
 
#### *got_message*
 - This is set to *true* when a message is received and false when calling the *transmit* method. 
 
#### *message_in*
 - 12 character string containing a message that has been received.
 
#### *message_out*
 - 12 character string containing a message that will be sent.

#### *timeout*
 - Set to *true* if the number of *retries* has been exceeded.


