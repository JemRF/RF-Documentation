---
title: "JemRF Smart Gateway"
keywords: getting started introduction, Smart Gateway Jemrf, Gateway, rf Sensor
last_updated: July 23, 2024
sidebar: wifi_sidebar
permalink: sgw-network.html
summary: JemRF Smart Gateway Network Tab.
---
# Network Details
The Network Details page is used to set a static IP address if needed, Identify a custom Network Time Server (NTP Server), and disable the Smart Gateway AP to reduce unwanted Wi-Fi networks and increase access security.

If the Gateway has an internal battery-backed clock, the Battery Clock section shows whether it is Active or Not.

If no Network Time Server is selected, there is the option to enter time manually.

There is the option for reporting using local time by selecting the local time zone.

<img src="images/sgw-network.png" width="425"/>
**Figure 1  The Nework Details screen.**


The screenshot below shows a change to the configuration that has been entered. The yellow fields indicate that the change has not yet been processed.


<img src="images/sgw-network1.png" width="425"/>
**Figure 2  Network changes.**


When changes are Saved the is a prompt in the upper left of the page showing about how long it will take for the change to be implemented.
Figure 3 show the status time to complete of a network IP change.

<img src="images/sgw-network-change.png" width="425"/>
**Figure 3  Network IP change in Progress.**


{% include note.html content="Only one change can be made at a time. A change must complete before making an additional change."%}

