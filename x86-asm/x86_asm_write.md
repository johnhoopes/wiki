---
title: Example of Assembly file write snipped
description: 
published: true
date: 2024-02-19T00:20:46.873Z
tags: 
editor: markdown
dateCreated: 2024-02-19T00:20:46.873Z
---

# How to do a write

`_start:

        #push "txt\x00"
        li $v1, 0x00747874
        addi $sp, $sp, -4
        sw $v1, 0($sp)

        #push "key."
        li $v1, 0x2e79656b
        addi $sp,$sp,-4
        sw $v1, 0($sp)

        #filename is on stack. prep for open
        move $a0, $sp
        li   $a1, 0x05 #READ_ONLY?
        move $a2, $zero
        li   $v0, 0xFA5
        syscall 0

        #read(fd, buff, len)
        #fd should be in $v0
        #a2 should be set to length of read
        move $a0, $v0
        move $a1, $sp  #blast it onto the stack
        li   $a2, 0x3F #63 should be enough bytes
        li   $v0, 0xFA3
        syscall 0

        #write(fd, buff, count)
        li   $a0, 0x04
        move $a2, $v0
        li   $v0, 0xFA4
        syscall 0`