---
title: The WIFI Pro Devices White label Option
keywords: Setting Custom settings for ESP-32 based WiFI Sensor
last_updated: Nov 14, 2025
tags:
sidebar: wifi_sidebar
permalink: wifi32s-whitelabel.html
folder: wifidocs
---

## The JemRF WiFi Pro Devices support White Label Option
The WiFi Pro series supports a private control panel. The hidden control panel provides customization of the sensor or gateway when viewed on the regular sensor control panels.

Option allow:
1. Customizing the banner words and title at the top, including foreground and background colors.
2. Hiding the Server Status in the banner area at the top of the page
3. Hiding the Server URL if not used

4. Hiding the Token field
   *   Or it can be set and then hidden from your customers if used else leave blank before hiding
5. Hiding or showing the options to set the network address manually
6. Enable Authentication on Setup, Sensor Config and MQTT control panels
7. Enable or hide the Relay Config Tab if not needed(if device has option).
8. Enter a Custom User Key (Must be 10 characters)

At the bottom is the field for the Authentication Key.

The default is the MMDD plus the last to digits of the Year plus the 4 characters of the Device Id after JEM
\Example: \
Date is **11**-**15**-20**25** 00:13:25\
ID: JEM**C868**407446A8 \
The resulting default Key would be **111525C868**. \
The default Key is base on the Sensor date and changes each day.

The image below shows the White Label Option page.

{% include image.html file="jemrfesp32whitelabel.jpg" alt="White Label Options"%}

The next image shows all the different fields that can be shown or hidden using Whitelabel option 1-7.

{% include image.html file="jemrf32sensorsetup-mu.jpg" alt="White Label Options"%}

The image below displays the default Setup Details tab, which includes all available options.
{% include image.html file="jemrf32sensorsetup.jpg" alt="Full Setup Options"%}

With all the options set to hide, the Setup Details tab is set to minimal, and the Relay Tab is gone
{% include image.html file="jemrf32sensorsetupmin.jpg" alt="Minimun Setup Options"%}

The Key field will turn Yellow when there is a change that needs the Key to authorize. When the correct Key is entered and you click off the Key field it will be validated and turn Green if Ok and Red if incorrec.

{% include image.html file="jemrfesp32whitelabel2.jpg" alt="White Label Options"%}


{% include image.html file="jemrfesp32whitelabel3.jpg" alt="White Label Options"%}

