<!-- TITLE: Reverse Engineering -->
<!-- SUBTITLE: A quick summary of Reverse Engineering -->

# Summary
Using tools to understand how something works.  Often involving dissassembly or decompiling.  Humans don't read machine code all that well.  To get around that we use disassembly tools to produce assembly code. Ideally the tools then allow you to explore the disassembled code and move from function to function learning how an application works.

# Generic Patterns
[Determining the purpose of a Function](/reverse-engineering-function-purpose)
[Finding Important Code Paths](/reverse-engineering-important-code)
[Changing Behaviors](/reverse-engineering-changing-behaviors)
[Following Tainted Data](/reverse-engineering-following-taint)
# Platforms
The platform of the application can have a large determination on how the reversing will be accomplished:
* [Windows PE Binary Disassembly](/windowspe-disassembly)
* [Linux Disassembly](/linuxelf-disassembly)
* [.Net Disassembly](/dotnet-disassembly)
* [Java Disassembly](/java-disassembly)