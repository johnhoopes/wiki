<!-- TITLE: Windows Debugging Python -->
<!-- SUBTITLE: Debugging Windows Processes using Python -->

Most code is from Gray Hat Python
# Attaching to process
from page 50 of pdf:
some stuff defined in my_debugger_defines.py available on https://nostarch.com/ghpython.htm

```
from ctypes import *
from my_debugger_defines import *
kernel32 = windll.kernel32
class debugger():
	def __init__(self):
		pass
	def load(self,path_to_exe):
		creation_flags = DEBUG_PROCESS
		startupinfo = STARTUPINFO()
		process_information = PROCESS_INFORMATION()
		startupinfo.dwFlags = 0x1
		startupinfo.wShowWindow = 0x0
		startupinfo.cb = sizeof(startupinfo)
		
		if kernel32.CreateProcessA(path_to_exe, None,None,None,None,creation_flags,None,None,byref(startupinfo),byref(process_information)):
			print "[*] We have successfully launched the process!"
			print "[*] PID: %d" % process_information.dwProcessId
		else:
			print "[*] Error: 0x%08x." % kernel32.GetLastError()

import my_debugger
debugger = my_debugger.debugger()
debugger.load("C:\\WINDOWS\\system32\\calc.exe")

```
	