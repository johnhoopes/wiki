---
title: Objection
description: Uses Frida to do cool things
published: true
date: 2023-08-14T15:11:23.824Z
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

# Prepare to hook a method
```
android hooking search methods gatt
```

Similar works on IOS

# Hooking
```
android hooking watch class_method asvid.github.io.fridaapp.MainActivity.sum --dump-args --dump-backtrace --dump-return
```

```
android hooking set return_value asvid.github.io.fridaapp.MainActivity.checkPin true
```

# keystore
```
android keystore list
```

# Memory
```
memory search "<pattern eg: 41 41 41 ?? 41>" (--string) (--offsets-only)
memory write "<address>" "<pattern eg: 41 41 41 41>" (--string)
```

# SQLite

