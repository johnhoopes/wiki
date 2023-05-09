---
title: Objection
description: Uses Frida to do cool things
published: true
date: 2023-05-09T20:40:34.948Z
tags: 
editor: markdown
dateCreated: 2023-05-09T20:40:34.948Z
---


Uses [Frida](/frida)

# How to start objection
```
objection -N -h 10.0.0.154 --gadget 'application name' explore
```

# Set a proxy in an application
```
com.application.blah on (google: 13) [net] # android proxy set 10.0.0.100 8080
```