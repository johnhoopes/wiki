<!-- TITLE: Debugging -->
<!-- SUBTITLE: A quick summary of Debugging -->

Books
Hacker Debugging Uncovered

Tools
[Ollydbg](/ollydbg)
# Goals
We use debugging concepts to figure out how an application works internally.  Instead of trying to understand an entire application debugging (and [reverse-engineering](/reverse-engineering)) is used to isolate specific behaviors and functions.  Debugging is a dynamic analysis method.  This can help give context to reverse engineering data.  Debugging can be used to walk through functions and observe the data that is being manipulated.  It can be used to watch as data is acquired by the application and then that data can be traced as it's manipulated.  

# Breakpoints - Instruction
Using data from reverse-engineering, key functions can be identified.  At it's simplest, a breakpoint can be set on the entry point of a process.  The process can then be traced as main() is called and the application sets up to accomplish it's mission.  Normally the setup isn't terribly interesting to security testing.  We're most often looking at how things communicate.  So we try to find areas where data is sent and received (socket_read, socket_send).  We may want to see what's going on before encryption happens, or what's been sent inside a tunnel.  We can put a breakpoint on the entry point of that function and look at the buffer about to be encrypted.  

Even better than watching buffers, we can modify the buffers.  It's quite common for application developers to make assumptions that data being passed inside encrypted tunnels is "safe".  It's got a sort of implicit trust that no one could have tampered with the data.  As a result this is often one of our most effective techniques.  Sometimes developers even try to layer encryption.  They'll encrypt something and then send it through an SSL tunnel. 

# Breakpoints - Memory
