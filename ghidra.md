---
title: Ghidra
description: A quick summary of Ghidra
published: true
date: 2022-11-15T05:17:10.650Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:19:39.457Z
---

# Scripts

~/ghidra_scripts

# Basic Block Script
```from ghidra.program.model.block import BasicBlockModel
from ghidra.util.task import TaskMonitor

bbm = BasicBlockModel(currentProgram)
blocks = bbm.getCodeBlocks(TaskMonitor.DUMMY)
block = blocks.next()

while block:
    print "{}".format(block.name) + "|{}".format(block.minAddress)+"|{}".format(block.maxAddress)
    block = blocks.next()
```

# Basic Block with Disassembly
```
from ghidra.program.model.block import BasicBlockModel
from ghidra.util.task import TaskMonitor

def print_disassembly(block):
    listing = currentProgram.getListing()
    ins_iter = listing.getInstructions(block, True)

    while ins_iter.hasNext():
        ins = ins_iter.next()
        print "{} {}".format(ins.getAddressString(False, True), ins)

bbm = BasicBlockModel(currentProgram)
blocks = bbm.getCodeBlocks(TaskMonitor.DUMMY)
block = blocks.next()

while block:
    print_disassembly(block)
    block = blocks.next()
    print
```
