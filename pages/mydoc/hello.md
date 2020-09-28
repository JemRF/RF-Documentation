---
title: HELLO Command
keywords: hello, ping
last_updated: July 3, 2016
tags:  
summary: "This page describes the HELLO command."
sidebar: mydoc_sidebar
permalink: hello.html
folder: mydoc
---

The HELLO command is good command to use to test if there is connectivity to a particular device. This is also commonly known as a *ping test*. When an RF module receives a HELLO command it will simply reply with HELLO.  

**Command:** HELLO <br>
**Response:** HELLO

Example:

```
python rf_config.py 03 HELLO
SENT     : 03HELLO
RECEIVED : 03HELLO----
```
