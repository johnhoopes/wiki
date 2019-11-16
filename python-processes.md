<!-- TITLE: Python Processes -->
<!-- SUBTITLE: A quick summary of Python Processes -->

# Creating and interacting with subprocesses
Note that I had some difficulty with the following.  Might not be entirely correct.

```
p = subprocess.Popen(["./full_troll"], stdin=subprocess.PIPE, stdout=subprocess.PIPE)
stdin = p.stdin
stdout = p.stdout
time.sleep(1)
stdin.write(stuff)
data = stdout.readline()
```