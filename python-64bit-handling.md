<!-- TITLE: Python 64 Bit Handling -->
<!-- SUBTITLE: A quick summary of Python 64 Bit Handling -->

# Reading, Packing, Printing
```
#Convert basestr string into a useable integer
base = int(basestr, 16)

#Output the integer in little-endian form (16bytes)
def q(x):
    return struct.pack("<Q", x)

#print them nicely with print formating
print ("base 0x%x offset: 0x%x added: 0x%x" % (base, x, x+base))

