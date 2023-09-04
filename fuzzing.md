---
title: Fuzzing
description: Notes on Fuzzing Research
published: true
date: 2023-09-04T22:55:07.884Z
tags: 
editor: markdown
dateCreated: 2022-11-28T06:48:05.014Z
---

# People

Jared Demott - EFS (Exploratory Fuzzing)

# Tools
## Sidewinder  from whom?
 - https://www.blackhat.com/presentations/bh-usa-06/BH-US-06-Embleton.pdfhttps://www.blackhat.com/presentations/bh-usa-06/BH-US-06-Embleton.pdf
  - Fitness function based on Markov Process (may need to research that).  Less used paths scored higher
  - Cross mutation.  Taking values from high valued inputs and swapping pieces.
  - terminals and non-terminals (keywords, mixed in with anything).  Transforming between them.
  
Constraint solvers

Sage from Microsoft
Project Springfield (SAGE based fuzzing service)


## AFL 

- https://github.com/vanhauser-thc/afl-cov - Shows coverage of fuzz

-   Improvements to AFL
-   Part of liveoverflows series on sudo fuzzing - 
    https://www.youtube.com/watch?v=zdzcTh9kUrc&list=PLhixgUqwRTjy0gMuT4C3bmjeZjuNQyqdx&index=10
-   Minimizes test inputs.  ./afl-tmin -i test_case -o minimized_result -- /path/to/program [...]

## AFL++
- Figure out how instrumentation works
- Instrumenting in binaries
- Training https://www.youtube.com/watch?v=6YLz9IGAGLw
- Deferred Fork mode (doesn't fork a new process until just before the key bit... not sure how this would work for a socket, but good for speed).
- Persistent Mode - Only concentrate on specific code (I could see setting a breakpoint at head of main loop, and if it gets back "here" it's done fuzzing.  Crashes might still happen later, but hopefully memory corruption can be caught in other ways.
- Learn about llvm mode.  llvm_mode/README.md in AFL++

## Frida for non-mobile

## Radare / Rizin / Cutter

## QEMU for fuzzing

# Sanitizers
- For crash detection 
- Usually can only run one at a time.
- Slows programs significantly
  - Undefined Behavior Sanitizer - signed overflows, nullpointers
  - Memory Sanitizer - unitizialized memory reads
  - Address Sanitizer - memory corruption detection
  - Thread Sanitizer - race conditions
  
 # Hardening
 - AFL++ Hardening  (check AFL readme sections)
   - Stack protection
   - Foritify source
 # Dictionaries
 - Helps the token engine apparently
 - Libtokencap (looks at strcmp and memcmp calls to find good things to try in payloads)
 
# Google Clusters Fuzz
# MSFT One Fuzz
   
# Remote GDB - 

-  What does it take to make a gdb server?
-  How do I connect

# Crash Detection

-   Non-responsive
-   Exceptions
-   Other?

# Questions:

## How to fuzz network daemon.  
I can find read and change value read.  How to set state to something valid before continuing.  In case of tcpserver, it's going to try to write a response back.  Is that the right place to terminate execution?

Maybe alfnet - https://github.com/aflnet/aflnet
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