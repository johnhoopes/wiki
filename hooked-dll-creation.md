<!-- TITLE: Hooked Dll Creation -->
<!-- SUBTITLE: A quick summary of Hooked Dll Creation -->

# Calling a DLL in Python

```text
from ctypes import WinDLL, c_int

atm_dll = WinDLL('atm.dll')
atm_dll.dispenseCash(c_int(20))
```
