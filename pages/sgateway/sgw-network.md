---
title: "JemRF Smart Gateway"
keywords: getting started introduction, Smart Gateway Jemrf, Gateway, rf Sensor
last_updated: July 23, 2024
sidebar: wifi_sidebar
permalink: sgw-network.html
summary: JemRF Smart Gateway Network Tab.
---
# Network Details
The Smart Gateway provides a wide range of network configurations. It provides an internal WiFi Access point if needed to allow configuration once plugged into the network. The Network Details page is used to set all the network and internal time functions.

The normal operation is to get network settings from the standard local router using DHCP, but there is the option to set a static IP address if needed.
For time from a network time server there is an option for a custom Network Time Server (NTP Server). After the Gateway is online and working if the WiFi AP is no longer needed, there is an option to disable the Smart Gateway AP to reduce unwanted Wi-Fi networks and increase access security.

If the Gateway has an internal battery-backed clock, the Battery Clock section shows whether it is Active or Not.

If no Network Time Server is selected, there is the option to enter time manually. It should be noted that if they Gateway is getting network configuration settings from the local router, the router could include a network time server that would not show in the Network Time Server field.

The time used for reporting is the local time based on the selected time zone.

<img src="images/sgw-network.png" width="425"/>
**Figure 1  The Network Details screen.**

The screenshot below shows a change to the configuration that has been entered. The yellow fields indicate that the change has not yet been processed.

<img src="images/sgw-network1.png" width="425"/>
**Figure 2  Network changes.**

When changes are Saved the is a prompt in the upper left of the page showing about how long it will take for the change to be implemented.
Figure 3 show the status time to complete of a network IP change.

<img src="images/sgw-network-change.png" width="425"/>

**Figure 3  Network IP change in Progress.**


{% include note.html content="Only one change can be made at a time. A change must complete before making an additional change."%}

