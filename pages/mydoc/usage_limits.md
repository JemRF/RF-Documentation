---
title: Monitoring Service Usage
keywords: monitoring, free monitoring, privateeyepi, usage
last_updated: Mar 27, 2022
tags:
summary: "This page explains our usage limits on free accounts"
sidebar: mydoc_sidebar
permalink: usage_limits.html
folder: mydoc
---

## PrivateEyePi.com

This document describes the usage limits for the free customer monitoring service provided by JemRf Solutions using our [PrivateEyePi Server](https://privateeyepi.com).
The PrivateEyePi server also supports subscriptions that add alert features and storage for more sensors.

## Usage Limits

We have implemented usage limits on the system to protect our system from being over loaded. You can monitor your PrivateEyePi usage at the bottom of your dashboard where you will see something like the following:

### Today's usage 45% (680/1500)

This means you have used 45% of your daily allowance. The 680 represented how many data readings you have sent to the server and the 1500 represents the daily allowance. When you get close to exceeding your daily limit we will display a message at the top of the dashboard warning you that you are approaching your daily limit.
At normal update of once every 5 minutes per sensors, 1500 readings provides storage for 5 sensors reporting once every 5 minutes per day. More sensors can be used, but at a slower update rate to not exceed the 1500 per day.

If you exceed your daily limit then the data on your dashboard will not be displayed. This is normally caused by a runaway sensor (like a motion sensor) that is sending data every few seconds. Sometimes we also encounter cases where the software on the Raspberry Pi has been modified to send data more frequently (e.g. temperature sensors). Please do not change transmit temperature sensor more frequently than 1 reading every 5 minutes. If you do then you will likely find you will exceed your daily allowance, or worse get your IP blocked from contacting our server.

In rare cases we do have to block IP addresses from contacting our server. We do this not to punish the user but to protect the system from being over loaded by what sometime amounts to a denial of service attack on our server.

If you find you are exceeding your daily allowance frequently then check the frequency that your sensors are sending data. Check if you might have a runaway sensor.

NOTE: The daily allowance total is totaled for all sensors, not per sensor.

Your data is not stored forever for free. Data after a year on free accounts is subject to being purged to reserve excessive database growth impacting system performance.