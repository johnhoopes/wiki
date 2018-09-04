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
# Library Loading
