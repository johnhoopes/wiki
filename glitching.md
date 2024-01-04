---
title: Glitching
description: 
published: true
date: 2024-01-04T19:56:23.663Z
tags: 
editor: markdown
dateCreated: 2023-12-16T03:26:02.410Z
---

# Goal
* Learn Glitching
* Learn FPGA
* Learn Python Hardware interfacing (GPIO on RASPI)
* Learn Python Serial interfacing
* Get something cool for Blackhat

# Steps
1. Get two microcontrollers?
 - Easy python programming/dumping would be nice.
2. Put a program on that blinks lights?
3. Learn to dump the program with python
4. Lock the chip
5. Differential Power.  
  - Try Salaea for analog analysis
  - Might need Need Oscilliscope and training for this
  - Is there a power differential on boot?  Why?
  - Checking one bit shouldn't take much. 
6. FPGA to count cycles.  Could it check programming?
   Is number of cycles different between protected and not?
   Perhaps use this instead of python to detect unlock?
7. Need to relearn how to program fpga.
8. FPGA needs serial communication and parsing.
9. Send clock count and pin to start count and pin to light when time comes.
10. Wire power on/off to start count pin on fpga.
11. Wire FPGA-Light -> EMP Trigger (and status light?)
12. Wire Power level switching for non-emp fault injection
12. Write Python harness
 - send session information to FPGA
 - reset chip (and trigger fpga to start counting)
 - wait some period of time
 - test reading chip
 - detect functionality? (watch blink pin?)
 

