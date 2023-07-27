---
title: Convert Apps for monitor.jemrf.com
keywords: Apps
last_updated: July 27, 2023
tags:
summary: "This page describes the changes needed for the JemRF Python Apps to switch from privateeyepi to monitor.jemrf.com."
sidebar: mydoc_sidebar
permalink: monitoring.html
folder: mydoc
---

This document describes the changes needed to the JemRF Python Applications to change the monitoring server from PrivateEyePi.com to Monitor.JemRF.com.

The changes are easy, they only require the URL be change in 2 applications for the to send data to Monitoring.

Use the text editor of choice.

### Alarmfunctionr.py Version 16 and up
Version 16 has both URLs in the code. <br />
On line 77 put a # in front of script_path

    script_path = "https://www.privateeyepi.com/alarmhostr.php?token="+globals.token+"&function="+str(function)
    to:
    #script_path = "https://www.privateeyepi.com/alarmhostr.php?token="+globals.token+"&function="+str(function)

On line 78 delete the # in front of script_path

    #script_path = "https://pep.jemrf.com/alarmhostr.php?token="+globals.token+"&function="+str(function)
    to:
    script_path = "https://pep.jemrf.com/alarmhostr.php?token="+globals.token+"&function="+str(function)

Save when done.
{% include note.html content="If you have downloaded different applications, be sure all copies of alarmfunctionr.py are updated."%}

### Webcam.py Version 4
Line 198 change:

    script_path = "https://www.privateeyepi.com/alarmhost.php?token="+token+"&function="+str(function)
    to:
    script_path = "https://pep.jemrf.com/alarmhost.php?token="+token+"&function="+str(function)

Save when done.

Now all the python 3 RF-Applications should start sending to the Monitoring site.

Note pep.jemrf.com is the data import path to monitor.jemrf.com.


```
