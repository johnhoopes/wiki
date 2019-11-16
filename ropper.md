<!-- TITLE: Ropper -->
<!-- SUBTITLE: A quick summary of Ropper -->


Found at: https://github.com/sashs/Ropper
# Installation
read website

# Constraints
```
reg == reg     -  assign register to another
reg == number  -  assign number to register
reg == [reg]   -  assign memory to register
reg += number/reg/[reg]
reg -= number/reg/[reg]
reg *= number/reg/[reg]
reg /= number/reg/[reg]
```

So "eax==1 !ebx" would look for gadges that set eax to 1 and which does not clobber ebx.

# Example command lines
```
ropper -file /lib/x86_64-linux-gnu/libc-2.27.so 
ropper -f /lib/x86_64-linux-gnu/libc-2.27.so -a x86_64 --chain "execve cmd=/bin/sh"
ropper -f /lib/x86_64-linux-gnu/libc-2.27.so -a x86_64 --opcode ccc3 #Int 3; ret - allows to debug rop chain


