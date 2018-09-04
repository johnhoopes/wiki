<!-- TITLE: Thick Client Local Issues -->
<!-- SUBTITLE: A quick summary of Thick Client Local Issues -->


Key Tools:
[Process Explorer](/process-explorer)
[Strace](/strace)

Key Targets:
* Credentials
* Sensitive Data

# Disk
Look at how the disk is used.
* Look at disk before anything runs.
* Look at disk after configuration.  Where did the configuration data go?
* Look while running.  Anything interesting temporarily written?
* Look after running what was left over.
# Registry
Similar to Disk except probably very little associated with running state
* Look after running and see what's there
# Permissions
What permission does the application run under? (Use task Manager / ps to check this)  Hopefully not root.
Does it drop privileges?  (Linux concept.  Find with Disassembly)
Is there a secondary portion of the application (drivers / services) that runs at a higher privilege?

# Library Loading
Look at library loading path.
On linux strace will show all of the paths checked until the library is loaded.
On windows process explorer will show it.
Idea is... to put a dll into a location that will be checked before the correct one.
If you can... use [DLL Hooking](/dll-hooking) or [SO Hooking](/so-hooking) for proof of concept and hooking.

