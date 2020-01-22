<!-- TITLE: Reverse Engineering Important Code -->
<!-- SUBTITLE: A quick summary of Reverse Engineering Important Code -->

# Summary
There are certain code paths that will be more interesting than others when looking for bugs.

# Input
Where does the code take input?

One strategy for effective debugging is to assign breakpoints on all of the read functions, and then put a breakpoint on the buffer that was read.  Then each reference to the buffer can be investigated to see what was read/written, and the the subsequent logic consisted of.

Usually these recv/send (in the case of TCP) or recvfrom / sendto (in the case of UDP) are stashed in DLLs / so files.  winsock / w32sock etc.  One should become very familiar with how these are called and what they return.

