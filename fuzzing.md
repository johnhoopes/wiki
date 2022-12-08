---
title: Fuzzing
description: Notes on Fuzzing Research
published: true
date: 2022-12-08T18:31:38.098Z
tags: 
editor: markdown
dateCreated: 2022-11-28T06:48:05.014Z
---

# People

Jared Demott - EFS (Exploratory Fuzzing)

# Tools
Sidewinder  from whom?

Constraint solvers

Sage from Microsoft

AFL 

 - https://github.com/vanhauser-thc/afl-cov - Shows coverage of fuzz

-   Improvements to AFL
-   AFL++ - More improvements to afl
-   Part of liveoverflows series on sudo fuzzing - 
    https://www.youtube.com/watch?v=zdzcTh9kUrc&list=PLhixgUqwRTjy0gMuT4C3bmjeZjuNQyqdx&index=10

Project Springfield (SAGE based fuzzing service)


# Remote GDB - 

-   \- What does it take to make a gdb server?

# Crash Detection

-   Non-responsive
-   Exceptions
-   Other?

# Questions:

## How to fuzz network daemon.  
I can find read and change value read.  How to set state to something valid before continuing.  In case of tcpserver, it's going to try to write a response back.  Is that the right place to terminate execution?

## Scenario:

Echo demon
connect from client with nc
work out a way to break on the read
what structures need to be in place to fuzz from that point?

  - likely the network structure needs to stay in place

  - possibly just the socket number (interesting to change it :) )

## How to go back and fake that a packet came in?

 - New thread?

 - Manipulate context of existing thread?

## What about forking?