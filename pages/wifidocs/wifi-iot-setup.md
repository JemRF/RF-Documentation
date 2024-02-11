---
title: The WIFI Sensor Setup
keywords: getting started introduction, WiFI Sensor
last_updated: Jan 12, 2024
tags:
sidebar: wifi_sidebar
permalink: wifi-iot-setup.html
folder: mydoc
---
## Creating Monitoring Account First
If you are planning on using our newer monitoring services [**"monitor.jemrf.com"**](https://monitor.jemrf.com). It is recommended you create your Monitoring Account first if you don't have one, because in Step of the WiFi Setup Details you will need to know your monitoring account token. If you do not have a JemRF Monitoring Service account, the sign-up instruction to create an account are at: [Create account and create a Token](jemrfregister.html).

* For the legacy service, the sign-up instruction  on PrivateEyePi are at: [Create account and get Token](pepregister.html). If you already have a PEP Token, you can use it on the newer JemRF Monitor service.

##  Setup Details
To reach the configuration page for the WiFi IoT Sensor, you can use any device that supports WiFi and an internet browser. In this example we will use a desktop computer.

{% include image.html file="Slide1da59.jpg" alt="WiFi Start"%}


***To make setup easy, the WiFi Sensor has its own Access Point.***

### Step 1 Connect to WiFi

The first step is to connect your smart device to the WiFi Sensor. Power up the WiFi Sensor and using your computer (or smart device) look for a WiFi Name that starts with **PEP** followed by some numbers. These numbers are the unique ID of your device. Connect to the device using the default password:

Password: PrivateEyePi
{% include image.html file="gwsetup-ssid.jpg" alt="WiFi Connect"%}


### Step 2 : Configure SSID and Password
Now open up a browser  and navigate to [http://192.168.4.1/](http://192.168.4.1).
{% include image.html file="wifisetup.jpg" alt="WiFi Setup Page"%}
From here you configure your WiFi Settings.

{% include image.html file="wifi-setup-ssid.jpg" alt="WiFi SSID Select Page"%}
Next enter the Network Name/SSID and Password of your WiFi router and click on save.

Wait a few moments for the WiFi Sensor to connect to the WiFi router. Click on the "Setup Details" menu option to refresh the screen. Once connected you will see the **WLAN:** IP address has given to the Wireless Sensor, as shown in the next image. In the example below it shows 192.168.254.8, yours will be different. What's important is your gateway is now connected to the Internet.
{% include image.html file="wifisetuponline.png" alt="WiFi Sensor Online"%}

### Step 3 : Connect to Monitoring Server
You can now switch you laptop or phone from the device WiFi to your home WiFi Network.
If you want to use our monitoring services,[**"monitor.jemrf.com"**](https://monitor.jemrf.com) is our newer service, focused on monitoring with custom tolerance settings to trigger notifications to help alert when there is a problem. The next step is to connect your gateway our services so you can monitor the devices and get alerts.  Both of our online services have a free tier. You are welcome to visit each to see which meets your needs and can sign up for both (only one will work at a time). Both use a token to link your device to your account.

#### <span style="color:blue">Monitor.JemRF.com</span>
If you want to use our monitoring services and you do not have a JemRF Monitoring Service account, the sign-up instruction to create an account on JemRF Monitoring are at: [Create account and create a Token](jemrfregister.html).

* For the legacy service, the sign-up instruction  on PrivateEyePi are at: [Create account and get Token](pepregister.html). If you already have a PEP Token, you can use it on the newer JemRF Monitor service.

### Step 4 : Final Sensor Settings
With your Sensor now online (has a WLAN number), you can stay on your home WiFi Network and point you browser to the WLAN address of the gateway. In the example picture above the 192.168.254.8 would be the WLAN address for my Sensor, your address will change. Go to http://WLAN (example http://192.168.254.8).
#### Server
Now on the WiFi Sensor Setup Details page, the **Server** setting is  **pep.jemrf.com**.
{% include image.html file="Jemrf-server.jpg" alt="WiFi Server"%}

#### Token
Using your account on [monitor.jemrf.com](https:/monitor.jemrf.com), after you login, click on your name in the upper right hand corner a drop down menu will appear. Select Account and then click on the Edit Token button.
 * If you have a PrivateEyePi token already you can paste it in the token field and click the Accept Token to validate it is unique and Save. Now the same token works for both servers.
 * If you do not have a PrivateEyePi Token, click Generate Sensor Id and it will create a token for you.

 Click the Accept Token to validate it is unique and Save.
{% include image.html file="JemRf-account-token.jpg" alt="WiFi Get token"%}

Return to the Sensor WiFi and go back to [192.168.4.1](http://192.168.4.1) and copy and paste the **Token** into the **Token**  field as shown in the below diagram:

{% include image.html file="wifi_pep_jemrf.png" alt="WiFi JemRF Server"%}
Clicking "Save" will connect the WiFi Sensor to the server.  After a few moments, click on the "Setup Details" tab to refresh the screen, you will see **"PEP: Connected"** as shown in the image above.

Once Connected, the Wireless Sensor will start forwarding Wireless Sensor data to the monitoring server.
