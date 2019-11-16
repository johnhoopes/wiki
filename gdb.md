<!-- TITLE: Gdb -->
<!-- SUBTITLE: A quick summary of Gdb -->

# Calling on running process by name
```
#Note that the -f5 might change if 3/4/5 digit pids.
gdb -p `ps -aef | grep -i full_troll | grep -v grep | cut -d' ' -f5
```