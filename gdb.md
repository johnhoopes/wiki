---
title: Gdb
description: A quick summary of Gdb
published: true
date: 2023-08-02T18:16:17.185Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:19:29.886Z
---

# Calling on running process by name
```
#Note that the -f5 might change if 3/4/5 digit pids.
gdb -p `ps -aef | grep -i full_troll | grep -v grep | cut -d' ' -f5
```

# Passing binary data on command line
from within gdb
```
run < <(printf "\xAA\xAA\xAA")
```
