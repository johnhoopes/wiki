<!-- TITLE: Dotnet Graywolf -->
<!-- SUBTITLE: A quick summary of Dotnet Graywolf -->

# Location
http://olympusclassic.dyns.cx/GrayWolf.exe

# Adding a printf line
Insert two IL Lines (try not to jack up an in progress instruction.
ldstr - The program hit the debug statement.
call - System.Void System.Console::WriteLine(System.String)

# Another printf line that writes to file instead

```text
ldstr - operand "c:\temp\log.txt"  (note that graywolf will double the \'s for you)
ldstr - operand "text to print" (note that this might be a local var in which you'd use ldloc.<number>)
call System.Void.System.IO.File::WriteAllText(String, String)
```
Note that AppendAllText might be better, and you can find these in mscorlib:System.IO.File.WriteAllText
