<!-- TITLE: Winappdbg -->
<!-- SUBTITLE: A quick summary of Winappdbg -->


Official documentation https://winappdbg.readthedocs.io/en/latest/

# Utilities
plist.py - list of processes
pmap.py - takes pid, or executable name.
ptrace.py should be fun, but haven't tried it yet.
selectmyparent.py - inherits handles... tokens?

crashlogger.py - very interesting.  Meant to detect crashes and might be able to determine exploitability.  Very coool!


# Modules
System - information about current vm.  32bit vs 64bit (System.Wow64 True if 32 bit)

```
from winappdbg import System, version

# Show the Windows version and the current architecture.
print "WinAppDbg %s" % version
print "Running on %s for the %s architecture." % (System.os, System.arch)
if System.wow64:
    print "Running in 32 bit emulation mode."
print "From this Python VM we can attach to %d-bit processes." % System.bits
```

```
from winappdbg import System

# Create a system snaphot.
system = System()

# Now we can enumerate the running processes.
for process in system:
    print "%d:\t%s" % ( process.get_pid(), process.get_filename() )
```




