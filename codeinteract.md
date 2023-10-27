---
title: Pause and inspect during Python Execution
description: 
published: true
date: 2023-10-27T14:02:06.745Z
tags: 
editor: markdown
dateCreated: 2023-10-27T14:02:06.745Z
---

# Code Inspect

I think python -i does some of this, but I haven't really worked it out.

`import code`

`code.interact(banner=None, readfunc=None, local=None, exitmsg=None)`

With the local parameter, you can use, for example:

    local=locals() for a local namespace
    local=globals() for a global namespace
    local=dict(globals(), **locals()) to use both the global namespace and the present local namespace

