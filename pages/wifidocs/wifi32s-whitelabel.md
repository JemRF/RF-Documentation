---
title: The ESP32 WIFI Sensor Whitelabel
keywords: Setting Custom settings for ESP-32 based WiFI Sensor
last_updated: Sept 20, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-whitelabel.html
folder: wifidocs
---

## The JemRF ESP32 WiFi Sensor White Label Option
The WiFi Version 2 Sensor supports a private control panel. The hidden control panel provides customization of the sensor when viewed on the regular sensor control panels. 

Option allow:
* Customizing the banner words and title at the top, including foreground and background colors.
* Hiding the Server URL if not used
* * Or it can be set and then hidden from your customers
* Hiding the Token field
* Hiding the Server Status in the banner area at the top of the page
* Showing the options to set the network address manually
* * It can also be set and then hidden from your customers
* Enable or hide the Relay Config Tab if not needed.


The image below shows the White Label Option page.

{% include image.html file="jemrfesp32whitelabel.jpg" alt="White Label Options"%}

The image below displays the default Setup Details tab, which includes all available options.
{% include image.html file="jemrf32sensorsetup.jpg" alt="Full Setup Options"%}

With all the options set to hide, the Setup Details tab is set to minimal, and the Relay Tab is gone
{% include image.html file="jemrf32sensorsetupmin.jpg" alt="Minimun Setup Options"%}

