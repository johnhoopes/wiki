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

