<!-- TITLE: Windowssimplify -->
<!-- SUBTITLE: A quick summary of Windowssimplify -->

# Windows Simplification
I believe there is a ton of inefficiency that could be removed and significanly improve windows performance.

# NTDLL.DLL
Tons of calls have this test/jnz before either int 2e or syscall call.  Figure out which one and make all of them use it.  Drop the checks.  Could probably make two versions and load the right one for the program.

References:
https://blog.amossys.fr/windows10_TH2_int2E_mystery.html
https://reverseengineering.stackexchange.com/questions/19333/what-are-the-difference-syscall-and-int-0x2e-instructions
https://reverseengineering.stackexchange.com/questions/22054/why-address-7ffe0308-always-gets-compared-in-64bit-applications-before-making-a

# Windows Universal Apps
As of windows 10, apps call a WIN-API dll and then the normal dll.  Series of useless indirection

# Jump -> Jump -> Jump -> Code
Dll calls dll calls dll calls dll function.  Just inline the end code.  saves lots of memory hits.
Ideally this goes to syscalls instead of lib redirections.

# Strategy
Write a new dll loader 

# Questions?
Static setups in _DLLMAIN - Flattened DLL's will need it and can't conflict.
Is there anything similar at the kernel level?

# Plan on How to do it?
Change Executables to call my version of flattened dll's.

1.  Pick Executable
2.  List it's DLL's
3.  Make V2 of the DLL's in my searchpath.
4.  Start Flatening.
5. Benchmarking.  Will speed be noticeable until it's something big?