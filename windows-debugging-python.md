<!-- TITLE: Windows Debugging Python -->
<!-- SUBTITLE: Debugging Windows Processes using Python -->


Massive Detour.
Gray Hat Python is 32bit centric.  Needed more.
Found [winappdbg]/winappdbg python package.  Similar functionality, already handles 32 and 64bit.   Using this to move onto what I really wanted to learn.

# Winappdbg







Most code is from Gray Hat Python

# Attaching to process
from page 50 of pdf:
some stuff defined in my_debugger_defines.py available on https://nostarch.com/ghpython.htm
debugger class below so that individual actions can be shown

```


import my_debugger
debugger = my_debugger.debugger()
debugger.load("C:\\WINDOWS\\system32\\calc.exe")

```

# debugger.py
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
			
	def open_process(self, pid):
		h_process = kernel32.OpenProcess(PROCESS_ALL_ACCESS, pid, False)
		return h_process
		
	def attach(self, pid):
		self.h_process = self.open_process(pid)
		if kernel32.DebugActiveProcess(pid):
			self.debugger_active = True
			self.pid = int(pid)
			self.run()
		else:
			print ("[*] Unable to attach to the process.")
			
	def run(self):
		while self.debugger_active == True:
			self.get_debug_event()
	
	def get_debug_event(self):
		debug_event = DEBUG_EVENT()
		continue_status = DBG_CONTINUE
		if kernel32.WaitForDebugEvent(byref(debug_event), INFINITE):
			raw_input("Press a key to continue..")
			self.debugger_active = FALSE
			kernel32.ContinueDebugEvent(debug_event.dwProcessId, debug_event.dwThreadId, continue_status)
	
	def detach(self):
		if kernel32.DebugActiveProcessStop(self.pid):
			print "[*] Finished debugging. Exiting..."
			return True
		else:
			print ("There was an error")
			return False
			
```
	
# Test