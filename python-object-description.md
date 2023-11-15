---
title: Things you can do to objects to learn more
description: 
published: true
date: 2023-11-15T19:58:07.648Z
tags: 
editor: markdown
dateCreated: 2023-11-15T19:58:07.647Z
---

# Header

To look at the code of a function:

```
import dis

def test(b): pass
dev add1(b): return b+1
test(0)
#reassigns code of other function to this one
test.__code__ = add1.__code__
dis.disco(test.__code__)
  1           0 LOAD_FAST                0 (b)
              2 LOAD_CONST               1 (1)
              4 BINARY_ADD
              6 RETURN_VALUE
```
