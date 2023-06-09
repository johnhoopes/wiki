---
title: I2C Reversing
description: I2C
published: true
date: 2023-06-09T18:26:19.805Z
tags: 
editor: markdown
dateCreated: 2023-06-09T15:33:22.621Z
---

# Enumerating I2C Bus
Saw a hardware project using this.
I need to try it sometime


`i2cscan.py ftdi:///2`
on raspi.

`i2cdump -y 1 0x6a` to dump data from an addr found with the scan.

`i2cset` not sure
