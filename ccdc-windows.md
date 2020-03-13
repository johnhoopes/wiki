<!-- TITLE: Ccdc Windows -->
<!-- SUBTITLE: A quick summary of Ccdc Windows -->

# Password Change DLL
Idea is... Box asks if password X is ok.  DLL will write X to a file, and likely send it off on the network.
Need to add registry entry for where the file should live and What host is catching passwords.

Catcher:
Log IP and username:password combination

[Password change DLL Source](/passwordchangedllsource)


How to install password dll
Make sure that you create a 32-bit password filter DLL for 32-bit computers and a 64-bit password filter DLL for 64-bit computers, and then copy them to the appropriate location.
Copy the DLL to the Windows installation directory \Windows\System32. 
Alter Registry Key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa   Value: "Notification Packages"  Change to name of DLL (without DLL).

To enforce both the default Windows password filter and the custom password filter, ensure that the Passwords must meet complexity requirements policy setting is enabled. Otherwise, disable the Passwords must meet complexity requirements policy setting.
(we'll want to disable this).
(probably a lot of hardening scripts that we should reverse)

# Need a way to base64 binaries, and have them extract to useable (for inclusion in scripts)
# Need a pastable script here to run on windows
Script needs to record status so you can see which pieces worked, and which ones failed.  Troubleshooting by scrolling back sucks.
Spit out status at end.
