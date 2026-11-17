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
The WiFi Pro series supports a private control panel. The hidden control panel provides customization of the sensor or gateway when viewed on the regular sensor control panels. With option for private or self-signed digital certificates.

There is a simple access control option the bottom of all pages, the field for the Authentication Key if enabled.

    Enter a Custom User Key (Must be 10 characters)
    Option for a private or Self-Signed SSL Certificate.


The image below shows the White Label Option page.

{% include image.html file="jemrfesp32whitelabel.jpg" alt="White Label Options"%}

### Display Options
The next image shows all the different fields that can be shown or hidden using Whitelabel page.\
Fields options apply to:
1. Customizing the banner words and title at the top, including foreground and background colors.
2. Hiding the Server Status in the banner area at the top of the page
3. Hiding the Server URL if not used

4. Hiding the Token field
   *   Or it can be set and then hidden from your customers if used else leave blank before hiding
5. Hiding or showing the options to set the network address manually
6. Enter Authentication Key if Authentication is enabled.

Controls (Not Shown) for fields that are not on all devices:\
1. Enable or hide the Relay Config Tab if not needed(if device has option).
2. Send the WLAN IP if the JSON option is selected as the MQTT Send Data Format is selected. (Sensors Only)


{% include image.html file="jemrf32sensorsetup-mu.jpg" alt="White Label Options"%}

The image below displays the default Setup Details tab, which includes all available options.
{% include image.html file="jemrf32sensorsetup.jpg" alt="Full Setup Options"%}

With all the options set to hide, the Setup Details tab is set to minimal, and the Relay Tab is gone
{% include image.html file="jemrf32sensorsetupmin.jpg" alt="Minimun Setup Options"%}


### Authentication Key
The sensor has the option to prevent accidental changes to the settings. That is done enabling the "Enable Authentication" check box.

When enabled, the Key field will turn Yellow when there is a change that needs the Key to authorize. When the correct Key is entered and you click off the Key field it will be validated and turn Green if Ok and Red if incorrect.


{% include image.html file="jemrfesp32whitelabel2.jpg" alt="White Label Options"%}

You have the option to use the default key or enter your own Custom User Key. The default Key is base on the Sensor date and changes each day. If using a **Custom User Key, it Must be 10 characters**.\
The format for the default Key is the two digits for the month, day, the last two digits of the year and the first four characters after JEM or JRF.

Example: \
Date is **11**-**15**-20**25** 00:13:25\
ID: JEM**C868**407446A8 \
The resulting default Key would be **111525C868**.

 You can see in this example, the Green Key field has the correct value.

{% include image.html file="jemrfesp32whitelabel3.jpg" alt="White Label Options"%}

### Private Certificate
The private Certificate file provides the option to upload one or two additional Security Certificates.
This provides options to use third party certificates or self generated certificates.

Certificates must be in plain text format with Begin Certificate at the top and End Certificate at the bottom.
The standard for plain text is a ".pem" file extension.

{% include image.html file="jemrfesp32whitelabel.jpg" alt="White Label Options"%}

### Reset Custom Key
If you enter a Custom User Key and forget it, you can get a temporary key by contacting Sales @ jemrf.com.  Sales will provide a link to the Generate a Temporary Access code.

Here is what the generator page looks like. Copy and paste the time from the sensor in the Date/Time field and copy and paste the "ID" in the upper right on the sensor page into the "Device ID" field. The temp key is good for the current hour. Meaning if the time is 12:55:00 the key will only be good for 5 minutes. If the time is 12:01:00 the key will be good for 59 minutes.

{% include image.html file="getmastercode.jpg" alt="White Label Options"%}

