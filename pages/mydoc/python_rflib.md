---
title: Python RFLIB library
keywords: python, code, rflib
last_updated: Oct 1, 2020
tags:  
summary: "This page explains the Python RFLIB library"
sidebar: mydoc_sidebar
permalink: python_rflib.html
folder: mydoc
---

### Description
The RFLIB Python library contains a series of functions that make sending and receiving radio messages easier. Sending and receiving messages through a JemRF radio is easily achieved by reading and writing to the serial port but this library has some more advanced features that you may need:

 - **Multiprocessing** Monitoring the serial port for incoming messages as well as carrying out other tasks (e.g. switch a light on/off) is best performed using multiprocessing. This library has a dedicated function (rf2serial) that continuously monitors the serial port to ensure no radio messages are missed, that when run in a dedicated thread (described fully below), frees up processing time to process all incoming data (e.g. call an external web service like PrivateEyePi, Adafruit, MQTT, Home Assistant etc...).
 
 - **Messaging Receipt Reliability** messaging will retransmit messages not received by the intended recipient, and timeout after some predefined amount of retry attempts. This is useful for time when you want to ensure your messages are being received and take some action if they are not received. 
 
 - **Serial Port Abstraction** hides the technicality of opening closing, reading and writing to the serial port. This library has a simple transmit method you can use to transmit radio messages and a callback function that is called when a message is received.
 
 - **Fetch message function** is used to fetch incoming messages from a queue (Python list), one by one. 
 
 - **Debug** your code using the debug feature that will output debug information to the serial monitor.
 
 - **Duplicate filtering** will filter duplicate messages received.
 
 - **Preprocessing LLAP messages** decomposes an LLAP message into its subcomponents (Device ID, Message Type, and Data)

### Example code

A number of examples are provided the [rf_tools](https://github.com/JemRF/rf_tools) repository, e.g.:

 - serial_mon.py (a utility that print all in coming messages to the screen)
 - rf_config.py (a utility to transmit a radio message and print the reply)
 - rf2mqtt.py (publishes all incoming messages to an MQTT message broker)
 - rf2adafuitio.py (interfaces with the AdafruitIO cloud service)
 - ...

### Installation

 - Download the library from here: [https://github.com/JemRF/rf_tools.git](https://github.com/JemRF/rf_tools.git)
 
### Functions

#### init()
 - Should be called once at the start of your application
 - Opens the serial port and initializes variables and queues
 
**Example:**
```
rflib.init()
```

**Returns**
- Nothing
 
#### rf2serial() function
 - This function reads and send data to the serial port. All incoming data from the radio module is added to an in-memory list called *message_queue*.
 - The function initiates a continuous loop that monitors the serial port that will only exit once the *event* global variable is set:

**Returns**
- Nothing

```
event.set()
```

 - Call this function in a thread of it's own:
 
 ```
from threading import Thread
 def main():
    rflib.init()

    a=Thread(target=rf2serial, args=())
    a.start()
 ```

#### getMessage() function
- This function fetches the next message from the *message_queue* (see rf2serial function), performs some preprocessing on the data (removal of duplicates and deconstruction of the LLAP message into sub components (see below example) and returns the data through the message class.

**Returns**

 - *sensordata* - The sensor reading data (e.g. for the following message : a99TMP22.25- *sensor_data* will contain 22.25)
 - *devID* - contains the two character sensor ID
 - *data* - contains the message portion of LLAP message (e.g. TMP22.25-)
 - *type* - a number that indicates the type of message
   - 1 = Button
   - 2 = State
   - 3 = Temperature A
   - 4 = Analog A
   - 5 = Temperature B
   - 6 = Temperature C
   - 7 = Humidity
   - 8 = Pressure
   - 9 = Battery
   - 10 = Analog B
 - *description* - a description of the message
   - ANAA
   - ANAB
   - BATT
   - BUTTON 
   - HUM 
   - PA
   - STATE
   - TMPA
   - TMPB
   - TMPC

**Example:**
```
message = getMessage();         
if message.sensordata <> "":
  print(message.devID)
  print(message.type)
  print(message.data)
  print(message.description)
  print(message.sensordata)
```

#### Add items to the *transmission_queue* to transmit radio messages (see also the *request_reply* function)
 - This method of transmitting a radio message simply transmits the LLAP message provided per example below. 
 - If you want to monitor for a reply message then you can do it using the *getMessage()* function but rather use the *request_reply()* function

```
rflib.transmission_queue.insert(0,"a80HELLO----")
```

#### request_reply(command)
- This function will transmit a radio message and wait for a reply which is returned in the request_reply class instance per example below.
- This function is dependent on the *rf2serial()* running in a thread 

**Where:**
 - *command* is the LLAP message to be transmitted
 
**Returns**
 - rt : 0 = no reply after three transmissions, 1 = reply received OK
 - num_replies : The number of messages received in response
 - id : a list of ID's received
 - message : a list of LLAP message content

**Example:**

```
request=request_reply("a80HELLO----") 
if (request.rt==1):
    for x in range(request.num_replies):
        print "RECEIVED : " + str(request.id[x]) + str(request.message[x])
```

### Debugging 
 - Set the following global variable in rflib.py in order to print debug data to the screen:

Change:
```
 RFDebug=False
```

To:
```
 RFDebug=True
```
 
 
 