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
System - information about current vm.

```
from winappdbg import System, version

# Show the Windows version and the current architecture.
print "WinAppDbg %s" % version
print "Running on %s for the %s architecture." % (System.os, System.arch)
if System.wow64:
    print "Running in 32 bit emulation mode."
print "From this Python VM we can attach to %d-bit processes." % System.bits
```

Enumerate processes
```
from winappdbg import System
# Create a system object.
system = System()
# Now we can enumerate the running processes.
for process in system:
    print "%d:\t%s" % ( process.get_pid(), process.get_filename() )
```

Starting a process

```
from winappdbg import System
import sys
# Instance a System object.
system = System()
# Start a new process.
process = system.start_process( command_line ) # see the docs for more options
# Show info on the new process.
print "Started process %d (%d bits)" % ( process.get_pid(), process.get_bits() )
```

Process
```
from winappdbg import Process, HexDump

def print_threads_and_modules( pid ):

    # Instance a Process object.
    process = Process( pid )
    print "Process %d" % process.get_pid()

    # Now we can enumerate the threads in the process...
    print "Threads:"
    for thread in process.iter_threads():
        print "\t%d" % thread.get_tid()

    # ...and the modules in the process.
    print "Modules:"
    bits = process.get_bits()
    for module in process.iter_modules():
        print "\t%s\t%s" % (
            HexDump.address( module.get_base(), bits ),
            module.get_filename()
        )
```

Read some memory

```

from winappdbg import Process

def process_read( pid, address, length ):

    # Instance a Process object.
    process = Process( pid )

    # Read the process memory.
    data = process.read( address, length )

    # You can also change the process memory.
    # process.write( address, "example data" )

    # Return a Python string with the memory contents.
    return data
```

Enumerate Threads
```
from winappdbg import Process, HexDump
def print_threads ( pid ):
    process = Process( pid )
    print "Threads:"
    for thread in process.iter_threads():
        print "\t%d" % thread.get_tid()				
```

Print a thread context

```
from winappdbg import Thread, CrashDump, System

def print_thread_context( tid ):
    System.request_debug_privileges()
    thread = Thread( tid )
    try:
		    thread.suspend()
        context = thread.get_context()
    finally:
        thread.resume()
				
    print CrashDump.dump_registers( context ),
		
```

